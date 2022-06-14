# 星航计划加入申请表

### 个人介绍

* Github ID: [geometryolife](https://github.com/geometryolife)

* Telegram ID: geometryolife

* Discord ID: Joe Chen#0827

* Starcoin 账号地址: 0x910D594c405c8144d3312b697194A8Fb


21年本科毕业，热爱开源，热衷技术。

22年春节开始学习 Rust 语言，目前正在学习中……四月开始接触区块链和 Web3，持续探索中……

常用语言 Rust、Move，对 GNU/Linux、Docker、WebAssembly、Web3 开发方向感兴趣。
热爱写作，[starcoin-cookbook](https://github.com/starcoinorg/starcoin-cookbook) 修补匠。

曾经学习的东西过于杂，而又缺少实践的机会，导致知识体系混乱，现在决定从前端作为入口重新整理自己的知识体系。
目前刚开始学习前端，Starcoin 是我最好的起点，希望能与大家共同成长。


### 学习日志

# 2022年4月27日

- Work List
  - 看视频和视频了解区块链相关的内容
    - [x] [吸金千万潮牌跨界赚钱，热门明星NFT你还不知道？](https://b23.tv/zAC75Fk)
    - [x] [如何通过DeFi实现暴富？纯干货分享，小白必看！](https://b23.tv/Lz1LRLo)
    - [x] [词汇表：元宇宙 & Web3](https://b23.tv/Fg5ycYz)
    - [x] [关于Web3: 退休这两年我错过的技术趋势](https://guoyu.mirror.xyz/f2yLu59TJ4u07FQ13UmiN4-cLELv3g-qQirY7YF_Qyw)
  - [x] 在 Windows 上编译 starcoin
  - [x] 提关于 starcoin 在 Win 上编译失败的 issue

- Summary

今天一整天都在尝试解决 Windows 平台上 Starcoin 编译错误的问题，最后还是无法解决，只能先提个 issue 了。

# 2022年4月26日

- Work List
  - 看视频了解区块链相关的内容
    - [x] [三分钟了解主流币之以太坊和以太币（ETH）](https://zhuanlan.zhihu.com/p/43979032)

- Summary

今天想把之前看过的 Move 语言教程动手敲一次，结果环境跑不起来，然后开始捣鼓环境。
在解决问题的过程中发现 WSL2 限制太多，尝试了很多方法都没解决。
明天打算在 Windows 上试试～

# 2022年4月25日

- Work List
  - 看视频了解区块链相关的内容
    - [x] [Aptos 未来100x 的新一代公链？ 有没有机会干掉 ETH2，Solana，Polkadot？](https://b23.tv/V1DnAia)
    - [x] [btc-code-2009-2018](https://b23.tv/XvNkHHu)
  - [x] 提交 PR - 添加中文写作规范
  - [x] 提交 wsl troubleshooting 并保持中英文同步

- Summary

工作上，修改了 starcoin-cookbook 的贡献指南，增加了中文撰写规范以及增加了 wsl 编译 starcoin 的 troubleshooting，保持中英文同步。
今天花的时间还是挺多的，修改文档不是件容易的事，尤其是需要把它做到尽可能地好。

# 2022年4月24日

- Work List
  - 看视频和文章了解区块链相关的内容
  - [x] [玩转智能合约开发NFT项目|NFT开盲盒设定价格带Mint功能背后的技术原理！自动生成NFT上传Opensea](https://b23.tv/3BeaOaI)
  - [x] [最简单的NFT制作免费上传出售教程NFT中国OpenSea上传作品](https://b23.tv/tIz9n6J)
  - [x] [12岁的他靠自制NFT，放完一个暑假赚进300万元！发豪言要当下个马斯克贝索斯](https://b23.tv/aroSKoq)
  - [x] [【上】NFT行业会在严管中倒下吗？](https://b23.tv/FkyVeJd)
  - [x] [LLVM之父Chris Lattner：编译器的黄金时代](https://zhuanlan.zhihu.com/p/502730940)
  - [x] [SWAP问答：SWAP是什么？SWAP有什么用？SWAP怎么用？](https://www.daweibro.com/node/206)
  - [x] [Linux交换空间（swap space）](https://segmentfault.com/a/1190000008125116)

- Summary

今天继续解决昨天在 WSL2 上编译失败的问题，我得到了不少收获：
通过查看编译报错信息，Google 后明白了是因为 swap 内存不足。
查看发现，我的 WSL2 的 swap 大小只有 4 G，而内存分配有 12 G，我恍然大悟。
编译过程中耗尽内存，往往会导致进程退出或其它问题的出现。
如果启用了交换内存功能，那么，当内存不足时，就会把一部分未使用的内存转移到 swap 上。
所以网上会有一种常见的说法，swap 到底要设置多大才合适，通常会告诉你设置成两倍内存大小。

我尝试用 Linux 设置 swap 交换文件的方法修改 swap，但是失败了。最让我震惊的时，我 Windows 上的内存爆了。
当我创建了一个 16 G 的交换文件后，实体机的内存消耗几乎达到100%，这让我很诧异。
搜索后发现，原来 Windows 有专门提供修改 WSL2 内存和 swap 交换文件的配置文件 `.wslconfig`。

知道了 Windows 默认给 WSL2 分配总内存的80%。比如，我的电脑 16 G，当 WSL2 使用内存接近100%时，实体机消耗的内存大约为 12 G～13 G。
这时会产生一个有趣的现象，电脑风扇响了（内存使用超过80%），这说明电脑内存处在一个稳定的高消耗阶段。
WSL2 运行在一个虚拟内存进程 `Vmmem` 上，这个进程的内存上限是在 `.wslconfig` 中设置的内存大小。

在 WSL2 上编译速度实在是太慢了，下次还是得直接使用实体机来编译。

# 2022年4月23日

- Work List
  - 看视频和文章了解区块链相关的内容
    - [x] [NFT项目操作指南，你必须熟悉的7个数据指标，让你快速掌握NFT项目实战技巧。](https://b23.tv/RG0zCMB)
    - [x] [BRP匿名公链，会是区块链的未来吗？【不构成任何投资建议】](https://b23.tv/LrNTiRp)
    - [x] [区块链技术2022年的发展趋势会是怎样呢？](https://www.zhihu.com/question/528308531)
      - [x] [A1](https://www.zhihu.com/question/528308531/answer/2442643240)
      - [x] [A2](https://www.zhihu.com/question/528308531/answer/2447701991)
    - [x] [Rust Ruby on Rust - 用 Rust 编写 RubyGem Extension 提升 600% 的性能](https://ruby-china.org/topics/42336)
    - [x] [关于区块链技术及业务的三个陷阱，而我们又该如何避免它们](https://cn.weforum.org/agenda/2019/12/guan-yu-qu-kuai-lian-ji-shu-ji-ye-wu-de-san-ge-xian-jing-er-wo-men-you-gai-ru-he-bi-mian-ta-men/)
  - [x] 添加区块链相关术语
  - [x] 尝试编译 starcoin

- Summary

今天还是在了解 Starcoin 并尝试编译 Starcoin，但是编译失败了，还未找到具体原因，明天再试试。
下午给 git alias 添加了一些内容，晚上收集了不少区块链相关的术语。

# 2022年4月22日

- Work List
  - 看视频了解区块链相关的内容
    - [x] [大厂入局，“数字藏品”成为新风口](https://b23.tv/0lwJY2a)
    - [x] [数字藏品NFT是骗局？白话解析国内数字产品真相](https://b23.tv/0gQcgJD)
    - [x] [2022怎么通过NFT赚钱—opensea的使用攻略](https://b23.tv/hrdoK1q)
    - [x] [程序员怎么看元宇宙和NFT？](https://b23.tv/HjNiLjy)
    - [x] [Opensea 自动生成1万张NFT 各部位随机组合](https://b23.tv/AW1Uds9)
    - [x] [元宇宙新闻 2022年3月 e](https://b23.tv/kqZF6eB)
  - [x] 看文章了解区块链相关的内容
    - [x] [怎么理解Web 3.0？](https://mp.weixin.qq.com/s/aKMyrT07ISXmgq6Aj33GRQ)
    - [x] [Github提交不记录Contributions](https://yuhongjun.github.io/tech/2017/04/26/Github提交不记录Contributions.html)
  - [x] 读官网的博客

- Summary

今天在捣鼓 Win 上的各种环境，把 starcoin-cookbook 加了些批注，读了一些 Starcoin 的博客。

# 2022年4月21日

- Work List
  - 看视频了解区块链相关的内容
    - [x] [美国最大NFT行业展，市场最前沿机会【牛尔摩斯深度分析】](https://b23.tv/854YKRf)
    - [x] [Metamask：Web3.0世界的入口](https://b23.tv/mONk7hm)
    - [x] [【尚硅谷-web】i18n国际化](https://b23.tv/VPcM0ug)
    - [x] [在Idea中高效的处理JAVA国际化、多语言 、i18n | 哎呦，洋气的不得了诶](https://b23.tv/o5SH2YY)
    - [x] [基于Vue的国际化i18n](https://b23.tv/rG8dH8z)
    - [x] [rails 国际化 i18n](https://b23.tv/AJIsXre)
  - [x] 看文章了解区块链相关的内容
    - [x] [基础知识回顾，I18N是什么，什么是国际化？](https://www.cnblogs.com/dkblog/archive/2008/06/30/1980790.html)
    - [x] [区块链：DAO 去中心化自治组织 —— 一篇文章彻底搞明白](https://mirror.xyz/0xcd3722b43f684d2aaeee7c769533cA31d3e0375e/aS2VSASeQS9Id2w8wbTyfs0AopZvSg0oUAtJo_Lw6KA)
    - [x] [什么是去中心化交易平台(DEX)？](https://academy.binance.com/zh/articles/what-is-a-decentralized-exchange-dex)
  - [x] 深入了解 starcoin-cookbook
  - [x] 读经济模型白皮书

- Summary

今天一直尝试了解 i18n，原先以为是一个自动翻译插件，到后来弄明白了，它只能翻译某些部分的内容，主体翻译还是需要自己去翻译的。
今天几乎花了一整天了解 Starcoin 的 cookbook，但是感觉有些东西还是没能很理解，明天继续干！

# 2022年4月20日

- Work List
  - 看视频了解区块链相关的内容
    - [x] [比特币和区块链啥原理？矿机挖矿咋回事？李永乐老师讲比特币（1）](https://youtu.be/g_fSistU3MQ)
    - [x] [比特币交易如何防伪？私钥公钥地址啥意思？李永乐老师讲比特币（2）](https://youtu.be/pbAVauYsqP0)
    - [x] [打工人把握好下一个时代风口：Web3](https://b23.tv/QbhRVuv)
    - [x] [Web3.0全景生态解析，就业/投资怎么选？](https://b23.tv/5LWl506)
    - [x] [【以太坊创始人V神】3分钟告诉你什么是以太坊](https://b23.tv/tvFkXTj)
    - [x] [以太坊之父成功之路，19岁拥亿万资产，V神有多神？中本聪接班人？危机关头硬分叉，以太币由来不得不知的传奇](https://b23.tv/3zTGbJA)
    - [x] [【热门NFT项目】发行价2.5 ETH 的Moonbirds 什么来路？现在正在抽白名单不要错过!](https://b23.tv/0jVPCHI)
    - [x] [普通人如何参与NFT？手把手教你如何寻找早期NFT项目与判断稀有度](https://b23.tv/DqRaPuy)
    - [x] [用最通俗的话告诉你什么是NFT与元宇宙](https://b23.tv/8xpZYXw)

- Summary

今天研读了 Starcoin 的技术白皮书，对 Starcoin 的设计理念有了深入的认识，不过有些概念还是弄不太清楚。
我对这篇白皮书的内容大概吸收了60%～70%，今天也看了很多关于区块链和 Web3 的概念视频。

在 YouTuBe 找了李永乐老师讲解比特币和区块链原理的视频，终于弄懂了去中心化账本、区块、链、挖矿概念、手续费、打包奖励、挖矿原理、身份认证、电子签名、公私钥、广播、双重支付、防止篡改、最长链……这些关系了。
知道了比特币发行总量2100万个。
理解了这些概念后，回看了之前看的关于钱包的视频，对钱包地址、公钥、密码、私钥、助记词、keystore 这些概念已经很清晰了。
然后看了 StarMask 使用多签账户的视频，明白了多签账户的用法。
在此基础上回看了之前关于[叔块](https://www.bcskill.com/index.php/arc  hives/1300.html)的这篇文章，对于孤块和叔块的概念有了清晰的认识。

### 学习成果

#### issue

- [x] [issue - Bug Report: starcoin_generator output ERROR field in help message #3423](https://github.com/starcoinorg/starcoin/issues/3423)
- [x] [fix issue - cannot compile on windows #3369](https://github.com/starcoinorg/starcoin/issues/3369)
- [x] [fix issue - Excessive swap may result in slower builds #70](https://github.com/starcoinorg/starcoin-cookbook/issues/70)
- [x] [issue - The account name will be reset every time log in](https://github.com/starcoinorg/starmask-extension/issues/62)

#### pr

- [x] [pr - add create a custom network #101](https://github.com/starcoinorg/starcoin-cookbook/pull/101)
- [x] [pr - 撰写 Linux 和 Docker 版本的加入主网络的教程](https://github.com/starcoinorg/starcoin-cookbook/pull/98)
- [x] [pr - 添加挖矿内容缺失的索引，add index for mining and add researcher chinese #96](https://github.com/starcoinorg/starcoin-cookbook/pull/96)
- [x] [pr - 添加 Windows 加入主网的内容](https://github.com/starcoinorg/starcoin-cookbook/pull/98)
- [x] [pr - 修改 windows 接入 Starcoin 控制台的错误命令](https://github.com/starcoinorg/starcoin-cookbook/pull/98)
- [x] [pr - add move prover english version #95](https://github.com/starcoinorg/starcoin-cookbook/pull/95)
- [x] [pr - fix typo for develop dapp #197](https://github.com/starcoinorg/starcoin-org-v2/pull/197)
- [x] [pr - add multisignature concept #94](https://github.com/starcoinorg/starcoin-cookbook/pull/94)
- [x] [pr - update dev network #91](https://github.com/starcoinorg/starcoin-cookbook/pull/91)
- [x] [pr - update test network #92](https://github.com/starcoinorg/starcoin-cookbook/pull/92)
- [x] [pr - update multi-signature accounts and multi-signature transactions #89](https://github.com/starcoinorg/starcoin-cookbook/pull/89)
- [x] [pr - 翻译多签账户和多签交易的文档](https://github.com/starcoinorg/starcoin-cookbook/pull/89)
- [x] [pr - add doc searcher #86](https://github.com/starcoinorg/starcoin-cookbook/pull/86)
- [x] [pr - update first transaction #88](https://github.com/starcoinorg/starcoin-cookbook/pull/88)
- [x] [pr - fix error command for windows #196](https://github.com/starcoinorg/starcoin-org-v2/pull/196)
- [x] [pr - update work with starcoin console #80](https://github.com/starcoinorg/starcoin-cookbook/pull/80)
- [x] [pr - update account manage #81](https://github.com/starcoinorg/starcoin-cookbook/pull/81)
- [x] [pr - update build from source link #3407](https://github.com/starcoinorg/starcoin/pull/3407#event-6605575098)
- [x] [pr - add a troubleshooting for building in Windows #79](https://github.com/starcoinorg/starcoin-cookbook/pull/79)
- [x] [pr - add the troubleshooting of slow compilation #74](https://github.com/starcoinorg/starcoin-cookbook/pull/74)
- [x] [pr - update starcoin usage #75](https://github.com/starcoinorg/starcoin-cookbook/pull/75)
- [x] [pr - add move package system concept #69](https://github.com/starcoinorg/starcoin-cookbook/pull/69)
- [x] [pr - Increase the interpretation of black words #3392](https://github.com/starcoinorg/starcoin/pull/3392/files#)
- [x] [修改- add mpm reference #59](https://github.com/starcoinorg/starcoin-cookbook/pull/59)
- [x] [pr - update mpm reference #63](https://github.com/starcoinorg/starcoin-cookbook/pull/63)
- [x] [pr - fix option --test help message #112](https://github.com/move-language/move/pull/112)
- [x] [collaborate & review - Accumulator docs #64](https://github.com/starcoinorg/starcoin-cookbook/pull/64)
- [x] [pr - add mpm reference #59](https://github.com/starcoinorg/starcoin-cookbook/pull/59)
- [x] [pr - fix typo of help information of mpm check-compatibility #3387](https://github.com/starcoinorg/starcoin/pull/3387)
- [x] [pr - 更新 mpm 中英文的内容](https://github.com/starcoinorg/starcoin-cookbook/pull/50)
- [x] [pr - 增加缺失 `cc` 链接器的排错内容](https://github.com/starcoinorg/starcoin-cookbook/pull/55)
- [x] [pr - add user guide of move package manager zh version #50](https://github.com/starcoinorg/starcoin-cookbook/pull/50)
- [x] [pr - add starcoin help message to reference #41](https://github.com/starcoinorg/starcoin-cookbook/pull/41)
- [x] [pr - replenish install by docker](https://github.com/starcoinorg/starcoin-cookbook/pull/40)
- [x] [pr - move 语言简介](https://github.com/starcoinorg/starcoin-cookbook/pull/38)
