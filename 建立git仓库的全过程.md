### **Git 初始化仓库并关联 GitHub 的全流程*

#### **1. 本地仓库初始化**

1. **创建本地目录**
   
   ```bash
   mkdir your-project   # 创建项目目录 
   cd your-project      # 进入目录
   ```

2. **初始化 Git 仓库**

   ```bash
   git init             # 生成 .git 文件夹，标记为 Git 仓库
   ```

---

#### **2. 配置 Git 用户信息**

全局配置（适用于所有仓库） 

```bash
git config --global user.name "Your Name"          # 设置用户名
git config --global user.email "your.email@example.com"  # 设置邮箱
```
---

#### **3. 关联 GitHub 远程仓库**

1. **在 GitHub 创建远程仓库**
   
    - 登录 GitHub，点击 **New Repository**，填写仓库名称并创建。
    - 获取仓库的 SSH 地址（格式：`git@github.com:username/repo.git`）

2. **本地关联远程仓库**

```bash
git remote add origin git@github.com:username/repo.git  # 关联远程仓库（origin 为别名）
```

---

#### **4. 推送代码到远程仓库**

1. **添加文件到暂存区**
   
```bash
git add . # 添加当前目录所有文件
git add file1.txt file2.txt  # 或指定文件
```

2. **提交到本地仓库**
   

 ```bash
 git commit -m "Initial commit"  # 提交并添加描述
 ```

3. **推送到远程仓库**
   
```bash
git push -u origin main # 首次推送并设置跟踪关系
```
- `-u` 参数建立本地与远程分支的默认关联，后续可直接使用 `git push`

---

#### **5. 验证关联状态**

```bash
git remote -v          # 查看远程仓库地址是否正确绑定
git branch -vv         # 检查本地分支是否跟踪远程分支
```

---

### **注意事项**

1. **SSH 密钥配置**
   
    - 本地需预先配置 SSH 密钥并添加到 GitHub 账户的 **SSH Keys**中（否则推送会提示权限错误）
    - 测试连接：`ssh -T git@github.com`，验证是否返回成功提示
2. **分支名称兼容性**
   
    - GitHub 新仓库默认分支为 `main`（旧版本可能为 `master`），需根据实际情况调整推送命令
3. **冲突处理**
   
    - 若远程仓库已有内容，需先运行 `git pull origin main --allow-unrelated-histories` 再推送

---

### 流程图

`新建本地目录 → git init → 配置用户 → 关联远程仓库 → add → commit → push -u`