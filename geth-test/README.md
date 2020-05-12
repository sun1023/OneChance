# OneChance合约测试-geth

以下以windows环境为例

启动cmd,并将目录修改为当前目录(geth-test)后

执行以下命令启动geth控制台
  
1. geth --datadir "./privatenet" init ./privatenet/genesis.json 2>>oneChance.log
   // 使用 genesis.json 文件初始化区块链,该文件为测试用3个用户分配了部分 Ether
2. geth --rpc --rpcapi "db,eth,net,web3" --rpcport "8080" --rpccorsdomain "*" --datadir "./privatenet" --port "30303" --identity "Sun" console 2>>oneChance.log
   // 在私有链上启动geth控制台

测试环境初始有3个账户,账户密码都是"test123456",账户解锁操作都在脚本中自动进行

以下每个js脚本都需要前一个脚本正常执行,顺序执行以下js文件内容,打开文件全选内容,复制粘贴到geth控制台代码会自动运行

1. deploy.js
   // 部署合约,设置合约互相引用地址
2. init.js
   // 初始化账户信息,用主办方账户为测试账户发放测试用代币,用主办方账户发布奖品信息
3. buyChance.js
   // 购买奖品 Chance ,并完成随机数提交工作
4. result.js
   // 查询中奖结果与参与活动的用户信息
   
ps. 请不要使用loadScript方式运行js文件,会有莫名其妙的问题,不报错但是交易也没有提交成功
