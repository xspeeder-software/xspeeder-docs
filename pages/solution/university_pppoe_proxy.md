### 5.2 高校多运营商联合运营 PPPOE 代拨解决方案

本方案针对高校多运营商联合运营场景，提出基于神行者 BRAS PPPOE代拨解决方案，用来指导解决运营中的实际问题。

#### 5.2.1 运营场景分析

近几年来，高校网络建设越来越完善，运营商投资力度也逐渐加大，由最初的单个运营商变成多家运营商综合运营的模式，运营需求越来越精细化，在逐步升级已有网络基础设施环境的同时，还要考虑到对已有系统的利用，规避盲目重复建设以及各种潜在的风险。

总体来说，具有如下运营诉求：

1. 统一的运营管理：包括无线网络有线网络的统一运营，用户数据的统一管理，以及与数字校园融合，实现统一认证。
2. 学生自主选择权：学生可以自由选择不同的运营商套餐，认证上网时只能匹配网络出口。
3. 在融合各个业务系统时，尽量遵循行业标准，减少不必要的二次开发，避免给已有系统带来影响，方便系统维护。
4. 能有效防止私接代理共享上网，有效识别终端，日志审计。

在以上需求中，允许学生自由选择运营商，认证自动匹配网络出口成为迫切需要解决的问题， 这涉及到运营商，学生，学校的多方权益保障，既要考虑到运营商和学校的运营管理需求，又要保证学生的网络使用自主权，传统的解决方案并没有一个简洁可行的方案，针对此应用场景，神行者BRAS给出了一个有效的解决方案-PPPOE代拨。 


#### 5.2.2 神行者BRAS PPPOE代拨方案

##### 网络拓扑

![](http://static.toughcloud.net/toughsms/tc_20181224103433_6.png)

如图所示，将神行者BRAS作为核心BRAS接入服务器部署在高校内部网络，与各个运营商BRAS进行对接，充当“中间代理”角色，识别接入用户的有效特征，将内部客户端的PPPOE认证转发至对应运营商的BRAS 实现二次认证，而对客户端来说就像直接拨号到运营商一样。

##### PPPOE 直接拨号流程

![](http://static.toughcloud.net/toughsms/tc_20181224103542_7.png)

1. 将神行者BRAS作为主要BRAS设备部署在网络中，所有PPPOE拨号请求首先经过神行者BRAS处理。
2. 神行者BRAS首先进行本地认证，本地认证服务器对用户进行验证根据用户绑定的运营商类型下发不同地址池。
3. 神行者根据本地认证下发的地址池选择不同运营商线路开始PPPOE代理拨号，认证成功后将运营商分配的IP直接分配给用户，建立网络连接，实现用户拨号上网目的。

##### WebPortal接入流程

![](http://static.toughcloud.net/toughsms/tc_20181224103706_8.png)

1. 用户通过无线或有线方式接入学校内网后，被重定向至统一认证Portal门户，用户输入账号密码提交认证。
2. 神行者BRAS首先进行本地认证，本地认证服务器对用户进行验证根据用户绑定的运营商类型下发不同地址池。
3. 神行者根据本地认证下发的地址池选择不同运营商线路开始PPPOE代理拨号，认证成功后将用户内网IP连接和PPPOE代理拨号会话连接建立一对一NAT转换，实现上网目的。

##### DNS智能重定向

- 在PPPOE 直接拨号的模式中，用户被直接分配运营商下发的IP地址，以及运营商的DNS，用户访问网络时对应的网络地址被解析为运营商的线路，用户上网体验和直接拨号是一致的。
- 在WebPortal 接入模式中，用户预先通过DHCP获取得到内网IP地址，当用户认证成功接入网络后，用户的DNS请求可以被神行者BRAS识别并智能重定向到对应的运营商网络，而不会造成DNS解析的网络IP地址和运营商线路不符导致体验不佳的情况 

#### 5.2.3 神行者BRAS PPPOE代拨优势

##### 账号统一管理

无论是学校还是运营商，在启用代拨方案后，各方对用户的统一管理不存在冲突，运营商针对学生手机账号实现运营管理，学校则通过学生的学号来进行管理，PPPOE代拨既保证学生上网要经过学校内部网络认证审计的要求，又同时满足运营商认证审计的要求。另外在保证学生账号不变的前提下，轻松切换运营商网络绑定。

##### 不同运营商与校园内网互联互通

在没有代拨的情况下，学生接入不同的运营商后，由于运营商之间路由之间的各种问题，访问学校内部网络体验不佳，而通过神行者BRAS PPPOE代拨方案，实现了对学生上接入IP地址内部统一分配管理，对学校内部的访问更加流畅。

##### 防代理检测

借助神行者BRAS的防代理检测功能更好的控制内部私接共享行为，保证学校和运营商利益。不同于传统的共享检测机制，神行者BRAS通过DPI深度检测，针对终端的个性特征，以及具备个通用户标识的应用特征，结合数据分析来判断客户端共享行为，执行有效的阻断策略。

##### 实现统一的可视化网络管理

神行者BRAS提供了丰富网络可视化管理功能，可以轻松实现学生上网流量的可视化管理。可以更准确的了解流量带宽占用的动态趋势，监控各类应用的运行情况，可以根据线路，IP，端口，协议，应用以及路由策略等生成各类报表，有效协助网络管理人员准确的掌握当前网络状况。

##### 日志审计，数据分析

借助神行者BRAS的日志审计功能，可以实现日志数据的高效采集、统一管理、集中存储、统计分析。如针对排名、分布、趋势和相似性分析，提供IP 历史、TOP 域名、应用流量流向图、URL 地图、TOP 用户、连接可视化分析和DNS 可视化分析等为代表的分析工具，并可协助高校统一管理网络日志并为安全事件的事后取证提供依据。

##### 性能保障

神行者BRAS单台设备可同时接32K并发代拨用户，上联线路超过60GE的吞吐。


