# 06--Redis数据库实践指南



### 1、安装环境设置

```shell
pip install redis-server redis
```



2、python文件中的代码设置

```python
import redis_server

# 数据持久化设置
import subprocess
subprocess.Popen(redis_server.REDIS_SERVER_PATH)

import redis
redis_news  = redis.StrictRedis(host="127.0.0.1", port=6379, db=0, decode_responses=True)
redis_video = redis.StrictRedis(host="127.0.0.1", port=6379, db=0, decode_responses=True)
```



## 遇到的问题汇总：

**1、Redis在Python文件中的数据持久化设置问题**

- 参考信息源：[Running Redis on Google Colab](https://www.kdnuggets.com/2022/01/running-redis-google-colab.html)

解决方法：

 1. Install

    ```shell
    pip install redis-server redis
    ```

    > **NOTE:**
    >
    > *While Jupyter Notebooks support many languages, Colab supports only Python. To use Redis with [Python](https://www.python.org/), you need a[ Redis Python client](https://docs.redis.com/latest/rs/references/client_references/client_python/). In this tutorial we demonstrate the use of [redis-py](https://github.com/andymccurdy/redis-py/), a Redis Python Client, which we install using the `%pip install redis `command. 
    >
    > **You can run a shell command in Jupyter Notebook or Google Colab with [IPython](https://jakevdp.github.io/PythonDataScienceHandbook/01.05-ipython-and-shell-commands.html) by prefixing it with the ! character or % to use magic commands. A list of useful magic commands for data scientists are described in the article - [top 8 magic commands in Jupyter Notebook](https://towardsdatascience.com/top-8-magic-commands-in-jupyter-notebook-c1582e813560).

 2. Start the Redis Server

    To start the Redis server run:

    ```shell
    import redis_server
    !$redis_server.REDIS_SERVER_PATH --daemonize yes
    ```

> NOTE:
>
> Alternately you can start the Redis server without shell commands, using a Python subprocess:
>
> ```python
> import subprocess
> import redis_server
> subprocess.Popen([redis_server.REDIS_SERVER_PATH])
> ```

3. Verify the Redis is Running

   If you want to verify that Redis is up and running you can connect to the server and run the "PING command". We create a connection to Redis using the Python client redis-py and then we ‘ping’ the server:

   ```python
   import redis
   client = redis.Redis(host = 'localhost', port=6379)
   client.ping()
   ```

4. Example code for Redis commands

   Once connected to Redis, you can read and write data [with Redis command functions](https://docs.redis.com/latest/rs/references/client_references/client_python/). In this example we use Redis as a [key value database](https://redis.com/nosql/key-value-databases/) (also called key value store). The following code snippet assigns the value bar to the Redis key foo, reads it back, and returns it:

   ```python
   client.set('foo', 'bar')
   client.get('foo')
   ```

   







