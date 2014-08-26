# redis监控工具Redis_Live
该工具使用python编写，环境要求python版本在2.7以上
redis_live官网 [http://www.nkrode.com/article/real-time-dashboard-for-redis](http://www.nkrode.com/article/real-time-dashboard-for-redis)
### 安装依赖包
```
pip install tornado
pip install redis
pip install python-dateutil
pip install argparse
```
### 下载代码
	git clone https://github.com/kumarnitin/RedisLive.git

### 配置配置文件
原配置文件RedisLive/src/redis-live.conf

```
{
	"RedisServers":
	[
		{
  			"server": "192.168.1.92",
  			"port" : 6379
		},

		{
  			"server": "localhost",
  			"port" : 6380,
  			"password" : "some-password"
		}
	],

	"DataStoreType" : "redis",

	"RedisStatsServer":
	{
		"server" : "ec2-184-72-166-144.compute-1.amazonaws.com",
		"port" : 6385
	},

	"SqliteStatsStore" :
	{
		"path":  "to your sql lite file"
	}
}
```
### 配置文件分析
RedisServers模块表示监控的redis服务器和相应得端口，可以监控多个
RedisStatsServer模块设置存储redislive data数据，如果没有备用的redis实例，可以配置"DataStoreType" : "sqlite"

### 启动redislive
#### 启动监控脚本	
	./redis-monitor.py --duration=120

#### 启动webserver
	./redis-live.py
#### 浏览器中打开
	http://localhost:8888/index.html
