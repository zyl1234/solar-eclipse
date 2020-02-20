# 简介

本网页是提供一个由事件相机(DAVIS346)于北京时间2019年12月16日13:46至14：42在武汉大学电子信息学院拍摄的日偏食数据，通过事件相机拍摄的数据显示出一些特殊的现象，例如事件点生成图像以特定的频率以水波状向外扩散，这些现象可能与日偏食的天文现象有关，由于术业有专攻，本网页将提供这些数据用来讨论，希望专业相关或有兴趣的朋友可以一起探索这一拍摄现象。



# 介绍

## 1 事件相机

不同于普通相机使用一定时间间隔获取单帧图像，事件相机通过每个独立像素中的电路检测光强的变化而触发事件，组成异步事件。事件相机相对于普通相机具有高时间分辨率、高动态范围和无运动模糊等优势。在本次利用事件相机观测日偏食主要利用了时间相机高动态范围和高时间分辨率的特点，即微小的亮度变化即可产生异步的事件点，并且在短时间内可以观测到亮度的变化，从而获取特殊的观测现象，其中红色的事件点代表该时间亮度变亮，蓝色的事件点代表该像素点亮度变暗。

本次拍摄日偏食使用的是DAVIS346事件相机，它的像素分辨率为346*260，时间分辨率为20us。

DAVIS346相机可以输出普通光学图像、事件点和相机自身惯性测量单元（imu）三个方面信息，事件点为单个像素点亮度变化超过某个阈值产生。本次拍摄为固定相机拍摄日食，故没有相机自身运动，主要利用普通光学图像和事件点两个信息。

## 2 日食

日食是当太阳、月球与地球排成一条直线，月球位于两者之间产生的一种天文现象。日食又分为全食、环食和偏食。由于这次观测地点在位于北半球的中国湖北武汉在12月26日日环食的半影内，不在伪本影范围内，因地球表面非常大，月球投射到地球上的伪本影范围很有限，所以只能看到日偏食的现象。

本次日食在湖北武汉观测时的初亏（日食开始时刻）为12:30:44，食甚（月球遮挡太阳最多时刻）为13:49:39，复原（日食结束时刻）为15:02:06，食分（太阳直径被月球遮挡的比例）为0.295。





# 数据

本次观测日偏食数据为普通光学图像和事件点，事件点是以txt文件储存，对于每个事件点它包含t、x、y、p这个维度的信息分别代表事件点出现的时间、在图像中的x、y坐标和事件点的极性代表该事件点亮度变亮或者变暗。

普通光学相机拍摄的图像如下图所示。

<img src="H:\solar eclipse\solar-eclipse\picture\普光.png" alt="普光" style="zoom:67%;" />

DAVIS346产生的事件点的txt文件格式为：

<img src="C:\Users\11243\AppData\Roaming\Typora\typora-user-images\image-20200218114303542.png" alt="image-20200218114303542" style="zoom:67%;" />

其中数据的第一列为DAVIS346相机拍摄日食时使用的ros系统中的时间戳，其单位为秒，由相邻两行之间的时间差也可看出此相机的时间分辨率很高，第二列和第三列为产生时间的在图像上的坐标，最后一列为事件点的极性，即该事件点亮度变亮或者变暗超过阈值。



#  数据分析

由于事件点的产生是异步的而普通光学图像的产生是在某一个确定的时间点，将很短一段时间内的事件点映射到普通光学图像上可以得到下列图像:

![2](C:\Users\11243\Desktop\2.png)

上述图像从左至右从上至下时间间隔为30ms左右，其中蓝色的点代表该点的亮度下降超过了一定的阈值，由于事件相机在拍摄过程中存在噪声以及自身元器件产生的噪声，如上图所示的事件点杂乱的随机的分布事件点的图像占据了这次拍摄过程的绝大部分时间。

有趣的是在观测的一些时间段内拍摄的数据出现了一些引人深思的现象，如下图所示：



![绘图1](C:\Users\11243\Desktop\绘图1.png)



以上是一组从左至右从上至下隔间时间为30ms左右的图像，这组图像出现的时间大概在13：50左右，由上述图像可以明显地看出与上图事件点杂乱分布的图像不同，第一行的三张图像从左至右图像中事件点数量逐渐增加并且分布由图像中间的太阳迅速往外扩散，而第二行的三张图像则是事件点数量急剧减少并且由事件点遍布整张图像收缩至事件点围绕至图像中心的太阳周围。从连续的时间上看，会出现蓝色的事件点在第一行图像中像水波一样从中心逐渐扩散到整个屏幕。在事件点收缩至图像中间如上述图的第二行第三章图像时，处于太阳中心的事件点出现蓝色和红色两圈事件点，它表示出内圈的红色事件点处亮度增加超过阈值而外侧蓝色圆环处事件点亮度降低超过阈值。



在出现了上述事件点如水波状扩散和收缩之后，DAVIS146相机观测到的图像如下图所示，事件点只出现在太阳光圈内而太阳光圈之外几乎无任何事件点，这代表着太阳光圈内像素点亮度变化发生了变化而太阳光圈外像素点亮度几乎不发生任何变化，这和上述的蓝色事件点杂乱分布在图像中有着很大的不同。



![3](C:\Users\11243\Desktop\3.png)





## 周期分析

事件点只出现在太阳光圈内之后事件点会再次逐渐向外扩散，以蓝色事件点占满整个图像为周期的起始点，如图2所示蓝色事件点像水波一样沾满整个屏幕，这种现象将会反复多次出现。

![4](C:\Users\11243\Desktop\4.png)

如上图所示，蓝色事件点如水波状向外扩散的现象周期性出现，在时间13:50至13:56左右的周期性事件点占满图像如上图的第一行所示，而在13:56至14:01左右出现的周期性事件点占满屏幕为第二行所示，由第二行贼可以更清楚得看出蓝色事件点如水波状向外扩散的趋势。

每次事件点如水波状向外扩散的周期不完全相同，可能由于事件点是个异步连续的过程，将其映射到图像上时会损失一定的时间精度，上述水波状扩散的周期起初大约为1.1s左右，周期上则到2.7s左右。





# 数据下载

数据链接 [百度网盘，提取码](https://pan.baidu.com/s/1CCupyyssmtbrGUzECK-8WQ)

