# TorchSharp在windows 11上安装运行  

## TorchSharpExamples (CUDA version)
CUDA version examples based on offical example project.
The original example project:  
https://github.com/dotnet/TorchSharpExamples?tab=MIT-1-ov-file
The orginal TorchSharp source code project:  
https://github.com/dotnet/TorchSharp

-----------------------------------------
## TorchSharpExamples示例项目  
先介绍一下TorchSharpExamples项目，这个工程项目很容易用，没有包含源码，直接可以build并运行。只是要注意Program.cs指定了从Desktop路径去加载训练数据（我运行的是CIFAR10），你可能需要修改一下路径，并且去网上下载CIFAR10适用于C/C++的数据集（选binary version）：  
`private readonly static string _dataset = "CIFAR10";
private readonly static string _dataLocation = Path.Join(Environment.GetEnvironmentVariable("USERPROFILE") , "Downloads", _dataset);`

示例项目默认是安装了CPU版本的nuget包，训练速度会比较慢，一个epoch要3分钟。
![image](https://github.com/user-attachments/assets/e8051491-64a1-45e1-aa21-06a131bea543)  

把默认安装的TorchSharp CPU版本的包删除，换上cuda版本的nuget。TorchVision只要安装在Examples.Utils项目。  
![image](https://github.com/user-attachments/assets/82ea8608-8554-4b7b-8a9d-f127550cde0c)  

这个似乎是CUDA被启用后的结果，batchsize被设置为CPU模式的8倍。速度快多了。（我用的是DELL G15 12700H+32GB+3070ti）：  
![image](https://github.com/user-attachments/assets/24d599aa-6a50-45eb-b1c8-4cb930a1065a)


-----------------------------------------
