## SEMMI: Multi-party security decision-making scheme for linearfunctions in the internet of medical things
### SEMMI: 医疗物联网中线性函数的多方安全决策方案
##### 关键词：医疗互联网、数据安全、智能决策系统、同态加密

> 在医疗互联网中，一是保证数据安全，二是参与者资源受限，故本文提出一种安全有效的辅助决策方案SEMMI，具体为：参与者将密文发送云端，采用流加密(streamencryption)和同态加密(homomorphic encryption)来传输数据，云端用密文计算，最终将结果与预解密结果进行匹配来验证结果的安全性。
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
















#### **可能可以引用的文章**：
 - Deep Learning Based Pathology Detection for Smart Connected Healthcare [基于深度学习的智能互联医疗病理检测](https://ieeexplore.ieee.org/document/9165267)
 - Computing and Processing on the Edge: Smart Pathology Detection for Connected Healthcare[边缘计算与处理：互联医疗智能病理检测](https://ieeexplore.ieee.org/document/8933558)
 - Data Security and Privacy Protection for Cloud Storage: A Survey [云存储中的数据安全和隐私保护(Survery)](https://ieeexplore.ieee.org/document/9142202)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAzNTg0OTIxNF19
-->