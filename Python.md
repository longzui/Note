# Python

##### py文件打包exe

1.  安装pyinstaller：

   ```python
    pip install pyinstaller
   ```

2. 使用pyinstaller进行打包

   ```pthon
   多个文件打包格式：
   pyinstaller [主文件] -p [其他文件1] -p [其他文件2]  --hidden-import [自建模块1] --hidden-import [自建模块2] 
   
   pyinstaller.bat -F main.py -p models.py --hidden-import pymssql --icon upload.ico
   
   单个文件打包格式：
   pyinstaller —F [单个py文件]
   ```

​	在线**转换ico**格式网址： https://onlineconvertfree.com/zh/convert/





##### schedule定时任务

1. import schedule

   

2. ```
   schedule.every(10).minutes.do(job, name)
   schedule.every().hour.do(job, name)
   schedule.every().day.at("10:30").do(job, name)
   schedule.every(5).to(10).days.do(job, name)
   schedule.every().monday.do(job, name)
   schedule.every().wednesday.at("13:15").do(job, name)
   ```
