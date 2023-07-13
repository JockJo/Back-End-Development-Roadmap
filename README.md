# Back-End-Development-Roadmap

十年鹅厂：后台开发技术图谱，后台开发成长Roadmap

## 题记

从2013年毕业加入鹅厂，不知不觉已然过去10年。期间团队一直有同学反馈，有时对个人成长有些迷茫，缺少一个后台开发的全景技术图谱，来建立起体系化的知识结构。这里结合自己的后台研发经验，把实战中觉得重要的技能点，整理一个后台开发的成长RoadMap，希望最后给大家的成长一些参考和帮助

简单把成长RoadMap分成4个阶段：

1. **后台基础（初级）**：掌握牢固的后台基础（go、os、tcpip...）并能熟练运用，为后面的发展打下地基
2. **工程素养（中级）**：写出一手好代码，有扎实的微服务工程能力，运用好云原生和DevOps持续提升工程效率
3. **项目架构（高级）**：有扎实严谨的系统架构设计能力，独立主导大中型项目落地，一切尽在掌握中
4. **综合素养（专家）**：技术更多是工具，掌握管理、产品、商业、高效沟通协作等多维度能力，帮助业务创造价值

当然，研发是个非常重实践的活，快速过遍RoadMap有体系化的认识，重点还是日常工作的不断实践和精进。时间较仓促赶的初稿，后续持续更新并补些参考材料和书籍，如果内容有错误和疏漏，帮忙多评论指正

## 后台基础篇（初级）

### 编程语言

- **语法**：数据类型、流程控制 if/for/switch、函数 func（闭包问题）
- **变量**：声明var/短变量声明:=/重声明、指针（自动推导？）、作用域、类型推断 type
- **赋值**：深拷贝和浅拷贝区别
- **类型转换**：类型断言表达式x.(T)，使用泛型Any
- **容器**：array/slice/set/map/sync.map，各容器的底层结构/操作性能/扩容策略/并发安全
- **数据结构和算法**：queue/stack/heap、sort、使用gods库
- **面向对象OOP**：struct/interface，组合的优缺点，值方法和指针方法区别
- **并发**：goroutine/channels（源码走读），协程生命周期，无锁FIFO实现
- **协程调度器**：GMP模型，MP数量和调度关系，抢占式调度策略
- **内存管理**：内存分配器/垃圾回收器，GC/STW/三色标记法，栈空间/逃逸分析优化
- **并发控制**：sync.WaitGroup/sync.Once，主协程等待子协程方法
- **上下文**：context.Context，层级关系，取消信号context.WithCancel
- **同步机制**：sync.Mutex/sync.RWMutex/sync.Cond/sync.atomic，各类的使用场景
- **网络**：net net.Dial、rpc socket、http net.http，高性能golang服务器实现
- **缓冲区操作**：strings.Builder/bytes.Buffer，io.Reader/io.Writer，性能对比和适用场景
- **对象池**：sync.Pool，性能优化原理
- **文件**：os.File，各类文件操作 os.OpenFile/os.Create
- **常用第三方库**：gin/grpc-go（学习源码），protobuf/go-redis/gorm/kafka，看实际业务场景
- **错误处理**：errors、panic/defer/recover、链式错误码Wrapping
- **测试**：go test，单元测试Test（testing/assert）、性能测试Benchmark
- **调试分析**：net/http/pprof、火焰图go-torch
- **包管理**：Go Modules、版本管理、路径管理 GOPATH（src/bin/pkg）、package

### 数据结构和算法

