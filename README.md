# Flow-Assistance-of-Delft3D
本项目将Delft3D中Flow常用功能集中显示，添加并行运算可视化、无人值守计划任务列表功能。

**目的**：
    本人平时用的多的就网格、插值、水动力和后处理模块，看到了B站@sosoly1978（https://www.bilibili.com/video/BV1jN4y127HA/?spm_id_from=333.337.search-card.all.click&vd_source=9e5fd74d3207deedeedec5d44c6b2289）开发的gui，
需要加QQ获取，本人十分社恐，于是为了方便自己使用，制作了这个软件。
****仅供学习交流使用，不可用做其他用途****
    本人才疏学浅，软件仍有许多问题和改进的空间，但没时间继续优化，如果有大佬做了更好的可以让我也体验一下将万分荣幸！

**功能**：
1、将Delft3D-Flow模型制作时使用的网格、插值、水动力和后处理模块集合在一起；
2、并行运算可视化；
   初始化时读取用户计算机核心数，设置计算核心可选范围为总核心数-1；
3、无人值守预安排计算任务。
   通过添加mdf文件（可在不同路径下，不同路径下可同名，同路径下不可重复）并调整mdf文件顺序，点击计算可按顺序执行，取消勾选无人值守则只计算待计算任务的第一个。


**说明**：
1、首次使用选择安装的Delft3D路径，选择至版本文件夹，如安装了多个版本，选择其中一个，如：C:\Program Files\Deltares\Delft3D 4.04.01。没有添加修改路径功能（毕竟选了之后也没必要修改），如需重置，在Happy2Flow.exe同路径下添加“initial.txt”（不用引号）文件可初始化软件；
2、首次使用会提示以后是否弹出提醒，可选择下次是否弹出；
3、使用本软件默认对Dleft3D和Matlab有基础的了解，并会使用mpi（
  首次使用并行运算需开启smpd服务：
  使用管理员权限开启命令提示符，输入
      cd C:\Program Files\Deltares\Delft3D 4.04.01\x64\share\bin
      smpd -install -phrase behappy
  运行后提示“MPICH2 Process Manager, Argonne National Lab installed.”即成功，注意修改响应的版本号）
4、软件通过在第6s、1min、10min、30min和后续间隔60min检测d_hydro.exe进程，判断是否开始下一个任务的计算，在这些时间点会短暂消耗算力（非常短暂，就像计算动量时写入文件时的卡顿一样），为正常现象。
5、软件有Matlab2023b版本上编写，因此使用打包的软件需要相应版本的编译器（https://ww2.mathworks.cn/products/compiler/matlab-runtime.html下载）
6、Happy2Flow.zip中有简单的测试算例


**问题**：
1、由于未知原因，quickplot模块在matlab中可以正常调用，在打包软件中，每次可以正常启动，但显示初始化界面后进程会结束，因此1.7版本中仅通过打开文件目录，需要手动打开 d3d_qp.exe ，路径、环境等原因都尝试过，也是过创建批处理文件等均未解决，本人非计算机专业，能力有限，请大佬不吝赐教，不胜感激！
2、如上所述、非计算机专业，因此不会优化，使用时内存占用需要留意（毕竟flow计算对内存要求也不高）、启动时会短暂占用cpu。
