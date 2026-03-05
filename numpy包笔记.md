## Numpy包笔记：

### **1 numpy简介：**

* 简介：py中用于科学计算的基础包



### **2 ndarry类型：**

#### **（1）性质：**

1. 多维性
2. 同质性（索引元素类型一致）
3. 高效性（连续空间存储，向量化运算）

*(注：创建ndarry对象时若元素类型不同，则“低级”类型会强转为“高级”类型，如int 1强转为’1‘)*



#### **（2）ndarry属性：**

1. **shape：**
   * 作用：数组形状（行 列 尺寸等）
2. **ndim：**
   * 作用：维度数量
3. **size：**
   * 作用：元素总个数
4. **dtype：**
   * 作用：元素类型
5. **T:**
   * 作用：转置（行变列，列变行）
6. **itemsize：**
   * 作用：单个元素占用的内存字节数
7. **nbytes：**
   * 作用：数组总内存占用字节数（相当于：size*itemsize）
8. **flag：**
   * 作用：内存存储方式（如是否连续）



#### **（3）ndarry创建：**

1. **基础创建：**

   1. **array()方法：**

      * 格式： var = np.array(list)

      *(注：array()可传入参数：dtype = 类型 来强制转换元素类型)*

   2. **copy()方法：**

      * 格式：var = np.array(ndarry对象)

      *(注：copy()创建的数组完全继承被复制的对象，创建后与被复制对象独立)*



