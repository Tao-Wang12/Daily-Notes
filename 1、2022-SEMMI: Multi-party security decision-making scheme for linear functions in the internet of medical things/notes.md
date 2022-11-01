## SEMMI: Multi-party security decision-making scheme for linearfunctions in the internet of medical things

### SEMMI: 医疗物联网中线性函数的多方安全决策方案

##### 关键词：医疗互联网、数据安全、智能决策系统、同态加密

> 在医疗互联网中，一是保证数据安全，二是参与者资源受限，故本文提出一种安全有效的辅助决策方案SEMMI，具体为：参与者将密文发送云端，采用流加密(streamencryption)和同态加密(homomorphic encryption)来传输数据，云端用密文计算，最终将结果与预解密结果进行匹配来验证结果的安全性。
> 
### 一、introduction

***起因***：用于数据采集的设备资源有限容易攻击、机器学习和神经网络算法在训练的过程中可能会泄露数据

***相关工作***：为了解决上述问题，Mohassel等人首先在2017年提出了第一个用于机器学习的隐私保护计算协议，采用非竞争的方式将数据传送到两台服务器，使用安全两方计算来联合训练各种机器学习模型；Hasan等人设计一种轻量级加密算法解决设备资源有限问题；使用KNN分类算法将计算外包给云服务器；高灵活性的多密钥加密方案

