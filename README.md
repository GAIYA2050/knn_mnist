# 使用Bagging集成的mnist数据集上的knn分类器

- 这是一个Bagging集成分类器。

- 被集成的基本分类器选用knn。

- 数据集使用mnist手写数字识别。

- 使用PyQt5写了个简单的过程展示界面。

- 能够验证自己手写的数字。

## 快速开始

**1.启动主窗口。**

运行项目根目录下`gui`包下`main.py`文件。

此时，有三种功能可供选择：

- 全部验证

- 随机验证

- 手写验证

下面做详细介绍。

**2.全部验证**

mnist数据集在项目根目录下`dataset`目录下。

没有使用交叉验证的方式，这里用的是数据集已经划分好的train和t10k作为训练集和开发集。

全部验证的功能：

点击按钮后，会对开发集中所有数据进行验证，并统计各knn分类器和bagging集成分类器的准确率。

请注意，因为knn实际上可以说是没有训练过程的，计算时间复杂较高，全部验证会花费很多时间（使用kd-tree可以大幅度提高knn的验证速度，但这里我没有使用）。

结果示例：

![全部验证](https://raw.githubusercontent.com/AaronJny/knn_mnist/master/sample/sample_1.png)


**3.随机验证**

数据集分布与2相同。

随机验证功能：

指定一个数字m，从开发集中，随机抽取m个样例用于测试，GUI会展示计算过程，并统计各knn分类器和bagging集成分类器的准确率。

注意，当给定数字为10000或者-1时，该功能近似于全部验证功能(多了展示计算过程的部分)。

结果示例：

![随机验证](https://raw.githubusercontent.com/AaronJny/knn_mnist/master/sample/sample_2.png)



**4.手写验证**

手写一个数字，截取图片，交给分类器识别。

程序会自动将图片规整为28*28尺寸，并转化为灰度，再对灰度矩阵数值进行调整，尽量使其接近原数据集的分布。

项目根目录下hand_write文件夹内，保存有几张我自己手写、截取的图片，可以进行测试。

注意：

- 截取的图片请以`标签.png`或`标签-n.png`命名，其中n为图片编号。例如，一张写有6的图片，`6.png`、`6-1.png`等都是合法的。

- 截取图片时请尽量使图像处于白板中央并适当留白。

- 数据集来自国外，因手写风格不同，图片获取标准不一致（我们手写的数字与原数据集不属于同一分布），手写的图片识别准确率可能不高。


结果示例1：

![手写验证1](https://raw.githubusercontent.com/AaronJny/knn_mnist/master/sample/sample_3.png)

结果示例2：

![手写验证2](https://raw.githubusercontent.com/AaronJny/knn_mnist/master/sample/sample_4.png)