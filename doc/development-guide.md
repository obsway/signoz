# 基于Signoz的定制开发


快速安装：

docker compose -f docker/clickhouse-setup/docker-compose.yaml up -d


## Contribute to Backend (Query-Service) 🌑 
https://github.com/SigNoz/signoz/blob/develop/CONTRIBUTING.md

```bash
# 安装
brew install sqlite

# 查看安装的程序文件

signoz %brew list sqlite
/opt/homebrew/Cellar/sqlite/3.46.0/bin/sqlite3
/opt/homebrew/Cellar/sqlite/3.46.0/include/ (2 files)
/opt/homebrew/Cellar/sqlite/3.46.0/lib/libsqlite3.0.dylib
/opt/homebrew/Cellar/sqlite/3.46.0/lib/pkgconfig/sqlite3.pc
/opt/homebrew/Cellar/sqlite/3.46.0/lib/ (2 other files)
/opt/homebrew/Cellar/sqlite/3.46.0/sbom.spdx.json
/opt/homebrew/Cellar/sqlite/3.46.0/share/man/man1/sqlite3.1

# 运行sqlite3命令行
signoz %sqlite3
SQLite version 3.43.2 2023-10-10 13:08:14
Enter ".help" for usage hints.
Connected to a transient in-memory database.
Use ".open FILENAME" to reopen on a persistent database.


```

## sqlite3基本命令
 sqlite3 [options] [databasefile] [SQL]

 sqlite的sql 参考
 https://www.sqlite.org/lang.html

 sqlite3 var/lib/signoz/signoz.db "VACUUM";

 VACUUM: clean the main database by copying it's content to the temporary database file and reload the original database file from the copy.


## 初始化本地开发环境,缺省sqlite的数据库文件目录在/var下面。 用sudo执行

```bash
signoz %sudo make dev-setup --debug=b
Password:
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i386-apple-darwin11.3.0
Reading makefiles...
Updating goal targets....
 File `dev-setup' does not exist.
Must remake target `dev-setup'.
mkdir -p /var/lib/signoz
sqlite3 /var/lib/signoz/signoz.db "VACUUM";
mkdir -p pkg/query-service/config/dashboards
------------------
--> Local Setup completed
------------------
Successfully remade target file `dev-setup'.
```
