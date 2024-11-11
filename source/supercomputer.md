# 杭州电子科技大学超算使用指南

## 基础知识

### 软件简明教程

这里只讲软件使用的必要步骤，详细使用及安装请移步[linux 学习笔记（施工中……）](https://github.com/LCQaha/My_notebook/blob/main/Linux/HanSP_notebook.md#%E8%BD%AF%E4%BB%B6%E6%96%BD%E5%B7%A5%E4%B8%AD)，如果觉得本节太难请直接跳过。

软件网盘资源请[点击此处](https://pan.baidu.com/s/14sh6Jx0jNJekzR0epgrdgQ?pwd=yxsm)

在本节中，将介绍如何使用 XShell 和 Xftp。根据当前信息，这两个软件只能在杭州电子科技大学校园网中使用，若使用时您在校外，请使用 VPN 登陆后直接在网页操作。

#### XShell

本软件用于取代网页端的命令行操作。

1. 点击`命令行[E-Shell]`
   ![supercomputer_EShell.png](./img/supercomputer_EShell.png)
2. 下载密钥文件
   记住这里的 ip 和端口号，后面需要用到。
   ![supercomputer_download_rsa.png](./img/supercomputer_download_rsa.png)
3. 修改名称
   将下载的文件`*_rsa.txt`修改为`*_rsa`，这是用于访问超算服务器的私钥。
4. 打开 XShell，完成基本设置
   - 点击`文件-新建`
     ![supercomputer_XShell_create_link_1.png](./img/supercomputer_XShell_create_link_1.png)
   - 在`链接`选项下作如下设置，请对照和下载时的 ip 和端口号是否一致：
     ![supercomputer_XShell_create_link_2.png](./img/supercomputer_XShell_create_link_2.png)
   - 在`用户身份验证`选项下修改登录方式为`Public Key`，并输入用户名（确保与你的超算账号用户名一致）
     ![supercomputer_XShell_create_link_3.png](./img/supercomputer_XShell_create_link_3.png)
   - 选中`Public Key`，点击设置
     ![supercomputer_XShell_create_link_4.png](./img/supercomputer_XShell_create_link_4.png)
   - 在设置中选择选择密钥文件，点旁边的三个点。
     ![supercomputer_XShell_create_link_5.png](./img/supercomputer_XShell_create_link_5.png)
   - 点击导入，找到你刚才保存的密钥文件，点击确定。
     ![supercomputer_XShell_create_link_6.png](./img/supercomputer_XShell_create_link_6.png)
   - 点击图中按钮，将链接添加至链接栏。
     ![supercomputer_XShell_create_link_7.png](./img/supercomputer_XShell_create_link_7.png)
   - 点击链接，开始访问。
5. 基本命令教学
   - `ls`：列出当前目录下的所有文件。
   - `

#### Xftp

本软件用于与远端服务器（这里是超算）进行文件传输。

1. 从 XShell
2. 打开 Xftp，完成基本设置
   - 点击`文件-新建`
     ![supercomputer_Xftp_create_link_1.png](./img/supercomputer_Xftp_create_link_1.png)
   - 按照下图所示进行设置：（ip 和端口号、用户名、Public Key，与 XShell 一致）
     ![supercomputer_Xftp_create_link_2.png](./img/supercomputer_Xftp_create_link_2.png)
3. 向远端服务器发送文件
   - 登录成功后，窗口会分成两个区域，左侧为你的本地目录，右侧为远端服务器目录。
     ![supercomputer_Xftp_send_file_1.png](./img/supercomputer_Xftp_send_file_1.png)
   - 在打开远程服务器中，接收文件的目标文件夹，然后本地找到需要传送的文件或文件夹，`右键-传输`即可发送到服务器。

### 网页端使用

点击下面的网址输入账号密码后登陆：
[https://manage-sc.hdu.edu.cn/sso/login](https://manage-sc.hdu.edu.cn/sso/login)

若您处于校外，请使用 VPN 进行登录，然后在 VPN 中选择“超算平台”并输入账号。

1. [杭州电子科技大学 VPN](https://vpn.hdu.edu.cn)

#### 文件上传

1. 点击网页上方的`数据管理-文件管理（E-File）`
2. 点击上传，选择上传文件或文件夹。

#### E-Shell 命令行

作用与 XShell 类似，由于网络原因，不建议使用远程命令行工具。

## MATLAB

### 上传代码文件

为了保证作业的规范性，在上传代码文件时请遵循以下规则：

1. 在用户主目录下创建一个名为`code`的文件夹，所有代码均保存在这里。
2. 如果一个账号有多人同时使用，建议在`code`下建立一个以名字命名的文件夹（不得使用空格、中文及其他特殊符号）。
3. 文件上传到自己的代码文件夹中。

【例】张三和李四属于同一个科研小组 A，他们创建了一个名为`A_part`的超算账号共同使用，则张三的代码存放路径`/public/home/A_part/code/zhangsan`，李四的代码存放路径`/public/home/A_part/code/lisi`。
张三需要跑一个 MATLAB 代码，其将代码存放在`/public/home/A_part/code/zhangsan/MATLAB_JOB_A_1`下，但第一次跑出的结果不理想，于是修改代码后将代码传到`/public/home/A_part/code/zhangsan/MATLAB_JOB_A_2`。
**再次申明，当前不建议在一个文件夹中运行两次代码，如确有需求，请联系管理员解决问题。**

### 作业提交

1. 将光标置于上方第一个选项的位置（这里是“工程计算”）然后选择`仿真计算`
   ![supercomputer_matlab_guide_1.png](./img/supercomputer_matlab_guide_1.png)
2. 将光标置于 Matlab 上，可以选择模板、命令行、图形三种模式（若没此选项请联系管理员）
   ![supercomputer_matlab_guide_2.png](./img/supercomputer_matlab_guide_2.png)
   ![supercomputer_matlab_guide_3.png](./img/supercomputer_matlab_guide_3.png)
3. 如果代码中不含有`parpool`等调用并行计算的代码，则只需申请一个核心就可以了。

#### 图形化界面

下图是图形化界面配置选择界面，在这里选择本次开启使用的版本、核心数和最大运行时间。（建议 4 个或更多）
![supercomputer_matlab_gui_4.png](./img/supercomputer_matlab_gui_4.png)
系统中自带的 Matlab 版本及其位置：

- 2021b：`/public/software/apps/MatlabR21b/bin/matlab`
- 2020a：`/public/software/apps/MatlabR20a/R2020a/bin/matlab`

**注意**：
**1. 模板中的预置版本不能使用，请自己手动配置可用路径，若需其他版本，请联系管理员。**
**2. 图形化界面使用完后，务必手动关闭，否则会持续计费至截止时间，并占据超算资源，请避免资源浪费。**
**3. 最大运行时限到达后会强制结束进程，请至少设置 72 小时，避免计算任务无法完成。**

#### 模板

下图是模板配置界面，在这里选择需要使用的代码文件，以及版本、所需的计算资源。

#### slurm 脚本

### 代码规范

1. 文件路径
   由于 Windows 和 Linux 系统文件路径格式不同，故建议通过代码代替路径字符串建立文件的保存路径。**（严禁使用斜线表示路径）**

   ```matlab
   %% 代码说明：
   % 本示例代码表示了一个简单的文件/文件夹创建方法。
   % 示例方法只能建立一层文件结构，本示例中创建的是".\my_foldername\"，若要建立多层，则需在fullfile()中添加更多的字符串。
   % 如创建".\subfolder\my_foldername\"，则使用：
   % fullfile(pwd,'subfolder',my_foldername)

   %% 代码示例：

   % 获取当前工作目录（绝对路径）
   current_dir = pwd;

   % 设置文件夹名称
   folder_name = 'my_foldername';

   % 拼接路径
   folder_path = fullfile(current_dir,folder_name);

   % 创建文件夹
   if ~exist(folder_path, 'dir')
      mkdir(folder_path);
      disp(['文件夹 ', folder_name, ' 创建成功']);
   else
      disp(['文件夹 ', folder_name, ' 已经存在']);
   end

   %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%


   % 一个向my_foldername写入文本的例子

   text_file = 'my_textfile.txt';
   file_path = fullfile(folder_path,text_file);
   f = fopen(file_path,'w');
   fprintf(f,'This is a test file.');
   fclose(f);
   disp(['文本文件 ', text_file, ' 创建成功']);
   disp(['文本文件路径：', file_path]);

   ```

2. 调用并行池

   ```matlab
   delete(gcp('nocreate'));      % 删除当前存在的并行池
   mypar = parpool(<corenum>);   % 创建并行池，<corenum>为核数

   parfor ……

   end

   delete(mypar);                % 删除并行池

   ```

## Pytorch（施工中……）
