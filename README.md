# redis_python_example
Redis  Python Example

#To have REDIS on locai follow these instructions

#enable WSL2 on Windows
#Follow thes Microsoft instructions: https://learn.microsoft.com/en-us/windows/wsl/install

#launch Ubantu on windows on your laptop
#Follow these steps to install REDIS on your local Ubuntu
#https://redis.io/docs/getting-started/installation/install-redis-on-windows/

curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list
sudo apt-get update
sudo apt-get install redis

#start the Redis server like so:

sudo service redis-server start

#Connect to Redis
#You can test that your Redis server is running by connecting with the Redis CLI:

redis-cli 
127.0.0.1:6379> ping
PONG

# install REDIS 
python -m pip install redis

# resis python test code
import redis

redis_host = "localhost"
redis_port = 6379
redis_password = ""

# Create connection
r = redis.StrictRedis(host=redis_host, port=redis_port, password=redis_password, decode_responses=True)

def is_redis_available(r):
    try:
        r.ping()
        print("Successfully connected to redis")
    except (redis.exceptions.ConnectionError, ConnectionRefusedError):
        print("Redis connection error!")
        return False
    return True

#check connection
if is_redis_available(r):
    print("Yay!")

# set map and get from map
# SET command creates one key-value pair while using MSET command, multiple key-value pairs can be created.

r.mset({"Croatia": "Zagreb", "Bahamas": "Nassau"})
r.get("Bahamas")


