## Road to Recovery - ACL完全断裂半月板复杂裂1.5年笔记

#### 受伤当天
2021/12/11的Mammoth mountain，温度零下10-15度左右，中午前后风非常大，吹的缆车摇到45度，能见度不佳，下着零星的小雪，雪道表面比较冰。我当时打算滑chair 23的招牌Dropout Chute和Wipeout Chute. 早上在相似难度的Gravy Chute热身两趟后感觉状态非常好，于是就决定不用jump turn (很耗体能)，随意滑下去。从切入到前几个弯都非常顺利，当时脑中想着mammoth双黑也不过如此，马上就能到山脚回酒店整理一波视频。就在一刹那，突然一个弯转的大了一点，失去了平衡，人还没反应过来就已经发现自己头朝下开始向山脚自由落体，42度的雪坡配合着强大的重力疯狂地牵扯着我的板子让我向下加速翻滚，没有任何办法能停下来。我当时觉得命可能要交代了。大概滚了200米，居然神奇地停了下来了，我爬起来一看发现只有一个板子掉了，想着运气不错捡回条命，于是把板子穿上打算继续往下滑，但总隐隐地感觉哪里有点不对。结果转第一个弯的时候发现左膝完全用不上力（应该是第一次摔的时候就已经把ACL搞断了)，左腿往后过伸就像没有了知觉一样，于是又开始了往下翻滚，这次觉得真的完了，出大事了。大概又滚了100米，发现已经快滚到了雪道最底部了。我站起来试图走回缆车站，被两个路人看到了叫了救援。于是我就被救援雪橇抬了下去。随时物品居然都都在，除了运动相机，它已经被永远地埋在mammoth雪山的一个角落了，再也找不到了。
当即腿就伸不直了，勉强可以走一点点路，但会非常疼，上楼也还勉强可以，但下楼完全不行。当时想着运气不错，这么可怕的事故似乎伤的还好。

#### Video Diffusion

1. Latent Video Diffusion Models for High-Fidelity Long Video Generation [Video Diffusion](https://arxiv.org/pdf/2211.13221.pdf)
2. MagicVideo: Efficient Video Generation With Latent Diffusion Models [Video Diffusion 2](https://arxiv.org/pdf/2211.11018.pdf)
3. Align your Latents: High-Resolution Video Synthesis with Latent Diffusion Models [Latent Video Diffusion](https://research.nvidia.com/labs/toronto-ai/VideoLDM/)



#### Architecture of Diffusion NeRF

<p align="center">
 <img src="https://github.com/efzero/PINER/blob/master/networks/Screen%20Shot%202023-07-20%20at%206.26.14%20PM.png?raw=true" width="1000" height="400">
</p>

<p align="center">
  <img src="https://github.com/efzero/PINER/blob/master/networks/Screen%20Shot%202023-07-20%20at%206.18.26%20PM.png?raw=true" width="500" height="400">
</p>



##### Results for Sparse-View Reconstruction

<p align="center">
 <img src="https://github.com/efzero/PINER/blob/master/networks/Screen%20Shot%202023-07-20%20at%206.48.24%20PM.png?raw=true" widht="1000" height="400">

 </p>


---

### This is a header

#### Some T-SQL Code

```tsql
SELECT This, [Is], A, Code, Block -- Using SSMS style syntax highlighting
    , REVERSE('abc')
FROM dbo.SomeTable s
    CROSS JOIN dbo.OtherTable o;
```

#### Some PowerShell Code

```powershell
Write-Host "This is a powershell Code block";

# There are many other languages you can use, but the style has to be loaded first

ForEach ($thing in $things) {
    Write-Output "It highlights it using the GitHub style"
}
```
