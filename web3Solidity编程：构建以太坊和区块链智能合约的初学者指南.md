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
# 说明，--dev.period 默认是 0，只有在交易 pengding 才能开启挖矿
>geth --dev --dev.period 20 --datadir "D:\Temp_workspace\ChainData" --http --http.corsdomain "*" --http.api "web3,net,admin,personal,miner,eth" --networkid 15 --password D:\Temp_workspace\ChainData\keystore\password.txt
INFO [04-30|12:16:18.162] Starting Geth in ephemeral dev mode...
WARN [04-30|12:16:18.173] You are running Geth in --dev mode. Please note the following:

  1. This mode is only intended for fast, iterative development without assumptions on
     security or persistence.
  2. The database is created in memory unless specified otherwise. Therefore, shutting down
     your computer or losing power will wipe your entire block data and chain state for
     your dev environment.
  3. A random, pre-allocated developer account will be available and unlocked as
     eth.coinbase, which can be used for testing. The random dev account is temporary,
     stored on a ramdisk, and will be lost if your machine is restarted.
  4. Mining is enabled by default. However, the client will only seal blocks if transactions
     are pending in the mempool. The miner's minimum accepted gas price is 1.
  5. Networking is disabled; there is no listen-address, the maximum number of peers is set
     to 0, and discovery is disabled.

INFO [04-30|12:16:18.176] Maximum peer count                       ETH=50 LES=0
 total=50
