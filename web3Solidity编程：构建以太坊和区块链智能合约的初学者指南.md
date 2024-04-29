## Geth 使用

### 使用 Geth 创建私有网络
- step1. 创建账户

```bash
>geth account new --datadir myChain
INFO [04-29|23:36:09.446] Maximum peer count                       ETH=50 LES=0 total=50
Your new account is locked with a password. Please give a password. Do not forget this password.
Password:
Repeat password:

Your new key was generated

Public address of the key:   0xFA35f43521C4869a4A1d3c95cf7bE49154d6e2b0
Path of the secret key file: myChain\keystore\UTC--2024-04-29T15-36-13.673112400Z--fa35f43521c4869a4a1d3c95cf7be49154d6e2b0

- You can share your public address with anyone. Others need it to interact with you.
- You must NEVER share the secret key with anyone! The key controls access to your funds!
- You must BACKUP your key file! Without the key, it's impossible to access account funds!
- You must REMEMBER your password! Without the password, it's impossible to decrypt the key!
```

-  step2. 创世模块的配置文件 genesis.json( 放置在 --datadir 下 )
```json
{
  "config": {
    "chainId": 15,
    "homesteadBlock": 0,
    "eip150Block": 0,
    "eip155Block": 0,
    "eip158Block": 0
  },
  "alloc": {},
  "coinbase": "0x0000000000000000000000000000000000000000",
  "difficulty": "0x200",
  "extraData": "",
  "gasLimit": "0xffffffff",
  "mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",
  "nonce": "0x0000000000000042",
  "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000"
}
```

- step3. geth init
```bash
>geth --datadir myChain --http --http.corsdomain "*" --http.api "web3,net,admin,personal,miner,eth" --networkid 15
INFO [04-29|23:52:30.863] Maximum peer count                       ETH=50 LES=0 total=50
WARN [04-29|23:52:30.879] Lowering memory allowance on 32bit arch  available=16059 addressable=2048
WARN [04-29|23:52:30.879] Sanitizing cache to Go's GC limits       provided=1024 updated=682
INFO [04-29|23:52:30.880] Set global gas cap                       cap=50,000,000
INFO [04-29|23:52:30.880] Initializing the KZG library             backend=gokzg
INFO [04-29|23:52:31.069] Allocated trie memory caches             clean=102.00MiB dirty=170.00MiB
INFO [04-29|23:52:31.069] Defaulting to leveldb as the backing database
INFO [04-29|23:52:31.069] Allocated cache and file handles         database=C:\Users\pitta\myChain\geth\chaindata cache=340.00MiB handles=8192
INFO [04-29|23:52:31.085] Using LevelDB as the backing database
INFO [04-29|23:52:31.096] Opened ancient database                  database=C:\Users\pitta\myChain\geth\chaindata\ancient/chain readonly=false
INFO [04-29|23:52:31.096] Initialising Ethereum protocol           network=15 dbversion=<nil>
INFO [04-29|23:52:31.097] Writing default main-net genesis block
INFO [04-29|23:52:31.415] Persisted trie from memory database      nodes=12356 size=1.79MiB time=33.1219ms gcnodes=0 gcsize=0.00B gctime=0s livenodes=0 livesize=0.00B
INFO [04-29|23:52:31.429]
INFO [04-29|23:52:31.429] ---------------------------------------------------------------------------------------------------------------------------------------------------------
INFO [04-29|23:52:31.429] Chain ID:  1 (mainnet)
INFO [04-29|23:52:31.429] Consensus: Beacon (proof-of-stake), merged from Ethash (proof-of-work)
INFO [04-29|23:52:31.429]
INFO [04-29|23:52:31.429] Pre-Merge hard forks (block based):
INFO [04-29|23:52:31.429]  - Homestead:                   #1150000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/homestead.md)
INFO [04-29|23:52:31.429]  - DAO Fork:                    #1920000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/dao-fork.md)
INFO [04-29|23:52:31.429]  - Tangerine Whistle (EIP 150): #2463000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/tangerine-whistle.md)
INFO [04-29|23:52:31.429]  - Spurious Dragon/1 (EIP 155): #2675000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/spurious-dragon.md)
INFO [04-29|23:52:31.429]  - Spurious Dragon/2 (EIP 158): #2675000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/spurious-dragon.md)
INFO [04-29|23:52:31.429]  - Byzantium:                   #4370000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/byzantium.md)
INFO [04-29|23:52:31.429]  - Constantinople:              #7280000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/constantinople.md)
INFO [04-29|23:52:31.429]  - Petersburg:                  #7280000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/petersburg.md)
INFO [04-29|23:52:31.429]  - Istanbul:                    #9069000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/istanbul.md)
INFO [04-29|23:52:31.429]  - Muir Glacier:                #9200000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/muir-glacier.md)
INFO [04-29|23:52:31.429]  - Berlin:                      #12244000 (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/berlin.md)
INFO [04-29|23:52:31.429]  - London:                      #12965000 (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/london.md)
INFO [04-29|23:52:31.429]  - Arrow Glacier:               #13773000 (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/arrow-glacier.md)
INFO [04-29|23:52:31.429]  - Gray Glacier:                #15050000 (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/gray-glacier.md)
INFO [04-29|23:52:31.429]
INFO [04-29|23:52:31.429] Merge configured:
INFO [04-29|23:52:31.429]  - Hard-fork specification:    https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/paris.md
INFO [04-29|23:52:31.429]  - Network known to be merged: true
INFO [04-29|23:52:31.429]  - Total terminal difficulty:  58750000000000000000000
INFO [04-29|23:52:31.429]
INFO [04-29|23:52:31.429] Post-Merge hard forks (timestamp based):
INFO [04-29|23:52:31.429]  - Shanghai:                    @1681338455 (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/shanghai.md)
INFO [04-29|23:52:31.434]
INFO [04-29|23:52:31.434] ---------------------------------------------------------------------------------------------------------------------------------------------------------
INFO [04-29|23:52:31.434]
INFO [04-29|23:52:31.434] Loaded most recent local block           number=0 hash=d4e567..cb8fa3 td=17,179,869,184 age=55y1mo1w
WARN [04-29|23:52:31.434] Failed to load snapshot                  err="missing or corrupted snapshot"
INFO [04-29|23:52:31.434] Rebuilding state snapshot
INFO [04-29|23:52:31.434] Resuming state snapshot generation       root=d7f897..0f0544 accounts=0 slots=0 storage=0.00B dangling=0 elapsed=0s
INFO [04-29|23:52:31.434] Regenerated local transaction journal    transactions=0 accounts=0
INFO [04-29|23:52:31.439] Chain post-merge, sync via beacon client
INFO [04-29|23:52:31.439] Gasprice oracle is ignoring threshold set threshold=2
WARN [04-29|23:52:31.439] Error reading unclean shutdown markers   error="leveldb: not found"
WARN [04-29|23:52:31.439] Engine API enabled                       protocol=eth
INFO [04-29|23:52:31.439] Starting peer-to-peer node               instance=Geth/v1.12.2-stable-bed84606/windows-386/go1.20.7
INFO [04-29|23:52:31.451] New local node record                    seq=1,714,405,951,449 id=cfd8be80448c92ac ip=127.0.0.1 udp=30303 tcp=30303
INFO [04-29|23:52:31.451] Started P2P networking                   self=enode://649e390027e6c4afcf33f2976e1e61d4c937cffc84e5199f0eb8e8ca5e7f0891469e4e64de2b7e13d5425f45cc93863e4e3b99e97ff6632c68639617b62aa1fd@127.0.0.1:30303
INFO [04-29|23:52:31.452] IPC endpoint opened                      url=\\.\pipe\geth.ipc
INFO [04-29|23:52:31.453] Generated JWT secret                     path=C:\Users\pitta\myChain\geth\jwtsecret
INFO [04-29|23:52:31.453] HTTP server started                      endpoint=127.0.0.1:8545 auth=false prefix= cors=* vhosts=localhost
INFO [04-29|23:52:31.456] WebSocket enabled                        url=ws://127.0.0.1:8551
INFO [04-29|23:52:31.456] HTTP server started                      endpoint=127.0.0.1:8551 auth=true  prefix= cors=localhost vhosts=localhost
INFO [04-29|23:52:31.464] Generated state snapshot                 accounts=8893 slots=0 storage=409.64KiB dangling=0 elapsed=30.743ms
INFO [04-29|23:52:41.608] Looking for peers                        peercount=1 tried=47 static=0
```

