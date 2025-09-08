# 2025 AIπ暑期招新第一轮测试说明

当你成功打开这个*.md文档时，证明你迈出了伟大的一小步，毕竟，你学到了如何打开一个Markdown文档。

Markdown文档有很多优秀的性质，我们推荐你在后续的记录和提交中使用这种格式。同时，我们也推荐一个好用的Markdown编辑器：[Typora](https://typora.io/)

我们希望这个文档可以让你对测试有初步的了解和准备。以下是有关第一轮测试的说明内容，请你仔细阅读，勤加准备。

## 考察方法

第一轮测试共有**5**道题目, 每道题目均有数个小问，一些需要你编程完成，一些需要你进行学习、推导、分析，并记录过程和答案，我们会在面试时进行提问。

记录时，我们推荐使用jupyter notebook，它可以保存你的代码运行结果，也支持markdown，Typora + LaTeX也是一个很好的组合。当然，如果你认为时间有限，也可以提交其他形式的文档，我们不会因此降低对你的评价，但希望你最终提交的结果清晰易辨，不至于带来交流的不便。

题目主干会给出与题目密切相关，且充分的学习材料和背景介绍，供大家学习参考。

## 考察重点

机器学习模型是各类学习理论、网络的基础；对机器学习理论有充分的了解能为未来的学习和研究打下坚实的理论基础。但学习机器学习理论却容易停留纸面，似懂非懂，到最后往往不知所以然。

同时，数据是支撑各类学习算法的核心，学会处理数据、认识数据，是打开AI大门的钥匙。

因此在第一轮考察中，我们会着重考察对经典机器学习模型的学习、理解、复现，以及一些基本的数据处理能力。

我们不禁止大家使用ai coding，因为ai时代利用好工具才能最大程度的提升效率，但我们希望ai只是**辅助**你完成coding，而不是替你完成所有的coding，总之我们希望你能从这些题目中学到一些基本的知识

## 预估测试时间表


| 时间节点 | 日程             | 说明                              |
| ---------- | ------------------ | ----------------------------------- |
| 9月8日 | 一轮测试开始     | 结束报名，公布赛题                |
| ~ | 测试答疑   | 线上进行答疑，交流                |
| 9月15日 | 一轮测试截止提交 | 没错，这就是DDL，具体时间另行通知 |

## 所需知识与参考资料

### GITHUB：

GITHUB会教会你很多东西，搞定教育认证很有用。

------

### **数学知识：**

- 微积分的基本知识，如多元函数求导，多元函数极值问题，凸函数的性质，泰勒公式等；
- 线性代数的基本知识，如什么是矩阵，矩阵的基本运算规则；矩阵转置和逆；矩阵的求导等；
- 概率论的基本知识，如什么是概率分布；什么是概率密度函数；贝叶斯公式是什么；什么是矩估计和极大似然估计。

  **供你参考：**

  华东师范大学数学系.数学分析（上册）（第三版）[M].北京:高等教育出版社,2001:335

  华中科技大学数学与统计学院编. 线性代数 第4版 [M]. 北京：高等教育出版社, 2019.01.

  陈家鼎 郑忠国.概率与统计（第二版）（概率论分册）[M].北京.北京大学出版社,2017:312

---

### **模型知识：**

- 对于机器学习算法的各种评价指标, 如F1 score, 准确率等;
- 机器学习的经典模型，了解其假设、公式推导、适用条件、效果、优缺点等，试着编写一些代码；
- 基本的数据处理方法，在利用上述编程知识的前提下，学习文本清洗，文本停用词的使用，token的概念，了解一些常见图像数据的加载，csv文件的加载等；
- 一些数据可能存在部分缺失，学习对这些“部分”缺失数据的处理方法。

  **供你参考：**

  周志华.机器学习[M].北京:清华大学出版社,2016:425（西瓜书）

  李航.统计学习方法[M].北京:清华大学出版社,2019.5.1

  深度学习（花书）

  [南瓜书Pumpkin Book](https://datawhalechina.github.io/pumpkin-book/#/)

  [Cornell CS4780 Lecture Notes](http://www.cs.cornell.edu/courses/cs4780/2018fa/page18/)

  [Andrew.Ng机器学习入门课程](https://www.bilibili.com/video/BV164411b7dx?from=search&seid=14373086289408297854)

  [斯坦福大学CS229: Machine Learning](https://www.bilibili.com/video/BV19e411W7ga?from=search&seid=641142794885784423)

---

### **编程知识：**

- 正确安装Python（尽量使用Python3以上版本），并配置一个良好的开发界面，如使用VSCode作为文本编辑器，并学习使用内部的功能进行代码调试，或者使用PyCharm等IDE作为开发平台；VSCode是一个免费的文本编辑器，PyCharm Community Edition是一个免费的IDE。同时也推荐大家尝试Cursor, Qwen-code, Gemini-CLI等IDE, 他们会极大程度提升你的coding 效率
- Python的语法，包括但不限于：了解list, tuple, dict等内建的类，及其使用方法；如何定义函数；条件语句和循环语句的使用等；
- Python对第三方库的调用，即import语句的使用；
- 常见Python库的使用，如os, math, sys, re, time等；
- 学习在终端下使用pip指令安装第三方库，学习常用的第三方库，如本测试中可能用到的NumPy,Pandas, Matplotlib；
- （可选）学习安装Anaconda并利用其对开发环境即第三方库进行管理。

  #### 供你参考

  **Python学习**
  (入门) Eric Matthes.Python编程 : 从入门到实践 [M].北京:人民邮电出版社,2016.7
  (进阶) Luciano Ramalho.流畅的Python [M].北京:人民邮电出版社,2017.5
  [廖雪峰官方Python教程](https://www.liaoxuefeng.com/wiki/1016959663602400)

  **编辑器**

  [VSCode官网](https://code.visualstudio.com/)
  [VSCode配置](https://code.visualstudio.com/docs/python/python-tutorial)
  [PyCharm使用](https://www.runoob.com/w3cnote/pycharm-windows-install.html)

  **NumPy**

  [官方文档](https://numpy.org)
  [入门教程(1)](https://cs231n.github.io/python-numpy-tutorial/)

  [入门教程(2)](https://www.runoob.com/numpy/numpy-tutorial.html)

  **Anaconda**

  [官方网站](https://www.anaconda.com/)
  [安装教程](https://blog.csdn.net/ITLearnHall/article/details/81708148?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162227311016780262549433%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=162227311016780262549433&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-81708148.pc_search_result_control_group&utm_term=anocanda&spm=1018.2226.3001.4187)

  **Pandas**

  （美）麦金尼（McKinney W.）著；唐学韬译. 利用Python进行数据分析 [M]. 北京：机械工业出版社, 2016.01.

  [官方网站](https://pandas.pydata.org/)

  [官网教程](https://pandas.pydata.org/docs/getting_started/intro_tutorials/)

  [极简教程](https://www.runoob.com/pandas/pandas-tutorial.html)

  **Matplotlib**

  [官方网站](https://matplotlib.org/)

  [官网教程](https://matplotlib.org/stable/tutorials/index.html)

---

### **文档编写：**

- Markdown的基础语法

- Typora的安装与使用，建议你开启实时内联公式显示；

- LaTeX在Typora环境下的使用，LaTeX语法。

  **供你参考：**

  [Markdown教程](https://www.runoob.com/markdown/md-tutorial.html)

  [Typora官网](https://typora.io/)

  [Typora的使用](https://sspai.com/post/54912)

  [LaTeX在Typora中的使用](https://blog.csdn.net/happyday_d/article/details/83715440)

------

### LLM：

生成式人工智能的正确使用，会为学习带来巨大的便利

**注**：以上提供的所有资料仅供参考，你也可以使用你强大的信息检索能力，找到更适合你自己学力水平的参考资料。
