# 持续集成&持续交付概念

### 前言 {#前言}

随着微服务架构与容器虚拟化技术的发展，持续集成与持续交付的概念又重新回到了大家的视野，越来越多的公司开始使用持续集成的系统来解决频繁发布带来的质量问题；使用持续交付的工具来实现代码在不同环境上的自动部署。原本有些学院派乌托邦式的思想正被千千万万次的集成与部署证明着它应有的价值。

### 持续交付的概念和产生 {#持续交付的概念和产生}

传统软件的开发与交付的周期都很漫长，一款普通的企业软件通常需要十几个开发人员，几个月的时间来完成，从需求的分析、系统的设计、编写测试用例、系统开发、单元测试、组装测试到交付调试。有条不紊的流程与规范像一辆绿皮火车下的枕木，稳定而可靠的保证整个系统缓慢的推进，每一次交付、升级，都需要提供基础的硬件、软件的环境、软件的代码、软件的文档与手册。  
还记得刚刚迈入软件开发行业的时候，跟随公司的服务团队，驻场交付产品，每一个驻场工程师都按照之前预演过好多遍的流程，对照着系统的部署手册，一步一步的组装硬件，安装软件，稍有差池，就要按照对应的应急预案进行回滚。开始的时候觉得交付像一个神圣的仪式，将用智慧和汗水构建成的软件交付给客户使用，是一种非常荣耀和值得骄傲的事情；后来越来越多次的产品交付让我深深的感觉每一次交付都像分娩一样痛苦，扪心自问是否有简单更舒畅的流程可以将软件交付给客户呢？  
[![](https://testerhome.com/uploads/photo/2017/c6dbe7d9-602f-4d80-9443-b697abd8d69f.png!large)](https://testerhome.com/uploads/photo/2017/c6dbe7d9-602f-4d80-9443-b697abd8d69f.png!large)  
要想快速的交付，首先要明白软件交付过程中遇到的核心问题是什么。总结成两个词“自动”与“可靠”。自动是一个很宽泛的词汇，在软件交付中代表着测试自动化、交付自动化、运维自动化等等，而可靠讲的是每一次交付要保证是当前的交付是稳定的或可回滚到稳定版本的。为了解决“自动”与“可靠”的问题，敏捷开发鼻祖Martin Fowler提出了持续集成与持续交付的概念，它所描述的软件开发，是从原始需求识别到最终产品部署到生产环境这个过程中，需求以小批量形式在团队的各个角色间顺畅流动，能够以较短地周期完成需求的小粒度频繁交付。频繁的交付周期带来了更迅速的对软件的反馈，并且在这个过程中，需求分析、产品的用户体验和交互 设计、开发、测试、运维等角色密切协作，相比于传统的瀑布式软件团队，更少浪费。通过这种小步快跑的方式，将小功能快速迭代、验证、交付，通过自动化的工具，将测试、部署、运维自动化，减少需求在软件生命周期中流动的时间。  
[![](https://testerhome.com/uploads/photo/2017/41436a14-8174-48c3-ba5e-e07728768d6c.png!large)](https://testerhome.com/uploads/photo/2017/41436a14-8174-48c3-ba5e-e07728768d6c.png!large)  
《持续交付-发布可靠软件的系统方法》，Jez Humble DavidFarley，2011  
2011年，Jez Humble编著的《持续交付\(发布可靠软件的系统方法\)》出版，持续交付的理念迅速被软件行业接受和流行。该书讲述如何实现更快、更可靠、低成本的自动化软件交付，描述了如何通过增加反馈，并改进开发人员、测试人员、运维人员和项目经理之间的协作来达到这个目标。《持续交付\(发布可靠软件的系统方法\)》由三部分组成。第一部分阐述了持续交付背后的一些原则，以及支持这些原则的实践。第二部分是本书的核心，全面讲述了部署流水线。第三部分围绕部署流水线的投入产出讨论了更多细节，包括增量开发技术、高级版本控制模式，以及基础设施、环境和数据的管理和组织治理。

### 持续交付工具链 {#持续交付工具链}

但是前辈只给了我们先进的思想，并没有给出默认的实现。不同的公司、不同的产品、不同的技术栈、不同的开发与部署形态决定了持续集成与持续交付注定是因人而异的，大家不断摸索什么样的方式是持续集成与持续交付的最佳实践。归根结底，持续集成与持续交付的难点在于如何屏蔽不同语言、不同框架、不同系统之间的持续集成与持续交付流程的差异性。曾经幻想过是否能有一种方式可以归约软件的交付，而这就是Martin Fowler留给我们的课后思考题-论如何实现持续集成与持续交付的流程标准化。  
当你问十个哲学家什么是哲学的时候，你会得到十一种答案，因为每个人都有对哲学不同的理解，对于持续交付也一样。个人选取了目前开源社区中最流行和优秀的开源软件，经过改造后搭建了全开源端到端交付流水线，这应该也是目前各大互联网公司使用最广泛的方案。其中Jenkins作为业内优秀的的CI/CD工具，担任整套了工具链的核心组织工作。  
[![](https://testerhome.com/uploads/photo/2017/58f3b593-06a6-4c28-b579-2dc73d5d1dfc.png!large)](https://testerhome.com/uploads/photo/2017/58f3b593-06a6-4c28-b579-2dc73d5d1dfc.png!large)

国内一些公司开发的轮子【非广告】：  
阿里云效/codepipeline：[https://www.aliyun.com/product/codepipeline](https://www.aliyun.com/product/codepipeline)  
百度效率云：[https://xiaolvyun.baidu.com](https://xiaolvyun.baidu.com/)  
普元devops平台：[http://www.primeton.com/products/devops/](http://www.primeton.com/products/devops/)

### Jenkins 2.0 新时代：从 CI 到 CD {#Jenkins 2.0 新时代：从 CI 到 CD}

自从15年9月底Jenkins的创始人Kohsuke Kawaguchi提出Jenkins 2.0（后称2.0）的愿景和草案之后，整个Jenkins社区为之欢欣鼓舞，不管是官方博客还是Google论坛，大家都在热烈讨论和期盼2.0的到来。16年4月20日，历经Alpha\(2/29\)，Beta\(3/24\)，RC\(4/7\)3个版本的迭代，2.0终于正式发布。这也是Jenkins面世11年以来（算上前身Hudson）的首次大版本升级。  
Pipeline as Code是2.0的精髓所在，是帮助Jenkins实现CI\(Continuous Integration\)到CD\(Continuous Delivery\)华丽转身的关键推手。所谓Pipeline，简单来说，就是一套运行于Jenkins上的工作流框架，将原本独立运行于单个或者多个节点的任务连接起来，实现单个任务难以完成的复杂发布流程。Pipeline的实现方式是一套Groovy DSL\(类似Gradle\)，任何发布流程都可以表述为一段Groovy脚本，并且Jenkins支持从代码库直接读取脚本，从而实现了Pipeline as Code的理念。  
建立持续交付流水线\(Continuous Delivery Pipeline\)是持续交付的前提。作为2.0的核心插件，Pipeline并不是一个新事物，它的前身是Workflow Plugin，而Workflow的诞生是受更早的Build Flow Plugin启发，由Nicolas De Loof于2012年4月发布第一个版本。而纵观Jenkins的几个竞争对手（Travis CI、phpci、circleci），Pipeline早已不是什么新鲜概念。可以说这次Jenkins 2.0的发布是顺势而为，同时也是大势所趋。  
如果要在更大范围探讨Pipelined的产生背景，我认为有三个层面的原因。  
第一层面，与不断增长的发布复杂度有关，其中一个典型场景就是灰度发布。原本只有大公司才有的灰度发布，随着敏捷开发实践的广泛采用、产品迭代周期的不断缩短、数据增长理念的深入人心，越来越多的中小公司也开始这一方面的探索，这对发布的需求也从点状的CI升级到线状的CD。这是Pipeline产生的第一个原因。  
第二层面，与应用架构的模块化演变有关，以微服务为代表，一次应用升级往往涉及到多个模块的协同发布，单个CI显然无法满足此类需求。这是Pipeline产生的第二个原因。  
第三层面，与日益失控的CI数量有关。一方面，类似于Maven、pip、RubyGems这样的包管理工具使得有CI需求的应用呈爆发性增长，另一方面，受益于便捷的Git分支特性，即便对于同一个应用，往往也需要配置多个CI。随着CI数量的不断增长，集中式的任务配置就会成为一个瓶颈，这就需要把任务配置的职责下放到应用团队。这是Pipeline\(as Code\)产生的第三个原因。  
先简单开个头，后续会详细介绍Pipeline的实现。

### 持续交付和Devops的关系 {#持续交付和Devops的关系}

devops（开发到运维）是另外一个现在很火的工程概念，和持续交付的关系很多时候让人傻傻分不清楚。从概念上来说，DevOps更关注Ops\(Operations\), 持续交付更关注Dev \(Development\) 。他们的目标都是解决相同的问题，即加速软件开发，减少软件开发到交付或上线的时间，并使开发、测试、运维几个角色协作的更紧密。一般来说个人倾向于两者说的是同一回事，它们只不过是一枚硬币的正反面而已，在概念上并没有什么争议。  
引用《持续交付》译者乔梁的观点，细微的差别可能就是持续交付体现的是产品交付的完整过程，devops强调的是从开发到运维的交付，传统的持续集成则更强调产品研发过程（开发+测试）。  
[![](https://testerhome.com/uploads/photo/2017/dce7e65c-a4c1-4cb1-8d10-be735394e89b.jpg!large)](https://testerhome.com/uploads/photo/2017/dce7e65c-a4c1-4cb1-8d10-be735394e89b.jpg!large)  
所以，你们开心就好\_^

### 结语 {#结语}

近期主要专注于基于开源框架的CI/CD平台的搭建和具体实现，积累了一些体会，也正在整个公司进行推广和应用。这里先开个头，时间允许的话尽可能把这一系列的文章完成，不要太监哈哈。另外，本篇部分概念和文字引用了其他持续交付相关文章的观点和截图，如有雷同，纯属我个人偷懒。
