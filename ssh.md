# SSH

## Local Port Forwarding (Outbound Tunneling)
```
My PC                     SSH Server           host2.com
┌────────┐    SSH -L   ┌───────────┐     ┌────────┐
|          |------------\|             |     |          |
| :8000 -------------------host2:80-----O-----> :80     |
| :9000 -------------------local:5432-┐|     |          |
|          |------------/|        :5432|     |          |
└────────┘             └───────────┘     └────────┘
```
1. `-L 8000:host2.com:80 user@example.com`
2. `-L 9000:localhost:5432 user@example.com`

```
-L LOCAL_PORT:[REMOTE_HOST:REMOTE_PORT]
                   ^-- from ssh server perspective
```

## Remote Port Forwarding (Inbound Tunneling)
```
My PC                     SSH Server           Client
┌────────┐    SSH -R   ┌───────────┐     ┌────────┐
|          |------------\|             |     |          |
| :3000 <--------------------------:9000 <----|         |
|          |------------/|             |     |          |
└────────┘             └───────────┘     └────────┘
```
1. `-R 9000:localhost:3000 user@example.com`

```
-R REMOTE_PORT:[LOCAL_HOST:LOCAL_PORT]
                   ^-- from My PC perspective
```

## Background
1. `-nNT`
1. `-fNn` (from Black Magic ssh)
1. `-o ExitOnForwardFailure=yes`
