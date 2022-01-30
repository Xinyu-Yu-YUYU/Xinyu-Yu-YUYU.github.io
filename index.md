# ·Preface
***注：适用于有一定C/C++基础***</br>
&ensp;&ensp;&ensp;&ensp;Arduino是一个基于硬件（Arduino Board）和软件（Arduino IDE）的开源电子平台。Arduino Board负责读取输入－传感器信号、开关的闭合或者是网络上的信息－将其转化为输出－驱动电机、点亮LED或者是在网上发布某些信息。操作者通过向主板上的微控制器发送一系列指令告诉开发板需要执行的操作。</br>
  &ensp;&ensp;&ensp;&ensp;其实现在网络上Arduino的学习资源已经可以满足大部分人的需要 ，技术相当成熟，个人比较推荐Arduino官方网站[https://www.arduino.cc](https://www.arduino.cc)和太极创客[http://www.taichi-maker.com](http://www.taichi-maker.com)（B站视频[https://b23.tv/tsy5Mm1](https://b23.tv/tsy5Mm1)）。那么可能就会有人问，这样的blog是否还有存在的价值。</br>
  &ensp;&ensp;&ensp;&ensp;不知道大家在查找资料的时候是否会遇上和我一样的情况：打开了N多个窗口，“苦心孤诣”，终于找到了解决这个bug的正确方案。就像拼图，这边缺了一块，那边又多出来一块，怎么也找不到完全契合的另一半。读者，来自不同年龄段，不同学历，需求总会不同。因此，我觉得，世间人物千千万，总有人会遇上和你一样的bug，会需要你的独家idea｡同样的，每个人的知识体系形成过程是不一样的，无论是学什么，我们总会无可避免地走一些弯路，当回过头来看，心路历程就显得尤其珍贵，我们会调整原有的学习思路，去整理出更系统更有效的方法。所以，我相信，即使很多人都写过这方面的内容，但用心创造的东西总是有价值的。</br>
 &ensp;&ensp;&ensp;&ensp; 当我在网络上查找教程或是资料的时候，我发现，很难有让人完全满意的。除了本身存在的问题，原因归结于以下几点：1、有些教程会略过一些我认为有必要去阐述的内容，这就使不少人在看完后仍处于一种一知半解的状态。2、讲述语言过于累赘或是深奥，一些很简单的问题偏偏要用晦涩难懂的语言去解释。3､排版问题，美观简洁的排版往往会加分不少，我相信没有人愿意去看代码和文字杂糅、格式无逻辑可言的文章。肝blog确实是一个费时间和心力的活儿，每个花了心思的博主都值得路人的点赞。当然，在写作过程中我也尽量避免这些问题。</br>
&ensp;&ensp;&ensp;&ensp;我的初衷是从一个学习者的角度去做一个笔记性质的blog，语言文字功底并不算好的我会尽量使我的文字简单易懂。希望能够为读者们提供一些帮助，若有不正确或者有待改进的地方，还请批评指正。</br>
# ·Arduino Board
&ensp;&ensp;&ensp;&ensp;Arduino UNO是相对来说来说最简单最易上手的开发板，也是应用最广泛参考资料最多，适合初学者入门，因此在这里我们只对Arduino UNO进行研究。如下图所示：
![Arduino UNO](https://img-blog.csdnimg.cn/a4b20f8d6a7d4333896ad9496a17bb72.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBALS3mkbjpsbznmoTpsbwtLQ==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
## ·基本硬件知识
&ensp;&ensp;&ensp;&ensp;Arduino UNO是一款基于**微控制器**[ATmega328P](https://baike.baidu.com/item/ATMEGA328P-AU)的单片机开发板。共有14个**数字输入/输出引脚**（这些引脚中有6个引脚可以作为PWM输出引脚），6个**模拟输入引脚**，16 MHz石英晶振，USB接口，电源接口，支持在线串行编程以及复位按键。用户只需要将开发板与电脑通过USB接口连接就可以使用。
## ·主要技术参数
微控制器 | ATmega328P
-------------|--------------
工作电压|5伏特
输入电压（推荐）|7~12伏特
输入电压（极限）|6~20伏特
数字输入输出引脚|14个
PWM引脚|6个
模拟输入引脚|6个
输入/输出引脚直流电流|20mA
3.3V引脚电流|50mA
闪存（Flash Memory）|32KB，其中由0.5KB用于系统导引
静态存储器（SRAM）|2KB
EEPROM|1KB
内置LED引脚|13
长|68.6mm
宽|53.4mm
重|25克
时钟频率|16MHz
注：EEPRON(electrically erasable programmable read-only memory)带电可擦可编程只读存储器

## ·引脚
![引脚说明图](https://img-blog.csdnimg.cn/2d5eff771b2a474eb4947688aba946bc.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBALS3mkbjpsbznmoTpsbwtLQ==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
### Arduino Uno引脚分配 - 电源

●   Arduino Uno开发板可以使用三种方式供电：
 1. 直流电源插孔 -可以使用电源插孔为Arduino开发板供电。电源插孔通常连接到一个适配器。开发板的供电范围可以是5-20V，但一般建议将其保持在7-12V之间。高于12V时，稳压芯片可能会过热，低于7V可能会供电不足。
 2.  **VIN引脚**（Input voltage） - 该引脚用于使用外部电源为Arduino Uno开发板供电。电压应控制在上述提到的范围内。
 3. USB电缆 - 连接到计算机时，提供500mA/5V电压。

●    **5v**和**3.3v**

提供稳压的5V和3.3v，向外部组件供电。

●    **GND**（接地）

共有5个GND引脚（除了明确标识的3个外还有两个分别在DC接口和USB转串口芯片处），它们都是互连的。

GND引脚用于闭合电路回路，并在整个电路中提供一个公共逻辑参考电平。务必确保所有的GND（Arduino、外设和组件）相互连接并且有共同点。

●    **RESET** - 复位Arduino开发板。

●    **IOREF** - 该引脚是输入/输出参考。它提供了微控制器工作的参考电压
### Arduino Uno引脚分配 - 模拟输入

Arduino Uno有6个模拟引脚，它们作为ADC（模数转换器）使用。

这些引脚用作模拟输入，但**也可用作数字输入或数字输出。**

**模数转换**

ADC是用于将模拟信号转换为数字信号的电子电路。模拟信号的这种数字表示允许处理器（其是数字设备）测量模拟信号并在其操作中使用它。

**Arduino引脚A0-A5**能够读取模拟电压。在Arduino上，ADC具有10位分辨率，这意味着它可以通过1,024个数字电平表示模拟电压。 ADC将电压转换成微处理器可以理解的位。
### Arduino Uno引脚分配 - 数字引脚

Arduino Uno的**引脚0-13**用作数字输入/输出引脚。其中，**引脚13**连接到板载的LED指示灯；**引脚3、5、6、9、10、11**具有[PWM](https://baike.baidu.com/item/PWM%E6%8A%80%E6%9C%AF)功能。（注意： 每个引脚可提供/接收最高40 mA的电流。但推荐的电流是20毫安。所有引脚提供的绝对最大电流为200mA。）
     &ensp;&ensp;&ensp;&ensp;在Arduino中，支持PWM的引脚产生约500Hz的恒定频率，而占空比根据用户设置的参数而变化。
     
  &ensp;&ensp;&ensp;&ensp;数字是一种表示1位电压的方式：0或1。Arduino上的数字引脚是根据用户需求设计为输入或输出的引脚。数字引脚可以打开或关闭。开启时，它们处于5V的高电平状态，当关闭时，它们处于0V的低电平状态。
&ensp;&ensp;&ensp;&ensp;在Arduino上，当数字引脚配置为输出时，它们设置为0或5V。
&ensp;&ensp;&ensp;&ensp;当数字引脚配置为输入时，电压由外部设备提供。该电压可以在0-5V之间变化，并转换成数字表示（0或1）。为了确定这一点，有2个阈值：低于0.8v视为0。高于2.0v视为1。
**注：这里的输入输出是针对与开发板而言**
&ensp;&ensp;&ensp;&ensp;将组件连接到数字引脚时，确保逻辑电平匹配。如果电压在阈值之间，则返回值将不确定
### Arduino Uno引脚定义 - ICSP插头

ICSP表示在线串行编程。该名称源自在系统编程（ISP）。 Arduino相关的制造商，如Atmel，开发了自己的在线串行编程插头。这些引脚使用户能够编程Arduino开发板上的固件。 Arduino开发板上有6个ICSP引脚，可通过编程电缆连接到编程器设备。
