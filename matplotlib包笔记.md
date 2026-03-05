## **matplotlib包笔记：**

### **1 matplotlib简介：**

* 简介：数据可视化处理的py库



### **2 matplotlib绘图：**

1. **通用设置方法：**

   1. **figure()方法：**

      * 格式：var = plt.figure(figsize=tuple)
      * 作用：创建一个图表，并设置图表

      *(注：参数 **figsize** 为图表尺寸，接收一个元组(x, y)，长100乘x，高100乘y)*

   2. **title()方法：**

      * 格式：var = plt.title(str)
      * 作用：给予图表一个标题

      *(注：添加参数 **color = '颜色Eng'**，可控制标题颜色)*

      *(注：添加参数 **fontsize = num** 可控制标题大小)*

   3. **xlable()方法：**

      * 格式：var = plt.xlable(str)
      * 作用：给x轴添加标签str

   4. **ylable()方法：**

      * 格式：var = plt.ylable(str)
      * 作用：给y轴添加标签str

      *(注：3 4均可添加参数 **fontsize = num** 以控制标签大小)*

   5. **legend()方法：**

      * 格式：var = plt.legend(loc)
      * 作用：控制图例

      *(注：参数 **loc** 要接收一个str，以控制图例出现的位置)*

      *(注：创建图例，需要在plt.plot()参数 **lable = '图例内容'**)*

   6. **grid()方法：**

      * 格式：var = plt.grid(axis)
      * 作用：控制x轴y轴显示横竖线

      *(注：直接传参数 True，则默认x轴y轴均有线)*

      *(注：参数控制哪一轴有线 **axis = 'x'** 和 **axis = 'y'**)*

      *(注：添加参数 **alpha = num**，可控制网格颜色深浅)*

      *(注：添加参数 **linestyle = '--'** 可使实线变成虚线，控制线的“模样”)*

   7. **xticks()方法：**

      * 格式：plt.xticks()
      * 作用：控制x轴的刻度

   8. **yticks()方法：**

      * 格式：plt.yticks()
      * 作用：控制y轴的刻度

      *(注：7 8可添加参数 **fontsize = num**以控制刻度大小)*

      *(注：7 8添加参数 **rotation = num** 以控制刻度逆时针旋转num°，默认水平)*

   9. **ylim()方法：**

      * 格式：plt.ylim(tuple)
      * 作用：控制y轴刻度范围为tuple范围

   10. **text()方法：**

       * 格式：
       * 作用：

   11. **show()方法：**

       * 格式：plt.show()
       * 作用：将创建好的图表展示出来
   
2. **折线图:**
   
   1. plot()方法:**
   
   * 格式：plt.plot(x, y)
   * 作用：绘制一个折线图
     
   
   *(注：添加参数 **lable = '图例内容'**，可创建图例)*
   
   *(注：添加参数 **color = '颜色Eng'** 控制线条的颜色)*
   
   *(注：添加参数 **linestyle = '--'** 控制线的虚实模样)*
   
   *(注：添加参数 **linewidth = num** 控制线的粗细)*
   
   *(注：添加参数 **marker = str** 控制数据节点的样式和大小)*
   
3. **柱状图与条形图：**
   
   1. **bar()方法：**
      * 格式：plt.bar(x, y)
      * 作用：绘制一个x轴y轴的竖直柱状图
   2. **barh()方法：**
      * 格式：plt.barh(x, y)
      * 作用：绘制一个y轴x轴的水平条形图
   
4. **饼图：**
   
   1. **pie()方法：**
   
      * 格式：plt.pie(list1, lables=list2)
      * 作用：按list1内容切分，对应配对给每一块扇形的标识（list2中），绘制一个饼图
   
      *(注：参数 **lables** 不是 **lable** ，以添加图例)*
   
      *(注：从圆的右水平线以逆时针方向开始排列list1)*
   
      *(注：添加参数 **autopct = '%.nf%%'** 第一个 %是转置符号，**'.n'**表示保留n位小数，**f** 表示以float类型显示，**%%** 表示显示符号 %)*
   
      *(注：添加参数 **startangle = num**，使从圆右水平线逆时针旋转num°后开始排 list1)*
   
      *(注：添加参数 **colors = list**，list中含对应数目的颜色的Eng名/颜色二进制号码/颜色十六进制号码的**字符串**，逐一配对给list1中各项)*
   
      *(注：添加参数 **wedgeprops = dict**，使饼图中间挖空，形成一个圆环，**dict**中设置 **'width = 占比num'** 控制挖空大小)*
   
      *(注：添加参数 **pctdistance = num** 控制圆环数字与圆心的距离)*
   
      *(注：添加参数 **explode = list**，list中设置数量与 list1中匹配的num，以控制对应扇形图的突出程度)*
   
      *(注：添加参数 **shadow = True** ，可使整个饼图和突出的扇形的底部都呈现阴影)*
   
5. **散点图：**
   
   1. **scatter()方法：**
   
      * 格式：plt.scatter(x, y)
      * 作用：以x轴y轴创建一个散点图
   
      *(注：添加参数 **alpha = num**，设置散点的透明度)*
   
      *(注：添加参数 **s = num**，控制散点大小)*
   
      
   
   
   
   
   
   
   
   
   
   
   
   