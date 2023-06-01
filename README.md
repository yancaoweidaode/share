# share
你可以按照以下步骤将清华源添加到 Ubuntu 20.04 的软件源中：

1. 备份原来的软件源列表，以便出现问题时可以恢复配置文件：

   ```
   sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
   ```

2. 打开软件源列表：

   ```
   sudo nano /etc/apt/sources.list
   ```

3. 在文件末尾添加清华源：

   ```
   # 清华源
   deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
   deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
   deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
   deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
   deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
   deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
   deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
   deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
   ```

4. 保存并退出编辑器。

5. 更新软件包索引：

   ```
   sudo apt update
   ```

现在，你可以使用清华源通过 apt 安装软件包了。