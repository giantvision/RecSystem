# 04--AWS的服务器申请及任务部署实践指南



### **1、服务器资源申请**

核心参数：

- cpu核心数
- 内存大小
- 磁盘大小

任务的原理及功能介绍，描述语言需要为英文。



### **2、登录服务器及任务部署**

1. 检查服务器的Python版本

   安装pip3:

   ```shell
   sudo yum -y install python3-pip
   ```

   - Link:  [How to install pip with python3?](https://stackoverflow.com/questions/6587507/how-to-install-pip-with-python-3)
   - AWS：[Install Python, pip, and the EB CLI on Linux](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install-linux.html)

   安装部署所需环境包：

   ```shell
   pip install --user -q  flask
   pip install --user -q flask_restful
   pip install --user -q elasticsearch
   ```

2. 服务器登录

3. 代码部署

   ```shell
   # 使用nohup让命令保持
   nohup python app.py
   ```

   >**备注：**
   >
   >```shell 
   >nohup command [command-argument ...]
   >```
   >
   >- Link:  [Linux nohup command](https://www.computerhope.com/unix/unohup.htm)
   
4. Linux下Python进程后天运行、查看及关闭

   ```shell
   # 查看进程
   ps -ef | grep python
   
   # kill 进程
   kill -9 进程号
   ```

   



