# docker-sync setup

```
gem install docker-sync
brew install fswatch
brew install unison
```

# compare

## normal docker-compose

```
docker-compose up -d
docker exec -it [your app container name] sh
```

in app container, create 100M file.

```
cd /var/test
/var/test # time dd if=/dev/zero of=speedtest bs=1024 count=102400
102400+0 records in
102400+0 records out
104857600 bytes (100.0MB) copied, 36.778332 seconds, 2.7MB/s
real    0m 36.77s
user    0m 0.20s
sys     0m 2.71s
```

## docker-compose with docker-sync

```
docker-sync-stack start
docker exec -it [your app container name] sh
```

in app container
```
/var/test # time dd if=/dev/zero of=speedtest bs=1024 count=102400
102400+0 records in
102400+0 records out
104857600 bytes (100.0MB) copied, 0.189606 seconds, 527.4MB/s
real    0m 0.19s
user    0m 0.01s
sys     0m 0.18s
```