- 通过 ipc 链接
```bash
> geth attach ipc:\\.\pipe\geth.ipc
Welcome to the Geth JavaScript console!

instance: Geth/v1.12.2-stable-bed84606/windows-386/go1.20.7
at block: 0 (Thu Jan 01 1970 08:00:00 GMT+0800 (CST))
 datadir: C:\Users\pitta\myChain
 modules: admin:1.0 debug:1.0 engine:1.0 eth:1.0 miner:1.0 net:1.0 rpc:1.0 txpool:1.0 web3:1.0

To exit, press ctrl-d or type exit
>
```

- 通过 rpc (http 方式) 链接
```bash
> geth attach http://127.0.0.1:8545
WARN [04-30|00:03:26.917] Enabling deprecated personal namespace
Welcome to the Geth JavaScript console!

instance: Geth/v1.12.2-stable-bed84606/windows-386/go1.20.7
at block: 0 (Thu Jan 01 1970 08:00:00 GMT+0800 (CST))
 datadir: C:\Users\pitta\myChain
 modules: admin:1.0 eth:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 web3:1.0

To exit, press ctrl-d or type exit
>
```

<hr> 经过上述步骤，完成到 Geth节点 的链接，在挖矿开始之前，需要设置 coinbase 或者 etherbase 账户。 创世块 genesis.json 中只是初始的

- step.4 设置 coinbase （用到 step1 中生成的账号地址: `0xFA35f43521C4869a4A1d3c95cf7bE49154d6e2b0`）
```bash
To exit, press ctrl-d or type exit
> miner.setEtherbase("0xFA35f43521C4869a4A1d3c95cf7bE49154d6e2b0")
true
> eth.coinbase
"0xfa35f43521c4869a4a1d3c95cf7be49154d6e2b0"  # 设置成功。启动挖矿程序之后，获得的挖矿奖励将发送到这个账户
>
```
- step.5 启动挖矿
```bash

```
- 
- 
