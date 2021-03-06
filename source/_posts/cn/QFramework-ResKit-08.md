---
title: QFramework 使用指南 (2020) - Res Kit（8）小结与补充
iscopyright: true
comments: true
lang: cn
tags:
  - Unity
  - Framework
  - QFramework
  - QFramework.ResKit
  - AssetBundle
categories:
  - QFramework
abbrlink: qf_reskit_08
date: 2019-09-08 23:01:18
author: 凉鞋 | 凉鞋的笔记：liangxiegame.com
---


<center>
<a href="https://tdou.cc/cn/qf_reskit_07.html">上一阶段</a> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="https://tdou.cc/cn/qframework.html">回到总览</a> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</center>

在上一篇，我们了解了 从其他目录加载资源 的功能。

在这一片，我们做一个补充和总结。

## 补充
补充分为两部分，一部分是代码生成，另一部分是关于自定义扩展资源类型的预告。

### 代码生成 
Res Kit 是支持代码生成的，生成按钮的位置如下所示:
![image.png](http://file.liangxiegame.com/7a76c4e3-1baa-4366-9c8f-3335e311e499.png) 

点击生成代码即可，生成后结果如下。
![image.png](http://file.liangxiegame.com/0ea13581-4960-4bc8-bbf1-b49a03455271.png) 

生成了 QAssets 代码文件，代码内容如下:
``` csharp
namespace QAssetBundle
{
    
    public class Testobj_prefab
    {
        public const string BundleName = "testobj_prefab";
        public const string TESTOBJ = "testobj";
    }
    public class Testsprite_png
    {
        public const string BundleName = "testsprite_png";
        public const string TESTSPRITE = "testsprite";
    }
}

```

生成了代码，那么在写资源加载的代码的时候就会爽的飞起，如下图示:
![image.png](http://file.liangxiegame.com/7b8ae854-aafe-49d8-9318-5f7d1190c8cc.png) 

图中，给出了资源名字的提示。

这样就不容易出现字符串的拼写错误了。


### 自定义资源类型
我们在上一篇了解了 从 Resources 或从网络中加载资源，实际上，只要掌握 Res Kit 的内部原理，就非常容易扩展自己的资源类型，可以定制资源的加载、卸载、加载路径、同步、异步的逻辑，甚至是加载、卸载的生命周期也可以定制。

当然这部分内容需要笔者花很多的经历去写，目前，我们只掌握已有的加载方式即可。

## 总结
我们花了 7 篇文章，从各个方面了解了 Res Kit 套件。

现在做一个小的总结:
* Res Kit
  * 同步加载资源 ResLoader.LoadSync
  * 异步加载资源 ResLoader.Add2Load + LoadAsync
  * 加载 AB 资源:
    * ResLoader.LoadSync(assetName)
    * ResLoader.LoadSync(abName,assetName)
    * 支持异步(LoadAsync)
  * 加载 Resources 资源:
    * ResLoader.LoadSync("resources://" + assetPath);
    * 支持异步(LoadAsync)   
   * 加载网络图片
     * ResLoader.Add2Load("netimage:" + imageUrl,(succeed,res)=>{});
   * 开发阶段建议使用 模拟模式
   * 真机阶段建议使用 非模拟模式
   * 模拟模式 资源工作流
     * 标记 AB
     * 代码加载
   * 非模拟模式 资源工作流
     * 标记 AB（不推荐在非模拟模式下添加资源，建议在开发阶段添加资源）
     * 打 AB包
     * 代码加载
   * ResMgr.Init 需要在项目启动时调用一次
   * ResLoader 建议每个需要加载的脚本，都申请一个。

此篇的内容就这些。

* 转载请注明地址：凉鞋的笔记：liangxiegame.com。
* 任何问题欢迎到 QQ 群：623597263 交流。


<center>
<a href="https://tdou.cc/cn/qf_reskit_07.html">上一阶段</a> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="https://tdou.cc/cn/qframework.html">回到总览</a> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</center>
