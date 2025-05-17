#### 条件语句

```java
// 单行条件
if (x < 10) x += 10;

// 多行代码块
if (x < 10) {
    System.out.println("x is small");
    x += 10;
}

// 常见错误：未加花括号
if (x < 0)
    System.out.println("Negate"); // 仅此句受if控制
    x = -x;                       // 始终执行❗
```

**规范要求**  
▸ 必须使用花括号包裹代码块  
▸ 支持两种花括号风格：

```java
// K&R 风格
if (cond) {
}

// Allman 风格
if (cond)
{
}
```

---

#### 循环结构

**While 循环**

```java
int i = 0;
while (i < 5) {
    System.out.println(i);
    i++;
}
```

**For 循环**

```java
// 传统形式
for (int i=0; i<arr.length; i++) {
    sum += arr[i];
}

// 增强形式（遍历数组/集合）
for (String s : stringArray) {
    System.out.println(s);
}
```

**流程控制**

```java
continue;  // 跳过本次循环
break;     // 终止当前循环
```

---

#### 基本数据类型（Primitive Types）

|类型|位数|取值范围|默认值|示例|
|---|---|---|---|---|
|`byte`|8|-128 ~ 127|0|`byte b = 100;`|
|`short`|16|-32768 ~ 32767|0|`short s = 500;`|
|`int`|32|-2³¹ ~ 2³¹-1|0|`int x = 1000000;`|
|`long`|64|-2⁶³ ~ 2⁶³-1|0L|`long l = 100L;`|
|`float`|32|±1.4E-45 ~ ±3.4E38|0.0f|`float f = 3.14f;`|
|`double`|64|±4.9E-324 ~ ±1.7E308|0.0d|`double d = 3.14;`|
|`char`|16|'\u0000' ~ '\uffff'|'\u0000'|`char c = 'A';`|
|`boolean`|1|true/false|false|`boolean flag=true;`|

---

#### 引用数据类型（Reference Types）

|类型|特点|示例|
|---|---|---|
|`String`|不可变字符序列|`String s = "Hello";`|
|数组|固定长度容器|`int[] arr = {1,2,3};`|
|类对象|通过`new`创建|`Scanner sc = new Scanner();`|
|接口|只能被实现|`List<String> list = new ArrayList<>();`|
|枚举|固定常量集合|`enum Color { RED, GREEN }`|

---

#### 方法定义

```java
public static int max(int x, int y) {
    return (x > y) ? x : y;
}
```

▸ 必须声明返回类型（`void` 表示无返回值）  
▸ 参数需明确类型  
▸ 方法签名示例：`public static int max(int x, int y)`

---

#### 数组操作

**声明与初始化**

```java
int[] arr = new int[3];       // [0,0,0]
int[] nums = {4,7,10};        // 直接初始化
```

**关键属性**

```java
arr.length  // 数组长度（非方法）
```

**遍历方式对比**

```java
// 传统for（需索引时使用）
for (int i=0; i<arr.length; i++) {
    System.out.println(arr[i]);
}

// 增强for（仅需元素时使用）
for (int num : arr) {
    System.out.println(num);
}
```

---

#### 练习关键点

**求数组最大值**

```java
public static int max(int[] m) {
    int max = m[0];
    for (int num : m) {
        if (num > max) max = num;
    }
    return max;
}
```

**windowPosSum**

```java
public static void windowPosSum(int[] a, int n) {
    for (int i=0; i<a.length; i++) {
        if (a[i] <= 0) continue;
        
        int sum = 0;
        for (int j=i; j<=Math.min(i+n, a.length-1); j++) {
            sum += a[j];
        }
        a[i] = sum;
    }
}
```

▸ 边界处理：`Math.min(i+n, a.length-1)`  
▸ 跳过负数元素：`continue`

---

#### 代码规范速查表

|场景|正确写法|错误写法|
|---|---|---|
|条件语句|必加花括号|省略花括号|
|方法返回值|必须匹配声明类型|缺少return语句|
|数组长度|`arr.length`（属性）|`arr.length()`（方法）|
|增强for循环|仅用于遍历|尝试修改元素|
