# 杭州电子科技大学超算使用指南

## 基础知识

### 软件简明教程

这里只讲软件使用的必要步骤，详细使用请移步[linux 学习笔记（链接施工中……）]()，如果觉得本节太难请直接跳过。

1. XShell
2. Xftp

### E-Shell 命令行

点击下面的网址输入账号密码后登陆：
[https://manage-sc.hdu.edu.cn/sso/login](https://manage-sc.hdu.edu.cn/sso/login)

### slurm 脚本编写

```bash
#!/bin/bash
#SBATCH -J <job_name>
#SBATCH -p <process_name>
#SBATCH -N <node_number>
#SBATCH --ntasks-per-node=<core_number>
#SBATCH --gres=gpu:<gpu_number>
#SBATCH --time=<time_limit>

cd $SLURM_SUBMIT_DIR
#################################
source /public/software/profile.d/***.**

srun hostname -s | sort -n >slurm.hosts
OMP_NUM_THREADS = $SLURM_NPROCS

```

## 实战

### MatLab

1. 单核心

   ```sh
   #!/bin/bash
   #SBATCH -J matlab_job
   #SBATCH -p normal
   #SBATCH -N 1
   #SBATCH --ntasks-per-node=1
   #SBATCH --time 24:00:00

   cd $SLURM_SUBMIT_DIR
   source /public/software/profile.d/apps_matlab2020a.sh

   matlab -nodesktop -nosplash -nodisplay -r <matlab_script>
   ```

2. 多核心
