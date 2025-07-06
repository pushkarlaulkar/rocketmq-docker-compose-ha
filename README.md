Install RocketMQ as docker compose in cluster mode deployed on 3 VM's

### env provide
- 3 VMs with docker compose
- 3 VMs can access each other
- mount a data disk on dir /data

Suppose the IP of VMS are:
- vm1: 10.66.64.4
- vm2: 10.66.64.5
- vm3: 10.66.64.6


VM Name | service deployed
------- | -----------------
VM1	    | namesrv1 + broker-a-master
VM2	    | namesrv2 + broker-b-master
VM3	    | broker-a-slave + broker-b-slave


### deploy
1. copy docker-compose.yaml and dir conf to each VM.

2. edit config to adapt your VM ip and broker name.

3. start by below command

```
cd /data/rocketmq
docker compose up -d
chown 3000:3000 data/ -R && chown 3000:3000 conf/ -R # Very important, change owner of data dir to rocketmq user.
docker compose up -d
```

Console will be availabe at http://vm1-ip:8082
