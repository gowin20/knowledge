#web #stores #redis
# Basics of redis


### Most Basic Commands
**enter redis (node.js version) **
```bash
> npm install -g redis-cli
> rdcli

> 127.0.0.1:6379>
```


**ping: check connection**
```bash
> ping
PONG

```
**echo**
```bash
> ECHO 'Hello World'
"Hello World"
```


**set**
```bash
> SET foo 100
OK
```

**get**

```bash
> GET foo
"100"
``````

**incr / decr**
```bash
> INCR foo
> GET foo
"101"

> DECR foo
> GET foo
"100"
```

**EXISTS**

```bash
> EXISTS foo
1
> EXISTS hippos
0
```

**del / flushall**

```bash
> DEL foo
1
> EXISTS foo
0
> FLUSHALL
# removes everything set up until now
```



[[Redis - Server Example]]

### Less Basic Commands

**mset: multi set**
```bash
> MSET key1 "Hi" key2 "Bye"
> GET key1
"Hi"
> GET key2
"Bye"
```

**append**
```bash
> APPEND key1 " World"
> GET key1
> "Hi World"
```

**rename**
```bash
> RENAME key1 greeting
> GET key1
(nil)
> GET greeting
"Hi World"
```


### Timed Variables

**expire, ttl**
```bash
> SET greeting "Hello World"
OK
> GET greeting
"Hello World"

> EXPIRE greeting 50
1
#greeting now expires in 50 seconds


> TTL greeting
> 33
#shows remaining time

#after expiry:
> TTL greeting
-2
> GET greeting
(nil)

```

**setex: setting value and expiration at the same time**
SET with builtin EXPIRE
```bash
> SETEX greeting 30 "Hello World"
OK
> TTL greeting
25
```

**persist**
saves a variable set to expire by removing the timer

```bash
> PERSIST greeting
-1
# -1 since greeting no longer expires
> GET greeting
"Hello World"
```



#### Next up: [[Redis Lists|Lists]]