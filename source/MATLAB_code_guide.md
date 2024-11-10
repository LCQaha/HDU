# MATLAB 代码编写规范

## 代码提速技巧

### 常用提速技巧

在这一节中，我将讲一个例子，通过这个例子来介绍一些常用的提速技巧。这些例子通过如下代码运行：

```matlab
clear all
% 建议测试规模:
%1--不超过2500;
%2&3--不超过5000:
% 200以上体现并行计算的优势
% 50以上并行计算反而慢


%% 第一部分
% fprintf('不分配空间的循环:');
% tic;Accelerate1(5000);toc;

fprintf('分配空间的循环:');
tic;Accelerate2(5000);toc;

fprintf('分配空间的矩阵化:');
tic;Accelerate3(5000);toc;

%% 第二部分
fprintf('并行计算:');
tic;Accelerate4(5000,50,4);toc;

fprintf('非并行计算:');
tic;Accelerate5(5000,50);toc;
```

1. 提前分配空间
   先来看`Accelerate1`和`Accelerate2`：

   ```matlab
   function Accelerate1 (mysize)

       A=rand(mysize);

       for i = 1:size(A,1)
           for j = 1:size(A,2)

               if A(i,j)>0.5
                   B(i,j)=A(i,j);
               else
                   B(i,j)=-A(i,j);
               end
           end
       end

   end
   ```

   ```matlab
   function Accelerate2 (mysize)


       A=rand(mysize);
       B=A*0;

       for i = 1:size(A,1)
           for j = 1:size(A,2)

               if A(i,j)>0.5
                   B(i,j)=A(i,j);
               else
                   B(i,j)=-A(i,j);
               end
           end
       end

   end
   ```

   `Accelerate1`和`Accelerate2`函数的代码实现方式基本相同，但`Accelerate2`函数在循环前提前将与矩阵 A 同等大小的零矩阵赋值给了 B，起到了**提前分配空间**的作用。

### 检查代码资源消耗情况

只靠范例来寻找错误显然是不够的，我们可以使用 MATLAB 自带的`运行并计时（）`功能查看每一行代码的执行时间，从而找出消耗计算资源的罪魁祸首。

### 远程集群多核心并行运算代码编写范例

参考资料：
[1] [让所有的 MATLAB 用户都能用集群做并行计算](https://blog.csdn.net/sizheng0320/article/details/104012909)