- **复杂度分析**：空间复杂度、时间复杂度（平均/最好/最坏）
- **线性表**：数组/链表/队列/堆栈，FIFO/LIFO模型，面试蛮多链表操作题目（如链表反转）
- **字符串匹配**：单串 BM/KMP；多串 字典树Trie/AC自动机/后缀数组，解决子串/回文等问题
- **排序**：二分查找，冒泡/插入/归并/堆排序/快速排序，掌握快排思路，使用sort.Sort()实现自定义排序
- **散列表Hash**：哈希算法，解决冲突（拉链/开放地址），动态扩容方案（参考java/golang）
- **跳表**：有序链表+多层索引，Redis使用跳表原因，实现有序Map对比红黑树优缺点
- **二叉树**：平衡二叉树/完全二叉树，AVL数/红黑树，java使用红黑树实现TreeMap原因
- **多路查找树**：B树/B+树，mysql使用B+树实现索引原因
- **堆**：大小顶堆，建堆/Fix()，解决优先队列/TopK/中位数问题，使用container/heap实现
- **动态规划DP**：核心是找到最优子结构（分治），解决背包等问题
- **搜索**：回溯/递归、深度dfs/广度bfs/启发式A*、记忆化搜索，解决数独/八皇后/旅行商等问题 
- **图**：邻接矩阵/邻接表、拓扑排序、最短路径 dijkstra/spfa/floyd，网络流/最大流 EK
- **其他**：数论&几何、位图Bitmap、并查集、线性规划等

### 操作系统

- **基础命令**：目录cd/ls/pwd、文件vim/cat/grep/awk、查询find、安转yum...
- **定位调试**：进程ps/strace、资源top/vmstat/iostat、网络netstat/tcpdump、文件lsof/du/df
- **经典x86架构**：Intel 8086，CPU/指令集架构/寄存器/总线/内存RAM/IO设备
- **系统调用**：进程fork/exec、信号kill/sigaciton、内存mmap、文件open/read/write、网络socket
- **进程管理**：进程/线程/协程区别，进程调度策略 抢占式/协作式，进程分类 IO/CPU密集型
- **进程间通讯IPC**：原子操作/共享内存/信号量/Socket，各个的原理和适用场景
- **进程地址空间**：进程独立，内存映射 物理->虚拟，函数栈/堆/内存映射/代码.全局变量.BSS
- **内存管理**：伙伴系统和slab分配器原理、内存映射mmap、交换空间swap
- **虚拟化和容器化**：KVM/容器Docker，隔离技术 Namespace/cgroup

### 计算机网络

- **TCP/IP协议栈**：物理链路层MAC/ARP、网络层IP、传输层TCP/UDP、应用层HTTP/FTP/DNS
- **连接状态**：TCP三次握手和四次挥手的过程，11种TCP状态的状态转换图
- **拥塞控制**：TCP拥塞控制算法和滑动窗口机制，粘包/顺序问题和解决方案
- **常见问题**：单机大量TIME_WAIT/CLOSE_WAIT连接原因，SYN/FIN洪水攻击和解决方案
- **定位工具**：netstat/tcpdump、连通性ping/dig/traceroute/nslookup、网卡ifconfig、防火墙iptables
- **Socket编程**：常用api/option，缓冲区大小/地址重用/立即关闭LINGER/禁用Nagle算法等
- **链接池**：短连接和长连接的区别和应用场景，链接池的大小设置
- **连接心跳保活**：KeepAlive心跳保活机制，应用层和TCP层心跳区别和联系
- **I/O模型**：同步/异步/阻塞/非阻塞，IO多路复用 select/epoll
- **网络模式**：单进程/多进程/多线程，PPC/TPC优缺点，Reactor/Proactor模型和性能优化
- **高性能网络编程**：单机并发链接数上限，C10K/C10M问题和解决思路（多路复用/网络模式/零拷贝/选项优化等）
- **HTTP**：HTTP1.x/2/3区别，GET/POST区别，常见状态码和请求头，KeepAlive机制，Cookie/Session区别...
- **HTTPS**：和HTTP的区别，SSL/TLS连接创建和认证过程
- **QUIC**：和HTTP的区别，基于UDP的优势和应用场景，低延迟和高吞吐的优化原理
- **WEB安全**：常见WEB安全问题，CSRF/XSS/CROS/跨域/域名劫持等问题和解决方案
- **DNS**：从URL输入到页面展现流程，LocalDNS问题和HTTPDNS优化

