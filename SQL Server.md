# SQL Server

- 反向生成模型
- [flask 从sqlserver数据库中反向生成models](https://www.cnblogs.com/jdm532000/p/10911876.html)
- 1.安装连接sqlserver数据库的模块pymssql：pip install pymssql
- 2.安装sqlacodegen包：pip install sqlacodegen
- 3.生成models：sqlacodegen mssql+pymssql://数据库用户名:密码@数据库地址:端口号/数据库名 > 生成models路径
- sqlacodegen mssql+pymssql://sa:highsai@123@localhost:1433/formula?charset=utf8  > models.py