2. **预定义形状创建：**

   1. **zeros()方法：**

      * 格式：var = np.zeros(数组shape)

      *(注：数列内元素全部初始化为0.)*

      *(注：参数接收的是shape属性元组)*

      *(注：默认类型为float64，可以显式写dtype来控制)*

   2. **ones()方法：**

      * 格式：var = np.ones(数组shape)

      *(注：数列内元素全部初始化为1.)*

   3. **empty()方法：**
   
      * 格式：var = np.empty(数组shape)
   
      *(注：数组元素未初始化，每次创建都是系统随机数)*
   
   4. **full()方法：**
   
      * 格式：var = np.full(数组shape, 元素值)
   
      *(注：数组全部元素被初始化为”元素值“)*
   
   5. **zeros_like()方法：**
   
      * 格式：var = np.zeros_like(other)
   
      *(注：将var初始化为形状与other相同，元素全部为0.，other为ndarray类型)*
   
   6. **ones_like()方法：**
   
   7. **empty_like()方法：**
   
   8. **full_like()方法：**
   
   *(注：6 7 8方法与5雷同，针对shape初始化，参数other均为ndarray类型)*
   
   
   
   3. **序列创建：**
   
      1. **arange()方法：**（等差数列）
   
         * 格式：var = np.arange(start, end, step)
   
         *(注：参数start为起始数值，end为终止数值，区间**左闭右开**，参数step为步长)*
   
      2. **linspace()方法：**（等间隔数列）
   
         * 格式：var = npp.linspace(start, end, num)
   
         *(注：参数start与end同上，区间**左闭右开**，参数num是元素个数，在范围内**均分,**num份相当于除以num，等间隔初始化)*
   
         *(注：元素类型默认float64)*
         
      3. **logspace()方法：**（对数间隔）
      
         * 格式：var = np.logspace(start, stop, n, base=底数)
      
         例：
      
         ~~~python
         arr = np.logspace(0, 4, 3, base=2)
         print(arr) #输出[1, 4, 16]
         ```
         相当于把区间[0,4]均分为3份，得[0,2,4]列表
         以2为底数，输出[2^0, 2^2, 2^4],即[1,4,16]
         ```
         ~~~
      
         *(注：将区间[satrt, stop]均分为n份，得到的一串列表，均以**base为底数进行幂运算**)*
      
         *(注：base默认为10)*
      
   4. **矩阵创建与随机数组创建：**
   
      1. **特殊矩阵：**
   
         * 零矩阵：元素全为0
         * 单位矩阵：主对角线为1，其余元素均为0
         * 对角矩阵：对角线非0，其余为0
         * 对称矩阵：转置后仍然相同的矩阵
         * 逆矩阵：原矩阵*逆矩阵=单位矩阵
   
      2. **eye()方法：**（单位矩阵）
   
         * 格式：var = np.eye(row, col)
   
         *(注：row即行，col即列，col默认为row值)*
   
         *(注：矩阵主对角线为1，其余为0)*
   
      3. **diag()方法：**（对角矩阵）
   
         * 格式：var = np.diag(list)
   
         *(注：主对角线为非0，从左上到右下依次填入list中的元素，其余为0，矩阵为n乘 n大小形状的方形)*
   
      4. **rand()方法：**（0-1随机浮点数）
   
         * 格式：var = np.random.rand(row, col)
   
         *(注：生成元素在0-1之间且为浮点类型，均匀分布，row即行，col即列)*
   
         *(注：参数本质上是一个shape元组)*
   
      5. **uniform()方法：**（按指定区间随机浮点数）
   
         * 格式：var = np.random.uniform(start, end, shape)
   
         *(注：取值区间为[start, end]，元素类型为float，shape为矩阵形状)*
   
      6. **randint()方法：**（按指定区间随机整数）
   
         * 格式：var = np.random.randint(satrt, end, shape)
   
         *(注：取值区间为[start, end]，元素类型为int，shape为矩阵形状)*
   
         *(注：4 5 6元素取值均为随机分布)*
   
      7. **randn()方法：**（正态分布随机取值）
   
         * 格式：var = np.random.randn(row, col)
   
         *(注：生成一个矩阵，元素取值为[-3,3]，元素取值符合**正态分布**)*
   
      8. **seed()方法：**（随机种子设置）
   
         * 格式：seed.random.seed(num)
   
         *(注：num为种子，任意数字，设置后上述随机生成的方法将固定一个随机组合)*
   
         *(注：方法不用变量接收，直接书写)*
   
      
   
      #### **（4）ndarray数据类型：**
   
      1. bool
      2. int
         * int8 uint8
         * int16 uint16
         * int32 uint32
         * int64 uint64
      3. float
         * float16（半）
         * float32（单）
         * float64（双）
      4. complex
         * complex64
         * complex128
   
      
   
      #### **（5）ndarray索引与切片：**
   
      1. **基本索引：**（传统索引方式）
   
      2. **切片：**
   
         1. **范围切片：**
   
            * 格式：容器[start : end : step]
   
            *(注：start为起始索引，默认为0；end为终止索引，默认末索引+1；step为步长，默认为1)*
   
         2. **布尔索引：**
   
            * 格式：容器[条件]
   
            例：
   
            ```python
            list1 = [2, 3, 4]
            arr = np.array(list1)
            print(arr[arr>=3])  #输出[3, 4]
            ```
   
            *(注：条件支持逻辑运算符，返回一个一维列表)*
   
         3. **slice()函数：**
   
            * 格式：var = 容器[slice(start, end, step)]
   
            *(注：start为起始索引，end为终止索引，区间**左闭右开**，step为步长，默认为1)*
   
      
   
      #### **（6）ndarray运算：**
   
      1. **算数运算：**
   
         1. **加减乘除：**（元素级运算）
   
            * 规则：**相同索引**的元素直接加减乘除
   
            *(注：多维数组加减乘除：相同索引元素直接加减乘除)*
   
            *(注：一个多维数组直接与一个标量加减乘除，则每个元素各自与该标量加减乘除)*
   
            *(注：list类型加法即：前者直接拼接后者，无减法)*
   
      2. **广播机制：**（不同shape的数组进行运算）
   
         * 含义：在一定条件下，不同shape的多维数组在加减乘除时，其**拓展变化成相同的shape**的机制
         * **条件：**在同一维度上，尺寸**相同**或其中**有1**
   
      3. **矩阵运算：**
   
         * **矩阵乘法：**@
         * 规则：新得矩阵的**row行col列**的值 等于 **矩阵1第row行**与**矩阵2第col列**中**相同索引**元素**相乘后累加**的值
   
      
   
      ### **3 numpy常用函数：**
   
      #### **（1）基本运算函数：**（12个）
   
      1. **sqrt()函数：**
   
         * 格式：var = np.sqrt(x)
         * 作用：返回x平方根值
   
         *(注：num可以为单个数字，列表，ndarray类型，默认返回float类型)*
   
      2. **exp()函数：**
   
         * 格式：var = np.exp(x)
         * 作用：返回指数e^x值，其中e为自然对数底数，返回float类型
   
      3. **log()函数：**
   
         * 格式：var = np.log(x)
         * 作用：返回对数ln(x)值，返回float类型
   
      4. **sin()函数与cos()函数：**
   
         * 格式：var = sin(x) 或 var = cos(x)
   
         * 作用：返回对应sin(x)值或cos(x)值，返回float类型
   
      5. **abs()函数：**
   
         * 格式：var = np.abs(x)
         * 作用：返回x的绝对值
          
         
   
      *(注：x可以为list或ndarray)*
   
      6. **power()函数：**
   
         * 格式：var = np.power(other, x)
         * 作用：给other中所有元素进行x方计算
   
      7. **round()函数：**
   
         * 格式：var = np.round(x)
         * 作用：返回x的四舍五入值
          
         
   
      *(注：对于intNum.5的四舍五入，会计算成Num而不是Num+1，此为**py特点**)*
   
      8. **ceil()函数与floor()函数：**
   
         * 格式：var = np.ceil(x) 或 var = np.floor(x)
         * 作用：ceil()返回x向上取整的值，floor()返回x向下取整的值
   
      9. **isnan()函数与nan属性：**
   
         * 格式：var = isnan(x)
         * 作用：检验x中是否为缺失值nan
         * 缺失值：np.nan意为非数字空值
          
         
   
      *(注：x可以为单个变量，list对象，ndarray对象)*
   
        *(注：逐个检查x中元素，遇到np.nan返回True，否则返回False)*
   
      
   
      #### **（2）统计函数：**（12个）
   
      1. **sum函数：**
   
         * 格式：var = np.sum(容器)
         * 作用：将所有元素累加
   
      2. **mean()函数：**
   
         * 格式：var = np.mean(容器)
         * 作用：计算返回所有元素的平均数
   
      3. **median()函数：**
   
         * 格式：var = np.median(容器)
         * 作用：先给所有元素升序排序，计算返回所有元素的的中位数，返回类型float
   
      4. **var()函数与std()函数：**
   
         * 格式：var = np.var(容器) 或 var = np.std(容器)
         * 作用：var()返回所有元素的方差，std()返回所有元素的标准差，均返回float类型
   
      5. **max()函数与min()函数：**
   
         * 格式：var = np.max(容器) 或 var = np.min(容器)
         * 作用：max()返回最大值，min()函数返回最小值
   
      6. **argmax()函数与argmin()函数：**
   
         * 格式：var = np.argmax(容器) 或 var = np.argmin(容器)
          
         * 作用：argmax()返回最大值的索引，argmin()返回最小值的索引
   
   7. **percentile()函数：**
   
      * 格式：var = np.percentile(容器, x)
      * 作用：计算返回容器中百分之x分位数，返回float类型
   
   8. **cumsum()函数：**（累和）
   
      * 格式：var = np.cumsum(容器)
      * 作用：返回一个list对象，每个元素都是前面元素的累加而得的值
   
      *(注：类似等差中的(S1, S2 , ..., S(n-1), Sn)*
   
   9. **cumprod()函数：**（累积）
   
      * 格式：var = np.cumprod(容器)
      * 作用：返回一个list对象，每个元素都是前面元素的累乘而得的值
   
   
   
   #### **（3）比较函数：**（10个）
   
   1. **greater()函数：**
   
      * 格式：var = np.greater(容器, x)
      * 作用：逐个元素与x比较，大于的为True，否则为False，返回一个布尔list
   
   2. **less()函数：**
   
      * 格式：var = np.less(容器, x)
      * 作用：逐个元素与x比较，小于的为True，否则为False，返回一个布尔list
   
   3. **equal()函数：**
   
      * 格式：var = np.equal(容器, x)
      * 作用：逐个元素与x比较，等于的为True，否则为False，返回一个布尔list
   
   4. **logical_and()函数：**
   
      * 格式：var = np.logical_and(容器1, 容器2)
      * 作用：对应索引的元素比较，二者均为非0返回True，二者有0返回False，返回一个布尔list
   
   5. **logical_not()函数：**
   
      * 格式：np.logical_not(容器)
      * 作用：依次检查每个元素，非0返回False，0返回True，返回一个布尔list
   
   6. **logical_or()函数：**
   
      * 格式：var = np.logical_or(容器1, 容器2)
      * 作用：对应索引的元素比较，二者有非0返回True，二者均为0返回False
   
   7. **any()函数：**
   
      * 格式：var = np.any(容器)
      * 作用：只要有一个非0，就返回True，全0返回False
   
   8. **all()函数：**
   
      * 格式：var = np.all(容器)
      * 作用：只要有一个0，就返回False，全非0返回True
   
   9. **where()函数：**
   
      * 格式：var = np.where(条件, 符合容器, 不符合容器)
      * 作用：判断条件真假，真从符合容器依次取值，假从不符合容器依次取值，最后返回一个list
   
   10. **select()函数：**
   
       * 格式：var = np.select(条件, 返回结果)
       * 作用：逐个元素判断是否属于条件中之一，返回对应的结果
   
       *(注：条件旅游为一个布尔list，返回结果也可以是list)*
   
   
   
   #### **（4）排序函数：**（6个）
   
   1. **sort()函数：**
   
      * 格式：var = np.sort(容器)
      * 作用：给容器升序排序，返回一个新数组
   
      *(注：与py原生sort()函数不同，前者无须接收返回值且改变容器本身，np.sort()需被接收返回值且不改变容器自身)*
   
   2. **argsort()函数：**
   
      * 格式：var = np.argsort(容器)
      * 作用：给元素升序排序后，返回旧索引组成的list
   
   3. **unique()函数：**
   
      * 格式：var = np.unique(容器)
      * 作用：去重后升序（默认）排序
   
   4. **concatenate()函数：**
   
      * 格式：var = np.concatenate(容器1, 容器2)
      * 作用：将容器2拼接到容器1后面
   
   5. **split()函数：**
   
      * 格式：var = np.split(容器, x)
      * 作用：将数组切割，得若干array
   
      *(注：参数x为单数字时，容器被均分成x份，若均分不了则报错；x为**索引ist**时，容器在**指定索引处切割**)
   
   6. **reshape()函数：**
   
      * 格式：var = np.reshape(容器, 新shape)
      * 作用：将原数组的形状更新为新shape
   
      *(注：若更新为新形状时不等分，则会报错)*
   
      *(注：新shape中必写row行，列可以写**-1**，这样可以使py**自行计算col列**的大小)*
   
      
   
   
   
   ​        
   
      
   
      ​     
   
      
   
   ​     
   
   ​      
   
   ​      
   
   ​      
   
   ​      
   
   ​      
   
   ​      
   
   ​      
   
   
   
      
   
      
   
      





 

