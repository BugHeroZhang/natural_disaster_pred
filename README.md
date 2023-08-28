## Predicting Landslides using CNNs and Sentinel-2 Data
## 通过卷积神经网络和来自Sentinel-2卫星的图像预测滑坡

此项目由
Max
Yichabod创建并维护至9.26.2021，由DaixiaDayo

### Quick outline of files:
### 快速入手

***请使用python3.7.x、TensorFlow1.15.x版本执行程式码***

Landslide_detection_main.py trains the network and does most of the other work, uses create_dataset.py to create a dataset out of images in a folder called 'earth_engine_good'. 

Landslide_detection_main.py训练神经网络并包揽大多数工作，其使用dataset.py创建一个数据集，数据集来自earth_engine_good中的图像，档案夹树状结构如下：

    earth_engine_good/
    ├── event_name_month_day_year/  #滑坡发生时间
    │   ├── yearmonthdayThhmmss/    #发生前的卫星图像
    │   │   ├── image1.tif
    │   │   ├── image2.tif
    │   │   └── ...
    │   ├── yearmonthdayThhmmss/    #发生后的图像
    │   │   ├── image1.tif
    │   │   ├── image2.tif
    │   │   └── ...
    │   └── ...
    ├── event_name_month_day_year/  #同上
    │   ├── yearmonthdayThhmmss/
    │   │   ├── image1.tif
    │   │   ├── image2.tif
    │   │   └── ...
    │   ├── yearmonthdayThhmmss/
    │   │   ├── image1.tif
    │   │   ├── image2.tif
    │   │   └── ...
    │   └── ...
    └── ...
***请注意，event和name是两个不同的变量，这一点与原始程式码有别，这两个变量仅用作区分，没有实际用途***

Accuracy_plotter.py creates a plot of accuracies during training based on the text files in results folder(copy pasted from what the python file prints).

Accuracy_plotter.py用于绘制训练和验证精度随训练周期变化的折线图，数据来自Landslide_detection_main.py所输出的控制台数据，在Results档案夹中已经给出样例

image_download_script.js can be pasted directly into the https://code.earthengine.google.com console and you just have to enter the coordinates of the earthquake into cropping_coordinates.py to get the bounding boxes.

image_download_script.js可以直接复制到https://code.earthengine.google.com ***（未经测试希望大佬多多提出issue！！）*** 将地震坐标输入cropping_coordinates.py中可以计算出周围10km的地理坐标，供auto_download.py使用

auto_download.py是从Google Earth Engine下载指定时间、坐标的地图数据
，使用时确保你拥有Google Earth Engine的访问权，中国大陆用户或许需要全局代理以登入Google Account

以下为许可证信息

MIT License

Copyright (c) [2019] [Max Langenkamp, Tuomas Oikarinen]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
