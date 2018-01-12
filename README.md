# 区块链知识框架

##阅读资料
###技术层面
- **比特币论文**
	- [Bitcoin: A Peer-to-Peer Electronic Cash System](https://bitcoin.org/bitcoin.pdf)
	- [比特币：一种点对点的电子现金系统](http://www.8btc.com/wiki/bitcoin-a-peer-to-peer-electronic-cash-system)
- **普林斯顿：比特币和加密货币**
	- [Bitcoin and cryptocurrency](https://www.coursera.org/learn/cryptocurrency)
- **斯坦福：比特币开发**
	- [Bitcoin Engineering (CS251P)](http://bitcoin.stanford.edu/)
- **Master Bitcoin（精通比特币）**
	- [Master Bitcoin](http://book.8btc.com/masterbitcoin2cn) By Andreas M. Antonopoulos
	- 从代码层面介绍比特币的技术细节
- **《区块链：技术驱动金融》**
	- 源于普林斯顿公开课，用通俗语言介绍了区块链和比特币的技术
- **《区块链技术指南》**
	- 2017年初，邹均著，与北航合作
	- 第一本比较全面介绍区块链技术的书，不细致，可以入门浏览
- **《区块链开发指南》**
	- 2017年底，申屠青春著
	- 可以大致了解区块链各种系统架构和开发流程，比较偏博客
- **《区块链：原理、设计与应用》**
	- 2017年底，杨保华（IBM Hyperledger团队）、陈昌著
	- 重点介绍Hyperlerger项目

###业务层面
- **区块链：从数字货币到信用社会**
	- 长铗（巴比特）,韩峰
- **区块链新经济蓝图及导读**
	- 定义了区块链1.0, 2.0, 3.0
- **区块链：定义未来金融与经济新格局**
	- 张健（火币网）
	- 沿人类社会经济发展规律由浅入深介绍区块链。第四章涉及比特币底层技术

###标准化白皮书
- [工信部:2016中国区块链技术和应用发展白皮书](http://www.199it.com/archives/526865.html)
- [TrustSQL腾讯区块链白皮书](https://trustsql.qq.com/chain_oss/TrustSQL_WhitePaper.html)
- [WEF（世界经济论坛） Realizing Potential Blockchain](http://www3.weforum.org/docs/WEF_Realizing_Potential_Blockchain.pdf)

###Blogs
- [精读比特币白皮书系列（1-6）](https://www.jianshu.com/p/ca0c0a0e0faa)
- [详解最近大热的闪电网络、雷电网络和CORDA](http://www.8btc.com/ln-rn-corda)
- [A blockchain in 200 lines of code](https://medium.com/@lhartikk/a-blockchain-in-200-lines-of-code-963cc1cc0e54)
- [比特币源码分析](http://blog.csdn.net/u012183589/article/category/7131199)


##技术栈
- **数据存储**
	- 目前为面向高吞吐量的键值数据库levelDB、rocksDB
	- 未来：传统的关系型数据库Mysql、Oracle
	- 大数据平台Hadoop+Habse
	- 下一代分布式版本文件系统IPFS
- **网络通信**
	- 点对点通信：建立虚拟链路，底层对应的物理链路可能随着网络时延抖动的变化（与网络状况、区块大小、区块中交易数量等因素有关）而改变相应的路径
	- 目前主要为无结构化的P2P通信
	- 未来联盟链中可能衍生出结构化的P2P通信
- **加密技术**
	- 哈希函数、非对称加密、数字签名
	- 目前金融系统中使用的国密算法
		- 与	区块链技术对应的是SM2、SM3和SM9国密算法
- **共识机制**
	- 可信任环境中分布式系统的共识机制
		- PaxOS、Raft
		- CAP理论：保留分区容错性（Partition tolerance）前提下，数据最终一致性（Consistency）和系统可用性（Availability）的Trade-off
	- 区块链：不可信环境中的共识
		- PoW、PoS(PPCoin)、DPoS(BitShares)
		- PBFT、RPCA(Ripple)
- **隐私保护**
	- 混币（CoinJoin）
		- 将比特币发送地址和接收地址的关系打断使交易无法被追踪。将多个交易的输入和输出混合，依赖中心化的系统进行
	- 环签名（Ring Signatures）
		- 门罗币（Monero）
		- 环中一个成员利用他的私钥和其他成员的公钥进行签名，验证者只知道签名来自这个环，但不知到谁是真正的签名者。仅仅通过查看环签名不可能辨别是哪个地址发起并最终签署了交易。
	- 零知识证明（ZKPs）
		- 在无需泄露数据本身情况下证明某些数据运算的一种零知识证明，允许两方（证明者和验证者）来证明某个提议是真实的，而且无需泄露除了它是真实的之外的任何信息。在密码学货币和区块链中，这通常是指交易信息数据。
		- Zcash： za-SNARKs
		- [Kosba A, Miller A, Shi E, et al. **Hawk: The blockchain model of cryptography and privacy-preserving smart contracts[C]**//Security and Privacy (SP), 2016 IEEE Symposium on. IEEE, 2016: 839-858.](http://ieeexplore.ieee.org/abstract/document/7546538/)
	- 同态加密
		- 同态加密提供了一种对加密数据进行处理的功能。其他人可以对加密数据进行处理，但是处理过程不会泄露任何原始内容。同时，拥有密钥的用户对处理过的数据进行解密后，得到的正好是处理后的结果。
	-  以太坊 State Channel
		-  一个账本统一打一笔钱到智能合约里，智能合约实现加密，中间的明细怎么改变价值最终的版本等外边是看不见的；等到最后交易完成，再把结果显回到基础上。中间过程部分的隐私是保护了的，但有一个问题是总额进来多少、出去多少，这些保护不了。
	-  ChinaLedger CCP中央对手方
		-  分成A链和B链，事件时序的见证在一条链上，而有效支付的见证在另外一条链上。这个实践顺序加密提交，提交为CCP——中央对手方，由中央对手方来解密、检验签名、检验余额，如果是有效就实现过户，然后加密再回去。
- **安全性**
	- 私钥安全
		- 如何产生私钥的保密算法或者基于身份的新私钥生成算法
	- 研究智能合约的安全
		- 以太坊区块链会遭受的脆弱性攻击
		- 编译原理和虚拟化等技术
- **跨链技术**
	- 不同结构、不同类型的区块链互联互通，面向异构区块链的跨链技术
	- Polkadot（波卡）：以区块链自身作为消息传递媒介
	- Ripple Interledger：通过账本间连接者传递通信消息
	- Aeternity：通过状态通道及路由来支持跨链通信
	- COSMOS
- **链下技术（性能）**
	- 链下完成小额支付，链上清算
	- 比特币闪电网络（Lightning Network）
	- 以太坊雷电网络（Raiden Network）
- **衍生技术**
	- 单链多链结合：英国数字货币RSCoin
	- 埃森哲可编辑区块链：可修改
	- IOTA基于有向非循环图（DAG）区块链：没有链的“分布式账本”

##系统架构、源码阅读
- **Bitcoin**
	- bitcoin-core
	- [lib-bitcoin](https://github.com/libbitcoin/libbitcoin/)
		- 比较推荐这个版本的源码
- **Ethereum**
	- Dapps开发：Solidity+Truffle+Web3+Geth
- **Hyperledger Fabric**
- **Ripple**
	- RPCA共识算法
- **国内**
	- NEO
	- 布萌
	- 微众银行BCOS
- **去中心化交易所**
	- 0x
	- KyberNetwork
	- Loopring
	- Bancor

##学术论文

##开源项目白皮书

##学习、资讯
- **网站**
	- [巴比特](www.8btc.com)：区块链门户网站，包括资讯、技术
	- [区块链铅笔](www.chainb.com)：偏资讯
- **公众号**

##币圈