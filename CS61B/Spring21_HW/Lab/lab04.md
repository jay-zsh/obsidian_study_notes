### 学习git
>学习[[git的使用]]


- 本地 git 工作流程： `git add` 和 `git commit`
- 使用 `git checkout` 在提交之间移动并更新文件
- 分离的 `HEAD` 状态
- 本地 git 与远程存储库集成： `origin/master` 和 `skeleton/master`

```shell
# 1. 查看提交历史获取目标commit hash
git log

# 示例输出：
# abc1234 (HEAD -> main) 最新提交
# def5678 旧版本提交
# ghi9012 初始提交

# 2. 将工作区恢复至目标版本（保留后续提交历史）
git checkout def5678 -- .  # 注意最后的点表示所有文件

# 3. 提交恢复操作（生成新版本记录）
git commit -m "恢复至def5678版本"
```

### == vs equals()
```java
public static boolean isSameNumber(Integer a, Integer b) {  
    return a.equals(b);  
}
```
