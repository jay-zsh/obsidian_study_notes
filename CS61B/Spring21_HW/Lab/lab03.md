### 增强型 for 循环（Java）

#### 核心语法

```java
for (Type variable : iterable) { 
    // 使用 variable
}
```

#### 等价传统写法

```java
for (int i = 0; i < array.length; i++) {
    Type variable = array[i];
    // 使用 variable
}
```

#### 关键特性

▸ 专为遍历数组/集合设计  
▸ 不支持索引访问（需传统for循环）  
▸ 在测试代码中：  
- 使用 `AList` 因支持 O(1) 随机访问  
- 避免使用 `SLList`（链表结构get(i) 为 O(N)）

#### 性能对比表

| 数据结构   | get(i) 时间复杂度 | 适用场景 |
| ------ | ------------ | ---- |
| AList  | O(1)         | 随机访问 |
| SLList | O(N)         | 顺序访问 |

#### 测试参数

```java
int[] testSizes = {1000, 2000, 4000, 8000, 16000, 32000, 64000, 128000};
```

▸ 采用指数级增长测试规模  
▸ 每次测试执行 10,000 次 getLast() 操作