#### **实验目标**

编写Java程序生成考拉兹序列（Collatz sequence），实现以下功能：

- **方法** `nextNumber(int n)`：返回下一个数
- **主方法** `main`：从n=5开始打印完整序列

---

#### **Collart规则**

1. **偶数**：next = n / 2
2. **奇数**：next = 3n + 1
3. **终止条件**：n = 1时结束

**示例**（起始数5）：  
`5 → 16 → 8 → 4 → 2 → 1`

---

#### **核心实现步骤**

##### 1. 实现`nextNumber`方法

```java
/**
 * 计算考拉兹序列下一项
 * @param n 当前项
 * @return 下一项数值
 */
public static int nextNumber(int n) {
    if (n % 2 == 0) {
        return n / 2;  // 偶数处理
    } else if (n == 1) {
        return 1;       // 终止条件
    } else {
        return 3 * n + 1; // 奇数处理
    }
}
```

**关键修复**：

- 增加`n == 1`的判断，避免无限循环
- 原错误实现未处理n=1的情况

##### 2. 主方法实现

```java
public static void main(String[] args) {
    int n = 5;
    System.out.print(n);
    while (n != 1) {
        n = nextNumber(n);
        System.out.print(" → " + n);
    }
    System.out.println();
}
```

**输出示例**：  
`5 → 16 → 8 → 4 → 2 → 1`

---

#### **Java语法要点**

- **取余运算** `%`：  
    `x % 4` 返回0、1、2或3
- **相等判断** `==`：  
    `if (n % 4 == 1)` 判断余数是否为1

---

#### **实验验证**

1. **基础测试**：验证起始数5的输出
2. **边界测试**：测试n=1时直接终止
3. **扩展测试**：尝试大数值如n=27（需112步到达1）

---

#### **数学背景**

考拉兹猜想（未证明）：  
所有正整数最终都会收敛到1。已验证至2⁶⁸量级，尚未发现反例。