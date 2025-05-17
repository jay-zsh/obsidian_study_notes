#### **实验准备**

1. 拉取代码：终端执行 `git pull skeleton master` 获取 `lab2/` 文件夹
2. 导入项目：在IntelliJ中导入 `lab2/pom.xml`

---

### **调试器核心工具**

#### **基础操作**

1. **设置断点**  
    ![断点示意图](https://sp21.datastructur.es/materials/lab/lab2/img2/breakpoint.png)
    
    - 点击行号右侧添加红色断点
    - 右键文件选择 `Debug` 启动调试
2. **执行控制**  
    ![调试按钮](https://sp21.datastructur.es/materials/lab/lab2/img2/debug_button.png)
    
    - **Step Into (F7)**：进入方法内部
    - **Step Over (F8)**：执行当前行，不进入方法
    - **Step Out (Shift+F8)**：跳出当前方法
    - **变量监视**：在调试窗口查看实时变量值
3. **流式调试技巧**
    
    - 优先使用 `Step Over` 快速定位问题范围
    - 嵌套调用时使用 `Evaluate Expression` 快速验证表达式结果

---

### **JUnit单元测试**

#### **测试结构**

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class ArithmeticTest {
    @Test
    void testSum() {
        assertEquals(11, Arithmetic.add(5, 6));  // 预期 vs 实际值
    }
}
```

#### **测试运行**

1. **单测试运行**：点击测试方法旁的绿色箭头
2. **批量运行**：右键测试类选择 `Run...`
3. **失败定位**：点击错误信息跳转到问题代码行

#### **高级测试技巧**

```java
@ParameterizedTest
@ValueSource(ints = {0, -5, 100})
void testEdgeCases(int input) {
    assertTrue(MyClass.process(input) >= 0);
}
```

---

### **IntList调试案例**

#### **案例A：列表元素偏移**

```java
// Bug示例：错误累加逻辑
public static void addConstant(IntList p, int c) {
    while (p != null) {
        p.first += c;  // 正确：p.first = p.first + c
        p = p.rest;
    }
}

// 测试验证
@Test
void testAddConstant() {
    IntList lst = IntList.of(1, 2, 3);
    addConstant(lst, 1);
    assertEquals("2 -> 3 -> 4", lst.toString());
}
```

#### **案例B：极值条件过滤**

```java
// Bug示例：最大值首位末位判断错误
private static int max(IntList p) {
    int max = Integer.MIN_VALUE;
    while (p != null) {
        if (p.first > max) max = p.first;  // 正确：应更新max
        p = p.rest;
    }
    return max;
}

// 调试技巧：在循环体内设置条件断点(p.first > currentMax)
```

---

#### **实验提交**

1. 本地测试：通过全部JUnit测试（绿色进度条）
2. 代码推送：`git push origin main`
3. 提交至Gradescope平台

---

### **常见问题**

1. **JDK版本冲突**  
    检查 `File > Project Structure > SDK` 是否匹配Java 15+
2. **调试器无响应**
    - 确保在 `Debug` 模式运行
    - 检查断点是否激活（红色实心圆点）