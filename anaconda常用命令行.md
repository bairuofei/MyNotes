# Anaconda常用命令行

```bash
conda activate                         // 切换到base环境

conda deactivate                 // 退出anaconda虚拟环境

conda activate learn                   // 切换到learn环境

conda create -n learn python=3   // 创建一个名为learn的环境并指定python版本为3(的最新版本)

conda env list                   // 列出conda管理的所有环境

conda list                       // 列出当前环境的所有包

conda install requests           // 安装requests包

conda remove requests            //卸载requets包

conda remove -n learn --all      // 删除learn环境及下属所有包

conda update requests            //更新requests包

conda env export > environment.yaml     // 导出当前环境的包信息

conda env create -f environment.yaml    // 用配置文件创建新的虚拟环境
```

# Anaconda2和Anaconda3的区别

目前已知的区别在于base环境的python版本。当安装anaconda2时，base环境默认是python2，而anaconda的默认base环境是python3。

pip下载python库太慢的换源方法：
> https://zhuanlan.zhihu.com/p/46975553

```bash
# 加入 -i 选项
pip install django -i https://pypi.tuna.tsinghua.edu.cn/simple
```

# 参考资料

https://www.jianshu.com/p/eaee1fadc1e9