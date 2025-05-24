## Git 同步到 GitHub 的完整指南

### 1. 初始化本地仓库
如果你的项目还没有初始化 Git 仓库，可以运行以下命令：
```bash
git init
```
这将在当前目录下创建一个新的 Git 仓库。

### 2. 添加文件到暂存区
使用以下命令将文件添加到暂存区：
```bash
git add <文件名>
```
或者
```bash
git add .  
```
或者    
```
git add *
```
这将添加当前目录下的所有文件。
### 3. 提交更改
使用以下命令提交更改：
```bash
git commit -m "提交信息"
```
这将提交暂存区中的所有更改，并添加一条提交信息。

### 4. 关联远程仓库
使用以下命令关联远程仓库：
```bash
git remote add origin <远程仓库地址>
```
将 `<远程仓库地址>` 替换为你的 GitHub 仓库的 URL，例如：
```bash
git remote add origin https://github.com/yourusername/yourrepository.git   
``` 
### 5. 推送更改到远程仓库    
使用以下命令将本地仓库的内容推送到远程仓库：
```bash
git push -u origin main
```
这将把本地的 `main` 分支推送到远程仓库的 `main` 分支。如果你的远程仓库没有 `main` 分支，你可以使用 `master` 分支。
如果是第一次推送，需要加上 `-u` 参数，这样以后就可以直接使用 `git push` 命令了。 
### 6. 检查远程仓库  
使用以下命令检查远程仓库：  
```bash 
git remote -v   
```
这将显示远程仓库的名称和 URL。  
### 7. 拉取远程仓库的更改    
使用以下命令拉取远程仓库的更改：    
```bash
git pull origin main    
``` 
这将把远程仓库的 `main` 分支拉取到本地仓库的 `main` 分支。  
### 8. 解决冲突  
如果在拉取远程仓库的更改时发生冲突，你需要手动解决冲突。
使用以下命令查看冲突的文件：
```bash 
git status  
``` 
这将显示冲突的文件。    
使用文本编辑器打开冲突的文件，手动解决冲突。    
解决冲突后，手动将文件添加到暂存区并提交更改。   
### 9. 常见问题及解决方法
#### 问题 1：`fatal: unable to access ... Recv failure: Connection was reset`
**原因**：网络连接问题，可能是由于代理、防火墙或网络限制。

**解决方法**：
1. 检查网络连接是否正常。
2. 如果在中国，尝试使用 VPN 或代理。
3. 清除 Git 的代理设置：
   ```bash
   git config --global --unset http.proxy
   git config --global --unset https.proxy
   ```

---

#### 问题 2：`fatal: unable to access ... Failed to connect to github.com port 443`
**原因**：无法通过 HTTPS 连接到 GitHub，可能是网络问题、防火墙限制或 DNS 配置问题。

**解决方法**：
1. **检查网络连接**：
   - 测试是否可以访问 GitHub：
     ```bash
     ping github.com
     ```
   - 如果无法访问，尝试使用 VPN 或代理。

2. **切换到 SSH 方式**：
   - 生成 SSH 密钥：
     ```bash
     ssh-keygen -t rsa -C "your_email@example.com"
     ```
   - 将公钥添加到 GitHub 账户中。
   - 更改远程仓库 URL：
     ```bash
     git remote set-url origin git@github.com:你的用户名/你的仓库名.git
     ```
   - 测试 SSH 连接：
     ```bash
     ssh -T git@github.com
     ```

3. **修改 DNS 设置**：
   - 将 DNS 设置为公共 DNS（如 Google DNS 或 Cloudflare DNS）：
     - Google DNS: `8.8.8.8` 和 `8.8.4.4`
     - Cloudflare DNS: `1.1.1.1` 和 `1.0.0.1`

4. **增加连接超时时间**：
   - 如果网络较慢，可以尝试增加 Git 的超时时间：
     ```bash
     git config --global http.lowSpeedLimit 0
     git config --global http.lowSpeedTime 999999
     ```

---

### 8. 总结
通过以上步骤，你可以完成 Git 与 GitHub 的同步操作，并解决常见问题。如果遇到其他问题，可以参考 Git 官方文档或 GitHub 帮助中心。

### 9. 参考资料
- [Git 官方文档](https://git-scm.com/doc)
- [GitHub 帮助中心](https://help.github.com)
- [Git 常见问题解答](https://git-scm.com/docs/gitfaq)