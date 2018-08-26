# Traffic1
Internet Traffic Analysis
#database
kddCup99.data_10_percent_corrected
kddCup99.data.corrected
#第一版本
##handle2.py
###主要功能
将kdd99的10%的数据集里面的非数值的特征（协议类型、网络服务类型、网络连接状态、攻击类型）转换成数值型的
###输出
在终端上输出:"status:" + 协议类型 + 服务类型 + 连接状态 + 攻击类型
注意：这里的类型和状态都已转换成数值
##main_cnn.py
###主要功能
将handle2.py修改出来的cvs（这里不转换成csv是因为写入csv会自动转换成科学技术法，处理起来不方便）通过一个conv+max——pool和两个全连接层
###输出
在终端输出：“step,prediction,label,test_accuracy,train_accuracy”
##训练结果如下
[图片1]
#第二版本
在版本1的基础上加入了数据归一化处理
其他地方都一样就不累赘了，因此下面只讲handle2.py修改的思路
##归一化
1/将数据集转置形成矩阵
2/将矩阵按照一行一行的最大值最小值的归一方法进行归一
3/将矩阵转回来
4/一行一行写入cvs文件中（生成的文件有：new.cvs和new_10_percent.cvs）
##训练结果如下
[图片2]
可以看出准确率特别的低，想到可能是将科学计数法转成float的时候精度被省略了，所以每个数据的特征几乎相同，无法辨别出label，于是做了第三版本的修改
#第三版本
主要是针对版本2的问题
改成了使用pandas模块来读取数据集将其转换成矩阵，这样就解决了精度确实的问题
##训练结果如下
[图片3]
训练准确率只比第一版本小了0.1%