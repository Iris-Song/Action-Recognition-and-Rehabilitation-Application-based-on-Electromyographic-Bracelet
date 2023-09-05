# Action-Recognition-and-Rehabilitation-Application-based-on-Electromyographic-Bracelet
my graduation project in Tongji University

## abstract
In clinical practice and research related to electromyographic (EMG) signals, whether information with practical significance can be effectively extracted from the collected EMG signals, and then the perception and prediction of muscle status, human body movements, and case rehabilitation can be made correctly, rely on method selection and design of feature extraction. By collecting and analyzing surface EMG signals of patients when they complete specified paradigm movements, the patient's motor function rehabilitation status can be evaluated, thereby helping rehabilitation physicians to formulate more appropriate personalized rehabilitation training programs.

In this paper, based on the multi-lead surface EMG (sEMG) signal collected by the electromyographic bracelet, its features are extracted, and the pattern classification method is used to identify the human hand action muscle mode corresponding to the signal feature, and then realize the human action recognition function. On the basis of previous laboratory system, I design and improve the surface electromyography-based rehabilitation training and state evaluation system to make it more practical. The system is implemented based on B/S architecture, which can select a variety of training paradigms for a specific patient. The system can collect, analyze and store multi-lead surface electromyographic data synchronously, and obtain and visualize time-frequency features related to specific actions. The system evaluates and scores the patient's movements based on the EMG data. The system can also be connected with mechanical gloves. The system can collect the EMG signals of a specific patient under a specific paradigm, and based on the random forest algorithm, train the scoring model for a specific patient in real time. In addition, when the movement score is lower than the set threshold, the gloves will drive the patient's hand for rehabilitation training.

**Key words:** machine learning, pattern recognition, rehabilitation treatment

## thesis
[Chinese vesion](https://github.com/Iris-Song/Action-Recognition-and-Rehabilitation-Application-based-on-Electromyographic-Bracelet/blob/main/thesis.pdf)

## system structure
The whole system uses Chinese.
### frontend
/templates folder

+ page1 实验列表
+ page2 模拟流程
+ page2_copy 新建实验
+ page3 查看历史实验
+ signin/signup 登录注册

### backend
+ views.py 主体部分实现
  + username 全局变量，设定当前用户【可以自己改成cookie存储】
  + get_visual_data 新建实验后按固定频率调用，对输入信号进行打分，未选择的动作模式默认得分为0
  + get_visualization_data 模拟流程时按固定频率调用，npy文件进行分析
  + music2 读取肌电手环数据
  + initial_sys 连接串口
+ train_module.py 模型部分实现
  + add_basic_dataset 添加基准训练数据，必选
  + add_select_dataset 添加选择的数据，只在用户的文件目录下查找
  + train_module lightgbm模型进行训练


### database
SQLite
https://blog.csdn.net/Gu_amber/article/details/122531578

#### 注册数据表
+ Patient 存储用户信息，目前是明文存储
+ experiment

#### 新建实验后生成npy文件
+ emgdata 文件夹下
命名方式 'experiment表中的index_id'_display

#### 数据集存储：

emgdata/basic_csv 存储基准训练集

emgdata/username 存储某一用户的标准数据集

## [Video demo](https://youtu.be/sB43WXYmbxg)
duration:  2:39 

quick introduction of hardware and EMG system

## source code
Inherit code from Brain Cognition and Computing Lab of Tongji University. All rights belong to Brain Cognition and Computing Lab.
