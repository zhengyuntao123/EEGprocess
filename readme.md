# 命名规则

函数命名采用驼峰式命名法，如myNameList

变量名用'_'隔开，如my_name_list

注释写在前一行，如：

```python
#这是一行注释
a=4
```

# 2022.6.21

## 日志

要求以后更新github时，使用md文件模仿此日志,添加到readme.md中

日期为一级标题，修改为二级标题，具体文件名为三级标题

## 文件格式

基本要求：除了医生给的文件可以是中文名以外，其他所有文件均应采用my_name_list形式

文件夹：

![image](https://user-images.githubusercontent.com/65967643/174789896-0ba1ddf4-8589-4f50-8e24-fd9220d1b90b.png)


共11个

img：存放acc,loss图片

model_save：存放模型

others：存放并非我们写的模块，如MIC和高博模型

patient_data：存放医生发来的原始病人数据和刺激参数

SE_parameter：存放处理后的参数

SE_test，SE_train：存放SE_get或SE_get_person处理后的SE切片

SE_test_processed,SE_train_processed：存放预处理后的SE切片

work_file：存放我们写的文件

![image](https://user-images.githubusercontent.com/65967643/174789950-efd2add9-036b-49ff-b12a-89c9f9d4c519.png)

主要包括CNN，不包含刺激参数的CNN，用MIC研究功能连接性的模块，处理excel文件的模块，常规数据处理模块，SE切片获取的模块，按人获取SE切片的模块，SE切片预处理模块

xls：对应EEG_MIC_module输出的xls文件目录

## 修改

### EEG_MIC_module

1、修改了部分路径，但没有测试，发现有很多地方还是绝对路径，且该模块使用的文件并非第四批病人数据

### excel_process

1、修改了路径

### SE_get_person

1、修改了截取训练集SE片段时，发作只截取8s；未发作截取8s，且偏移为0/8/16/24……保证没有重叠

2、截取测试集SE片段时，仍然截取16s

3、修改了路径

### SE_get

1、大致修改了路径，但没有测试是否正确

2、发现这个文件并没有划分训练集和测试集

### SE_pretreatment

1、修改了路径

2、使用的是Gao_Novel_CNN_RNN16_2561630689427.h5 我后面找到了这个模型

### 增加CNN_no_parameter

1、修改了部分参数，以适应8s的训练集和16s的测试集

2、修改了路径

3、去掉了刺激参数的部分，修改了CNN结构

4、仅将训练集的10%作为验证集

5、模型保存时，仅保留至acc_小数点后6位

6、修改了绘图

7、对于图片，模型的命名有待讨论

### CNN

1、改了路径和绘图，但没有测试