## 工程素养篇（中级）

### 编码能力

- **代码管理**：Monorepo/Multirepo，理解大仓优缺点，代码复用/依赖管理/代码规范审查/构建工具链建设
- **代码架构**：MVC/DDD，理解DDD分层架构设计思想，用户接口层/应用层/领域层/基础设施层
- **目录结构**：规范清晰layout，参考 https://github.com/golang-standards/project-layout
- **设计原则**：SOLID原则 单一指责/开闭原则/接口隔离...，KISS/DRY/YAGNI/LOD原则 防止过度设计/不写重复代码...
- **设计模式**：掌握几种常用模式 单例/工厂/代理/适配器模式....
- **代码质量标准（坏味道）**：可读性/可扩展/可维护/可测试；分层清晰/模块化好/简洁易懂/规范一致/代码复用...；
- **编码风格**：规范命名/注释/函数/错误处理等，参考 https://google.github.io/styleguide/
- **编码细节**：业务逻辑、规范、边界、异常、性能、日志、并发、安全、兼容...
- **单元测试**：TDD设计思路，编写可测试性代码，依赖注入mock，UT的ROI和覆盖率权衡
- **代码评审**：需求拆小，小批量CR<200行，参考 https://google.github.io/eng-practices/review/
- **静态代码检查**：了解Coverity/Gometalinter等工具的检查规则集，设置规范/安全/团队一致性约束质量红线
- **代码度量**：关注规范问题数/安全问题数/圈复杂度/重复代码率...

### 微服务架构

- **架构演进**：单体应用/分布式SOA/微服务/服务网格，了解微服务和SOA的区别
- **RPC框架**：gRPC/Spring/tRPC（源码走读），高性能网络模型实现，插件化架构AOP，微服务治理组件
- **序列化协议**：protobuf/json/xml，性能和压缩空间对比，序列化原理tlv，反射和动态解析特性
- **服务注册和路由发现**：etcd/consul/zk/polaris，分SET等动态路由功能
- **配置中心**：etcd/zk/apollo，数据高可用方案，选主和解决脑裂问题
- **服务网关**：Kong/Zuul，收拢API注册/认证授权/入口协议/限流熔断/优雅下线/日志监控等能力
- **负载均衡**：常见策略 轮询/随机/权重，一致性Hash实现原理和节点扩缩容Key迁移策略
- **访问限流**：Hystrix/polaris，分布式限流实现方案，限流算法 计数器/滑动窗口/漏桶/令牌桶，常见业务限流维度
- **故障熔断**：服务健康检测机制，服务熔断的触发和恢复条件，全死全活保护策略
- **自适应过载保护**：微服务运行指标自适应 CPU/等待队列/超时请求等

### 中间件（redis/mysql/kafka）

**redis相关**：

- **应用-基础**：常见数据类型，性能和慢操作 bigkey/hotkey，批处理 pipeline
- **应用-缓存**：缓存穿透/击穿/雪崩的解决方案，过期删除策略 惰性/定期，内存淘汰策略 8类 LRU/LFU，
- **应用-并发访问**：单命令INCR/DECR，Redis-Lua，事务ACID MULTI/EXEC，分布式锁 SETNX 对比zk/consul
- **应用-消息队列**：数据类型List和Streams，PUB/SUB，消息组 XADD/XREADGROUP/XACK
- **系统-高性能**：线程模型 单线程（规避并发控制），数据结构 压缩表/跳表，网络框架 epoll，内存管理 jemalloc
- **系统-高可用**：冗余部署 主从复制（副本），持久化方案 AOF/RDB，HA集群 哨兵机制 sentinel
- **系统-易扩展**：可伸缩性 数据分片（分区），负载均衡，集群方案 replication/sentinel/cluster

**mysql相关**：

