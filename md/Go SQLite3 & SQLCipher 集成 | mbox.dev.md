> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [mbox.dev](https://mbox.dev/dev/go/sqlite-sqlcipher/)

> 在 Go 项目开发中使用 sqlite3 本地数据库，非常容易。

*   [工具安装](https://mbox.dev/dev/go/sqlite-sqlcipher/#gong-ju-an-zhuang)
*   [SQLCipher](https://mbox.dev/dev/go/sqlite-sqlcipher/#sqlcipher)

在 Go 项目开发中使用 `sqlite3` 本地数据库，非常容易。通过利用 `gorm.io` 提供的包，快速集成 `sqlite3`。

以下是 `gorm.io` 提供的集成代码：

```
package main

import (
  "gorm.io/gorm"
  "gorm.io/driver/sqlite"
)

type Product struct {
  gorm.Model
  Code  string
  Price uint
}

func main() {
  db, err := gorm.Open(sqlite.Open("test.db"), &gorm.Config{})
  if err != nil {
    panic("failed to connect database")
  }

  // Migrate the schema
  db.AutoMigrate(&Product{})

  // Create
  db.Create(&Product{Code: "D42", Price: 100})

  // Read
  var product Product
  db.First(&product, 1) // find product with integer primary key
  db.First(&product, "code = ?", "D42") // find product with code D42

  // Update - update product's price to 200
  db.Model(&product).Update("Price", 200)
  // Update - update multiple fields
  db.Model(&product).Updates(Product{Price: 200, Code: "F42"}) // non-zero fields
  db.Model(&product).Updates(map[string]interface{}{"Price": 200, "Code": "F42"})

  // Delete - delete product
  db.Delete(&product, 1)
}


```

工具安装
----

在 mac 上通过 `brew install sqlite` 命令安装 `sqlite3` 工具。

利用 `sqlite3 ./test.db`，就可以打开数据库文件，并使用 SQL 进行数据查询。

使用 `sqlite` 本地数据库非常容易，但是安全性上得不到保证。即任何人都可以直接打开 `test.db` 数据库文件。

SQLCipher
---------

`sqlcipher` 则是专门解决 `sqlite` 数据库的明文问题，保证数据库文件加密存储。

在 Go 中使用 `sqlcipher` 也很简单。可以引用 `github.com/open-olive/gorm-sqlcipher` 包，也可以通过修改 `gorm.io/driver/sqlite` 包，

将引用 `github.com/mattn/go-sqlite3` 包替换为 `github.com/mutecomm/go-sqlcipher` 包即可。

修改上面的例子：

```
package main

import (
  "gorm.io/gorm"
  sqlcipher "github.com/open-olive/gorm-sqlcipher"
)

type Product struct {
  gorm.Model
  Code  string
  Price uint
}

func main() {
  //设置密码
  dsn := fmt.Sprintf("test.db?_pragma_key=%s&_pragma_cipher_page_size=4096", "password")

  db, err := gorm.Open(sqlcipher.Open(dsn), &gorm.Config{})
  if err != nil {
    panic("failed to connect database")
  }

  // Migrate the schema
  db.AutoMigrate(&Product{})

  // Create
  db.Create(&Product{Code: "D42", Price: 100})

  // Read
  var product Product
  db.First(&product, 1) // find product with integer primary key
  db.First(&product, "code = ?", "D42") // find product with code D42

  // Update - update product's price to 200
  db.Model(&product).Update("Price", 200)
  // Update - update multiple fields
  db.Model(&product).Updates(Product{Price: 200, Code: "F42"}) // non-zero fields
  db.Model(&product).Updates(map[string]interface{}{"Price": 200, "Code": "F42"})

  // Delete - delete product
  db.Delete(&product, 1)
}


```

现在，就无法使用 `sqlite3` 工具打开数据库文件了，必须在 mac 上通过 `brew install sqlcipher` 命令安装 `sqlcipher` 工具。

通过 `sqlcipher` 打开数据库文件：

```
$: sqlcipher test.db
sqlite> PRAGMA key = 'password';
sqlite> PRAGMA cipher_page_size = 4096;


```