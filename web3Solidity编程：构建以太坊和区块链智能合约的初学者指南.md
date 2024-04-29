## Geth 使用

### 使用 Geth 创建私有网络
- step1. 创建账户

```bash
>geth account new --datadir "D:\Temp_workspace\ChainData"
INFO [04-30|00:28:44.431] Maximum peer count                       ETH=50 LES=0 total=50
Your new account is locked with a password. Please give a password. Do not forget this password.
Password:
Repeat password:

Your new key was generated

Public address of the key:   0xEC881C1871aB18Ae6fB404BCE24aC87Ab764ca3f
Path of the secret key file: D:\Temp_workspace\ChainData\keystore\UTC--2024-04-29T16-28-54.603250100Z--ec881c1871ab18ae6fb404bce24ac87ab764ca3f

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
>geth --datadir "D:\Temp_workspace\ChainData" --http --http.corsdomain "*" --http.api "web3,net,admin,personal,miner,eth" --networkid 15
INFO [04-30|00:30:28.967] Maximum peer count                       ETH=50 LES=0 total=50
WARN [04-30|00:30:28.983] Lowering memory allowance on 32bit arch  available=16059 addressable=2048
WARN [04-30|00:30:28.983] Sanitizing cache to Go's GC limits       provided=1024 updated=682
INFO [04-30|00:30:28.983] Set global gas cap                       cap=50,000,000
INFO [04-30|00:30:28.984] Initializing the KZG library             backend=gokzg
INFO [04-30|00:30:29.168] Allocated trie memory caches             clean=102.00MiB dirty=170.00MiB
INFO [04-30|00:30:29.173] Defaulting to leveldb as the backing database
INFO [04-30|00:30:29.173] Allocated cache and file handles         database=D:\Temp_workspace\ChainData\geth\chaindata cache=340.00MiB handles=8192
INFO [04-30|00:30:29.235] Using LevelDB as the backing database
INFO [04-30|00:30:29.444] Opened ancient database                  database=D:\Temp_workspace\ChainData\geth\chaindata\ancient/chain readonly=false
INFO [04-30|00:30:29.447] Initialising Ethereum protocol           network=15 dbversion=<nil>
INFO [04-30|00:30:29.448] Writing default main-net genesis block
INFO [04-30|00:30:29.764] Persisted trie from memory database      nodes=12356 size=1.79MiB time=26.8359ms gcnodes=0 gcsize=0.00B gctime=0s livenodes=0 livesize=0.00B
INFO [04-30|00:30:29.778]
INFO [04-30|00:30:29.778] ---------------------------------------------------------------------------------------------------------------------------------------------------------
INFO [04-30|00:30:29.778] Chain ID:  1 (mainnet)
INFO [04-30|00:30:29.778] Consensus: Beacon (proof-of-stake), merged from Ethash (proof-of-work)
INFO [04-30|00:30:29.778]
INFO [04-30|00:30:29.778] Pre-Merge hard forks (block based):
INFO [04-30|00:30:29.778]  - Homestead:                   #1150000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/homestead.md)
INFO [04-30|00:30:29.778]  - DAO Fork:                    #1920000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/dao-fork.md)
INFO [04-30|00:30:29.778]  - Tangerine Whistle (EIP 150): #2463000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/tangerine-whistle.md)
INFO [04-30|00:30:29.778]  - Spurious Dragon/1 (EIP 155): #2675000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/spurious-dragon.md)
INFO [04-30|00:30:29.778]  - Spurious Dragon/2 (EIP 158): #2675000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/spurious-dragon.md)
INFO [04-30|00:30:29.778]  - Byzantium:                   #4370000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/byzantium.md)
INFO [04-30|00:30:29.778]  - Constantinople:              #7280000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/constantinople.md)
INFO [04-30|00:30:29.778]  - Petersburg:                  #7280000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/petersburg.md)
INFO [04-30|00:30:29.778]  - Istanbul:                    #9069000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/istanbul.md)
INFO [04-30|00:30:29.778]  - Muir Glacier:                #9200000  (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/muir-glacier.md)
INFO [04-30|00:30:29.778]  - Berlin:                      #12244000 (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/berlin.md)
INFO [04-30|00:30:29.778]  - London:                      #12965000 (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/london.md)
INFO [04-30|00:30:29.778]  - Arrow Glacier:               #13773000 (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/arrow-glacier.md)
INFO [04-30|00:30:29.778]  - Gray Glacier:                #15050000 (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/gray-glacier.md)
INFO [04-30|00:30:29.778]
INFO [04-30|00:30:29.778] Merge configured:
INFO [04-30|00:30:29.778]  - Hard-fork specification:    https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/paris.md
INFO [04-30|00:30:29.778]  - Network known to be merged: true
INFO [04-30|00:30:29.781]  - Total terminal difficulty:  58750000000000000000000
INFO [04-30|00:30:29.781]
INFO [04-30|00:30:29.781] Post-Merge hard forks (timestamp based):
INFO [04-30|00:30:29.781]  - Shanghai:                    @1681338455 (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/shanghai.md)
INFO [04-30|00:30:29.781]
INFO [04-30|00:30:29.781] ---------------------------------------------------------------------------------------------------------------------------------------------------------
INFO [04-30|00:30:29.781]
INFO [04-30|00:30:29.781] Loaded most recent local block           number=0 hash=d4e567..cb8fa3 td=17,179,869,184 age=55y1mo1w
WARN [04-30|00:30:29.781] Failed to load snapshot                  err="missing or corrupted snapshot"
INFO [04-30|00:30:29.781] Rebuilding state snapshot
INFO [04-30|00:30:29.781] Resuming state snapshot generation       root=d7f897..0f0544 accounts=0 slots=0 storage=0.00B dangling=0 elapsed=0s
INFO [04-30|00:30:29.781] Regenerated local transaction journal    transactions=0 accounts=0
INFO [04-30|00:30:29.790] Chain post-merge, sync via beacon client
INFO [04-30|00:30:29.790] Gasprice oracle is ignoring threshold set threshold=2
WARN [04-30|00:30:29.790] Error reading unclean shutdown markers   error="leveldb: not found"
WARN [04-30|00:30:29.790] Engine API enabled                       protocol=eth
INFO [04-30|00:30:29.790] Starting peer-to-peer node               instance=Geth/v1.12.2-stable-bed84606/windows-386/go1.20.7
INFO [04-30|00:30:29.809] Generated state snapshot                 accounts=8893 slots=0 storage=409.64KiB dangling=0 elapsed=27.422ms
INFO [04-30|00:30:29.860] New local node record                    seq=1,714,408,229,859 id=f5278e754354cdbe ip=127.0.0.1 udp=30303 tcp=30303
INFO [04-30|00:30:29.860] Started P2P networking                   self=enode://fe1ec84f8b3dd556f0ee4453ec5d8e3f6414c02b651da3886170b2f8fad4af355da93fe70d6474bc2ec15eda52d868692e75c71dbe45600e7b6e2592f766a055@127.0.0.1:30303
INFO [04-30|00:30:29.863] IPC endpoint opened                      url=\\.\pipe\geth.ipc
INFO [04-30|00:30:29.863] Generated JWT secret                     path=D:\Temp_workspace\ChainData\geth\jwtsecret
INFO [04-30|00:30:29.864] HTTP server started                      endpoint=127.0.0.1:8545 auth=false prefix= cors=* vhosts=localhost
INFO [04-30|00:30:29.867] WebSocket enabled                        url=ws://127.0.0.1:8551
INFO [04-30|00:30:29.867] HTTP server started                      endpoint=127.0.0.1:8551 auth=true  prefix= cors=localhost vhosts=localhost
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