- **应用-SQL优化**：执行计划 explain，慢SQL分析 mysqldumpslow，链接管理 show processlist
- **应用-事务**：ACID，隔离级别 RC/RR 脏读/幻读/不可重复读，版本控制 MVCC
- **应用-锁机制**：全局锁/表锁/行锁，行间锁
- **系统-高性能**：存储引擎 InnoDB，索引 B+树
- **系统-高可用**：主从复制 同步/半同步/异步，日志 binlog/redolog，binlog模式 ROW、落盘策略
- **系统-可扩展**：业务分离、读写分离、分库分表/数据分区、sharding
- **系统-可运营**：认证授权、SQL误操作、SQL注入、参数配置、监控指标、排障调优、计费方案

**kafka相关**：

- **应用-基础**：主题Topic/分区Partition/副本Replica、生产Producer/中转Broker/消费Consumer、消息Record/位移Offset
- **应用-消息模型**：消费者组Consumer Group，点对点模型p2p vs 发布订阅模型pub/sub
- **应用-消息队列特性**：消息可靠性（不丢消息）、消息顺序性、消息唯一性
- **应用-流计算**：分布式流平台Kafka Streams
- **系统-高性能**：磁盘顺序读写/零拷贝机制等，重平衡Rebalance，消息延迟和堆积
- **系统-高可用**：副本机制Replica，Leader/Follower，HA系统 基于zk的controller
- **系统-可扩展**：分区机制Partition，负载均衡策略
- **系统-可运营**：认证授权、运营操作、参数配置、监控指标、排障调优、计费方案

### 云原生&DevOps

- **研发流程**：宣讲、方案、编码、代码CR、测试、发布、运营
- **云原生应用**：CNCF Landscape/Trail Map，docker/k8s/istio，云原生成熟度
- **开发环境**：一键环境搭建（机器/配置/代码），开发IDE VSCODE/JetBrains，本地开发&远程调试
- **代码仓库 Git**：基本工作原理（暂存区/本地/远程），常用操作，冲突解决方法...
- **分支管理**：常见策略优缺点（Git flow/Github flow/Gitlab flow），主干开发&特性开关
- **CI/CD**：平台工具 Jenkins/TravisCI/GitLab，自动化流水线设计，工作流 XaC/GitOps
- **环境管理**：多环境 Pro/Rre/Test/Dev，环境路由标记和数据隔离方案
- **自动化测试**：金字塔模型 UT/API/UI，集成测试方案，测试左移和右移方案
- **部署发布**：灰度发布/滚动发布/蓝绿部署/红黑部署，多SET部署方案（SET探活/流量切换） 
- **自动化HPA能力**：服务无状态化&容器化，模板编排&瘦容器SideCar，参数调优（利用率/探针...）
- **系统可观测**：Logging/Metrics/Tracing，全景看板，组件核心监控（DB同步距离/MQ未消费数）
- **效率工具**：持续利用工具提效，快捷键/IDE插件/脚手架/工具包/机器人/chatGDP...
- **研效度量**：质量指标 MTTR/MTBR/故障数/缺陷数/安全漏洞数，效率指标 需求吞吐量/部署频率/需求研发周期 feature lead time...

## 系统架构篇（高级）

### 高性能