WARN [04-30|12:16:18.176] Lowering memory allowance on 32bit arch  available=16059 addressable=2048
WARN [04-30|12:16:18.179] Sanitizing cache to Go's GC limits       provided=1024 updated=682
INFO [04-30|12:16:18.179] Set global gas cap                       cap=50,000,000
INFO [04-30|12:16:18.689] Using developer account                  address=0xEC881C1871aB18Ae6fB404BCE24aC87Ab764ca3f
INFO [04-30|12:16:18.689] Using leveldb as the backing database
INFO [04-30|12:16:18.689] Allocated cache and file handles         database=D:\Temp_workspace\ChainData\geth\chaindata cache=340.00MiB handles=8192 readonly=true
INFO [04-30|12:16:18.693] Using LevelDB as the backing database
INFO [04-30|12:16:18.693] Opened ancient database                  database=D:\Temp_workspace\ChainData\geth\chaindata\ancient/chain readonly=true
INFO [04-30|12:16:18.693] Initializing the KZG library             backend=gokzg
INFO [04-30|12:16:18.883] Allocated trie memory caches             clean=102.00MiB dirty=170.00MiB
INFO [04-30|12:16:18.883] Using leveldb as the backing database
INFO [04-30|12:16:18.883] Allocated cache and file handles         database=D:\Temp_workspace\ChainData\geth\chaindata cache=340.00MiB handles=8192
INFO [04-30|12:16:18.987] Using LevelDB as the backing database
INFO [04-30|12:16:19.069] Opened ancient database                  database=D:\Temp_workspace\ChainData\geth\chaindata\ancient/chain readonly=false
INFO [04-30|12:16:19.070] Initialising Ethereum protocol           network=15 dbversion=8
INFO [04-30|12:16:19.070]
INFO [04-30|12:16:19.070] ---------------------------------------------------------------------------------------------------------------------------------------------------------
INFO [04-30|12:16:19.070] Chain ID:  1337 (unknown)
INFO [04-30|12:16:19.070] Consensus: unknown
INFO [04-30|12:16:19.070]
INFO [04-30|12:16:19.070] Pre-Merge hard forks (block based):
INFO [04-30|12:16:19.070]  - Homestead:                   #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/homestead.md)
INFO [04-30|12:16:19.070]  - Tangerine Whistle (EIP 150): #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/tangerine-whistle.md)
INFO [04-30|12:16:19.070]  - Spurious Dragon/1 (EIP 155): #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/spurious-dragon.md)
INFO [04-30|12:16:19.070]  - Spurious Dragon/2 (EIP 158): #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/spurious-dragon.md)
INFO [04-30|12:16:19.070]  - Byzantium:                   #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/byzantium.md)
INFO [04-30|12:16:19.070]  - Constantinople:              #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/constantinople.md)
INFO [04-30|12:16:19.071]  - Petersburg:                  #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/petersburg.md)
INFO [04-30|12:16:19.071]  - Istanbul:                    #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/istanbul.md)
INFO [04-30|12:16:19.071]  - Muir Glacier:                #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/muir-glacier.md)
INFO [04-30|12:16:19.071]  - Berlin:                      #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/berlin.md)
INFO [04-30|12:16:19.071]  - London:                      #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/london.md)
INFO [04-30|12:16:19.071]  - Arrow Glacier:               #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/arrow-glacier.md)
INFO [04-30|12:16:19.071]  - Gray Glacier:                #0        (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/gray-glacier.md)
INFO [04-30|12:16:19.071]
INFO [04-30|12:16:19.071] Merge configured:
INFO [04-30|12:16:19.071]  - Hard-fork specification:    https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/paris.md
INFO [04-30|12:16:19.071]  - Network known to be merged: true
INFO [04-30|12:16:19.071]  - Total terminal difficulty:  0
INFO [04-30|12:16:19.071]
INFO [04-30|12:16:19.071] Post-Merge hard forks (timestamp based):
INFO [04-30|12:16:19.071]  - Shanghai:                    @0          (https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/shanghai.md)
INFO [04-30|12:16:19.071]
INFO [04-30|12:16:19.071] ---------------------------------------------------------------------------------------------------------------------------------------------------------
INFO [04-30|12:16:19.071]
INFO [04-30|12:16:19.072] Loaded most recent local block           number=35 hash=d590b6..0f5a69 td=0 age=17s
INFO [04-30|12:16:19.072] Loaded most recent local finalized block number=35 hash=d590b6..0f5a69 td=0 age=17s
INFO [04-30|12:16:19.072] Loaded local transaction journal         transactions=0 dropped=0
INFO [04-30|12:16:19.073] Regenerated local transaction journal    transactions=0 accounts=0
INFO [04-30|12:16:19.077] Chain post-merge, sync via beacon client
INFO [04-30|12:16:19.078] Gasprice oracle is ignoring threshold set threshold=2
INFO [04-30|12:16:19.078] Starting peer-to-peer node               instance=Geth/v1.12.2-stable-bed84606/windows-386/go1.20.7
WARN [04-30|12:16:19.078] P2P server will be useless, neither dialing nor listening
INFO [04-30|12:16:19.146] IPC endpoint opened                      url=\\.\pipe\geth.ipc
INFO [04-30|12:16:19.148] New local node record                    seq=1,714,450,161,941 id=c47d16c9ebafd2ad ip=127.0.0.1 udp=0 tcp=0
INFO [04-30|12:16:19.148] HTTP server started                      endpoint=127.0.0.1:8545 auth=false prefix= cors=* vhosts=localhost
INFO [04-30|12:16:19.148] Started P2P networking                   self=enode://8b807a25ee2f1533d61ce9a5c71eb5e89b1f9deaa13798b5faef71602aeaff57c5a1fcc040085adc2938a557aab0f07dd58719e2cf953f5055af021b95e33771@127.0.0.1:0
INFO [04-30|12:16:19.167] Starting work on payload                 id=0x06532471fe5bdd99
INFO [04-30|12:16:19.167] Updated payload                          id=0x06532471fe5bdd99 number=36 hash=5df9e4..15eb45 txs=0 withdrawals=0 gas=0 fees=0 root=762634..baab26 elapsed=0s
INFO [04-30|12:16:19.167] Stopping work on payload                 id=0x06532471fe5bdd99 reason=delivery
INFO [04-30|12:16:19.178] Imported new potential chain segment     number=36 hash=5df9e4..15eb45 blocks=1 txs=0 mgas=0.000 elapsed=10.572ms mgasps=0.000 dirty=0.00B
INFO [04-30|12:16:19.179] Chain head was updated                   number=36 hash=5df9e4..15eb45 root=762634..baab26 elapsed="517.2µs"
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
> miner.start()
null
> eth.blockNumber
41
```
- step.6 查看挖矿账户情况
```bash
> eth.accounts
["0xec881c1871ab18ae6fb404bce24ac87ab764ca3f"]
> eth.getBalance(eth.coinbase)/1e18
1.157920892373162e+59
```

- step.7 添加私有网络到 metemask, 并导入账号

![image](https://github.com/Cvjark/Notebook/assets/89090949/a567133c-cfc1-40cd-af05-99eac46f9895)


- 