***问题与挑战***：
![医疗物联网框架图](https://raw.githubusercontent.com/Tao-Wang12/Daily-Notes/main/images/8lmyaxJBRXAWdX8f.png)
 1. 大量数据收集难
 2. 在数据收集、传输、处理和存储过程中容易受到攻击
 3. 数据中存在用户个人隐私容易泄露
 
***本文贡献***：提出一种安全高效的多方联合智能决策方案，可以有效处理机器学习中的线性函数问题。
> 1、使用同态加密保证数据传输和计算都是以密文形式
> 2、针对该方案部署灵活性问题，利用多密钥同态设计了一种适用于密文计算的医疗计算模型，但受同态加密算法效率的限制
> 3、理论和实验评估了设计的方案，对浮点数采用取整操作减轻对训练结果的影响

### 二、Preliminary

> 符号：$\mathbb{Z}$表示整数，$\mathbb{N}$表示自然数，$a \stackrel{R}{\leftarrow} \chi$表示随机从$\chi$中选取随机数$a$，$b \stackrel{U}{\leftarrow} \mathbb{Z}$表示从整数集合$\mathbb{Z}$中只选择$b$，大写和粗体的字母代表矩阵，小写和加粗的代表向量。

**同态加密的简短介绍**：(KeyGen, Enc, Dec, Eval)

 -  $\operatorname{KeyGen}\left(1^{\lambda}\right) \rightarrow(sk, pk, evk)$：给定初始化参数，生成私钥$sk$，公钥$pk$，以及公共传输密钥$evk$；
 - $\operatorname{Enc}(m, p k) \rightarrow(c)$：用公钥$pk$加密明文消息$m$，得到密文$c$；
 - $\operatorname{Dec}(c, s k) \rightarrow(m)$：用给定私钥$sk$解密密文，得到明文$m$；
 - $\operatorname{Eval}\left(f, c_{1}, c_{2}, \cdots, c_{x}\right) \rightarrow\left(c_{e v a l}\right)$：给定代数运算$f$和密文$c_{1}, c_{2}, \cdots, c_{x}$得到密文计算结果$c_{e v a l}$
 
 **GSW同态加密方案**：
 ![GSW同态加密方案的简单介绍](https://raw.githubusercontent.com/Tao-Wang12/Daily-Notes/main/images/lw9sGQ50keQ8H8I8.png)

### 三、Scheme model and design goal

**系统模型**：
![系统模型](https://raw.githubusercontent.com/Tao-Wang12/Daily-Notes/main/images/pFNDANVqEUH0RM4c.png)

 *可分为四步*：
 1. 使用流加密在传感器和用户之间进行数据加密传输；
 2. 用户从可信机构获取公钥信息，然后将数据加密并上传到云端；
 3. 查询用户向受信任的机构请求服务。可信机构向查询用户提供公钥。查询用户使用公钥对数据进行加密，然后将加密后的数据发送到云端进行处理。云将处理后的结果传输给可信机构；
 4. 可信组织解密并将计算结果发送给查询组织，查询组织对结果进行统计，得到最终的决策结果。
 
 **威胁模型**：

敌手$\mathscr{A}$可能通过监控网络通信链路获取各方加密后的数据，可能会在云上发起攻击来获取用户存储在云上的加密数据，可能会联合一些参与者通过密文推导出用户的明文信息。

### 四、Proposed scheme

![方案各阶段执行顺序](https://raw.githubusercontent.com/Tao-Wang12/Daily-Notes/main/images/H8ONeysGbczeHJaL.png)

~~具体里面数据的传输、加解密、公私钥的运用略看~~

### 五、Analysis and evaluation

**安全性分析**：

 1. 加解密安全性分析
 - chaotic的系统和流密码保证了传感器和用户之间的安全通信
 - 同态加密方案是安全的，满足INA-CPA安全
  2. 系统安全性分析
 - 该方案的假设是，云值得信赖但是好奇的，并且敌手不会破坏数据机密性或用户隐私
 - 在提出的KNN分类算法中，假设敌手控制了一些用户节点，系统仍然可以保证其他用户数据的机密性，不会瘫痪

**实验和评估**：

 - 比较了加密方案每个阶段的时间消耗
 - 在加密消耗时间与密文数据量大小上与Paillier方案对比，时间上有明显优势
 - 密钥存储空间与参数$q$的设置成正比，也就是说可以尽可能的选择小的参数$q$来降低通信和存储成本
 - 先在5个数据集上进行实验，测试准确性，然后使用UCI的乳腺癌数据集，比较每个部分的时间，发现绝大部分时间花在云的计算上，达到了预设的目标，最后与相关方案比较，体现本方案优势

### 六、总结

在智能医疗设备场景中的一个安全高效智能的决策方案，采用GSW同态加密算法、KNN分类算法在不同数据集上进行测试训练(25%测试，75%训练)，结果与其他算法和方案相比，有一定的优势，最后构建了一个在联邦学习场景下的算法。

#### **可能可以引用的文章**：
 - Deep Learning Based Pathology Detection for Smart Connected Healthcare [基于深度学习的智能互联医疗病理检测](https://ieeexplore.ieee.org/document/9165267)
 - Computing and Processing on the Edge: Smart Pathology Detection for Connected Healthcare[边缘计算与处理：互联医疗智能病理检测](https://ieeexplore.ieee.org/document/8933558)
 - Data Security and Privacy Protection for Cloud Storage: A Survey [云存储中的数据安全和隐私保护(Survery)](https://ieeexplore.ieee.org/document/9142202)

#### **数据集网站**：
[UCI机器学习数据集](https://archive.ics.uci.edu/ml/datasets.php)
[kaggle在线查询数据集](https://www.kaggle.com/datasets)

### 个人小结

 1. 采用同态加密，但作者把大部分计算放到云上，很大程度上减小了本地计算开销【可以考虑将计算开销大的步骤交给云】
 2. 方案的模型比较简单，但作者花了较大的篇幅介绍其组成和详细步骤【可以学习这种行文方法】
 3. 他的算法和代码都是现成或者稍作修改的，数据集方面文中说了要用模拟数据集和真实数据集进行实验，但好像都是模拟的数据集【可学】
 4. 实验部分，大部分是自我方案内部的比较，后续是数据集的测试与训练，再后是与其他方案的粗略比较【看起来实验很丰富，但与其他方案比较的比较粗糙，可以学习】

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQyNTczMDkyNiwxMDM1ODQ5MjE0XX0=
-->