- **容量预估**：用户路径梳理，接口裁剪&QPS预估，关注木桶效应（前端/接入/逻辑/存储/依赖第三方）
- **全链路压测**：请求标注&环境隔离，流量复制 TcpCopy/GoReplay，用例校准，瓶颈定位，环境清理&用例回归
- **横向扩容 Scale-out**：逻辑层做分布式微服务拆分，存储层引入分布式数据库提升伸缩性
- **访问限流**：业务侧提前预约/设验证码/限制重试，系统侧基于API网关做限流熔断/过载保护
- **性能分析**：链路追踪 Tracing，应用分析 pprof/torch，性能4大金刚（CPU/内存/磁盘/网络）
- **服务性能优化实践**：关注锁粒度/异步处理/日志缓冲/队列丢包/内核参数net.core.somaxconn...
- **数据库优化**：分片sharding（TiDB）、业务分离、读写分离、链接池&链接代理、慢SQL优化、参数调优...
- **缓存Cache**：本地缓存/分布式缓存区别，读写策略，关注缓存穿透/击穿/雪崩问题，关注BigKey/HotKey
- **消息队列MQ**：流量削峰/异步处理/应用耦合、消息可靠性/顺序性/唯一性（重试/幂等），关注消息延迟堆积监控
- **静态资源**：CDN加速，预加载策略 Preload，图片优化（格式webp/合并sprite/压缩/懒加载）

### 高可用

- **影响因素**：机房故障、网络抖动、计算/存储资源不够、代码bug、依赖系统问题、城市级不可抗地震水灾...
- **衡量指标**：可用性百分比（x个9），服务等级协议 SLA，MTBF&MTTR
- **故障模式与影响分析 FMEA**：挖掘系统可用性隐患，业务功能/故障模式/影响范围/风险程度/解决措施/规划代办...
- **冗余架构**：同城双活（基础要求），两地三中心（评估ROI/功能分级/跨IDC数据同步方案）
- **业务隔离**：业务按重要性分级，基于业务/地域/编号做分SET部署和灰度发布，关注SET预留容量
- **快速故障转移**：客户端做失败重试，API网关做故障判定和转移，引入HA/健康心跳/长短连拨测策略
- **核心路径柔性降级**：偏产品策略，接口失败放过/补默认数据/用缓存数据/直播降码率...
- **运营保障**：例行全链路压测，混沌工程&容灾演练，特性开关做快速恢复，活动报备，值班巡检和SOP...

### 可扩展

- **设计原则**：合适/简单/演进，模块高内聚低耦合，适当重构
- **分层架构**：用户层/接入层/逻辑层/基础层/存储层，明确各层职责，降低系统耦合度
- **微服务模块化**：基于DDD做服务模块拆分，变化/稳定分离，接口隔离，没跨模块数据层调用

### 系统安全

- **理论基础**：安全原则CIA 机密性/完整性/可用性，黄金法则 认证/授权/审计
- **密码学**：熟悉3种经典加密算法及场景，对称加密AES/非对称加密RSA/散列算法SHA256加盐（不可逆）
- **Web安全**：熟悉4类常见攻击 XSS/SQL/CSRF/SSRF，攻击原理/危害案例/防御方案
- **数据安全**：用户隐私类等敏感数据（手机号/身份证），全流程加密传输（https）和加密存储（AES）
- **云组件安全**：云账号拆细，关注弱密码和最小授权原则，定期云顾问安全扫描...
- **编码安全**：集成安全扫描门禁，关注明文秘钥/越权漏洞/高危组件/参数校验/日志审计...
- **黑灰产对抗**：提升黑产成本，业务侧条件限制/用户限频/链路鉴权/业务风控/机器学习，防误伤弹验证码...
- **业务安全**：清晰业务安全隐患点，关注账号安全/内容安全/支付安全/活动薅羊毛/防盗版/防欺诈/短信炸弹...

### 典型业务系统

- **接入系统**：怎么做用户的长链接管理？
- **账号系统**：怎么实现微信/QQ/手机号多种方式登陆和绑定？
- **支付系统**：怎么解决分布式事务问题？
- **消息IM系统**：怎么保证消息的实时性/可靠性/顺序性/唯一性？
- **直播系统**：怎么做流媒体协议选型？怎么优化核心音视频指标？
- **资料系统**：怎么做好DB和缓存的数据实时同步？
- **搜索推荐**：怎么提高搜索推荐的准确率和召回率？
- **活动运营**：怎么做低代码能力复用？怎么防用户薅羊毛？
- **广告系统**：怎么做好计费的反作弊？
- **开放平台**：怎么做好OpenApi的认证和授权？
- **数据仓库**：怎么实现分布式数据平台和智能BI报表？

### 项目实战

- **项目介绍**：介绍下这个项目？
- **承担角色**：你在项目中担任什么角色？团队怎么分工协作？
- **业务数据**：关注哪些业务核心数据？具体数据是多少？
- **竞品分析**：当时项目在行业内竞品有哪些？你们有什么业务/技术竞争力？
- **技术难点**：这个项目有什么技术难点？你是怎么解决的？
- **选型对比**：项目每个技术难点的行业方案是怎么样的？有没有进行选型对比？
- **架构设计**：项目的系统架构和技术栈是怎么样的？每个点是否合理？
- **系统瓶颈**：当前系统的瓶颈在哪里？用户量/数据量扩大100倍能否支撑住？
- **海量高并发**：该项目你是怎么支持海量高并发的？
- **系统高可用**：该项目你是怎么做系统高可用的？
- **可扩展性**：该项目你是怎么提高系统可扩展性的？
- **系统安全**：整个项目的业务和系统安全你关注哪些方面？具体做了哪些保障措施？
- **运营成本**：项目运营成本由哪些构成？有哪些成本优化方案？
- **系统部署**：项目当时接入/逻辑/存储是怎么部署的？哪些城市？多少核心？是否合理？
- **依赖组件**：依赖哪些中间件？版本和配置是什么？对应单价是多少？
- **技术指标**：关注哪些系统技术核心指标？值是多少？有什么优化方案？
- **监控体系**：项目的监控体系是怎么搭建的？发现问题到问题恢复一般要多久？
- **故障机制**：发生过最大的故障是什么？怎么解决的？有什么经验总结？
- **用户反馈**：用户反馈流程是怎样的？日常反馈量和主要问题？客诉处理时间是多久？
- **用户体验**：团队关注产品的用户体验吗？日常是怎么做的？
- **项目总结**：再回头看，项目有哪些地方做得好的？哪些地方做得不好的？
- **未来规划**：后面项目的主要规划是什么？

## 综合素质篇（专家）

### 管理

- **团队管理**：聚焦3个核心 定目标/带人/做事，群策群力打胜战
- **管理误区**：团队缺乏方向，上级派活被动执行，全保全揽忙于救火，固守边界，看过程但拿不出结果...
- **制定目标**：制定合理的团队OKR，明确团队职责/充分上下级沟通/明确负责人和时限/结果可量化...
- **团队招聘**：明确团队招聘标准，基础扎实/项目经验/自驱力/聪明度/主动思考找解决方案
- **梯队建设**：团队各T人数比例，鼓励骨干own核心项目，关注后备leader选拔培养和适当授权
- **分工协作**：鼓励owner意识，扁平化管理和敏捷小分队机制，分工明确尽量稳定...
- **跨地域协作**：关注培养本地TL，模块任务尽量闭环，更高效和温度的远程会议
- **员工成长**：工作中树立标杆和实践精进，完善技术分享/导师机制/答辩辅导/团队文档/行业会议...
- **激励机制**：用好激励管理三板斧 绩效/调薪/晋级，公平透明的考核机制，公开及时的认可点赞...
- **氛围建设**：团建活动重在多交流互动，零食/聚餐/生日/周年/运动日...

### 产品（todo）

- **市场调研**：
- **产品设计**：
- **用户调研**：
- **消费心理学**：
- **产品运营**：
- **用户增长**：
- **数据分析**：
- **项目管理**：

### 商业（todo）

- **宏观政策**：
- **金融市场**：
- **行业趋势**：
- **战略管理**：
- **财务管理**：
- **市场营销**：
- **团队管理**：

### 软技能（todo）

- **结构化思维**：
- **问题分析和解决**：
- **高效沟通**：
- **快速学习**：
- **项目管理**：
- **时间管理**：
- **团队协作**：
  
