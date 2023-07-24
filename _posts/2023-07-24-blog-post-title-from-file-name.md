# Road to Recovery - ACL完全断裂半月板复杂裂1.5年笔记

## 受伤当天 

2021/12/11的Mammoth mountain，温度零下10-15度左右，中午前后风非常大，吹的缆车摇到45度，能见度不佳，下着零星的小雪，雪道表面比较冰。我当时打算滑chair 23的招牌Dropout Chute和Wipeout Chute. 早上在相似难度的Gravy Chute热身两趟后感觉状态非常好，于是就决定不用jump turn (很耗体能)，随意滑下去。从切入到前几个弯都非常顺利，当时脑中想着mammoth双黑也不过如此，马上就能到山脚回酒店整理一波视频。<br>
就在一刹那，突然一个弯转的大了一点，失去了平衡，人还没反应过来就已经发现自己头朝下开始向山脚自由落体，42度的雪坡配合着强大的重力疯狂地牵扯着我的板子让我向下加速翻滚，没有任何办法能停下来。我当时觉得命可能要交代了。大概滚了200米，居然神奇地停了下来了，我爬起来一看发现只有一个板子掉了，想着运气不错捡回条命，于是把板子穿上打算继续往下滑，但总隐隐地感觉哪里有点不对。结果转第一个弯的时候发现左膝完全用不上力（应该是第一次摔的时候就已经把ACL搞断了)，左腿往后过伸就像没有了知觉一样，于是又开始了往下翻滚，这次觉得真的完了，出大事了。大概又滚了100米，发现已经快滚到了雪道最底部了。当即腿就伸不直了，勉强可以走一点点，但会挺疼。我站起来试图走回缆车站，被两个路人看到了叫了救援。于是我就被救援雪橇抬了下去。随时物品居然都都在，除了运动相机，它已经被永远地埋在mammoth雪山的一个角落了，再也找不到了。

## 受伤初期 

很感谢女朋友第二天就从从印第安纳飞过来照顾我，也很感谢热心的朋友们，一口气开了8个小时回到湾区，然后把我送回了家。睡觉很痛苦因为腿根本伸不直，X光显示胫骨平台有撕脱性骨折，医生认为大概率ACL(前叉韧带)断了，但是抱着侥幸的心理想着半月板应该没事，结果核磁结果显示了最糟的结果:ACL完全断裂，半月板复杂撕裂并有提篮样碎片移位卡着关节。这样的伤通常是要永久告别剧烈运动了。当时由于膝盖的角度受限，没法走路，出门在家全靠双拐，彻底体会到了残疾人的艰难，并且非常地痛恨浴缸这样的家具：为了满足一小部分喜欢泡澡的人给没法走路的人带来极大的不便。<br>
当我一月初去见主刀医生的时候，膝盖只能弯90度，并且伸不直。医生觉得情况比较严重，建议两期手术（第一期手术恢复关节活动度，处理半月板，第二期手术重建ACL).通常这样的伤不需要两个手术，我的术前情况比较严重，医生害怕术后效果不佳，于是提议保守两期处理。我问医生半月板撕裂还有救吗。医生说我来的时候已经伤后三周了可能有点晚，但他会try his best (Three weeks might be too late but I will try my best)。他说最糟情况可能是要切除大部分半月板。主刀医生希望能立即做手术。很多人会再去问几个医生之后决定，但我当时隐隐地感觉应该相信这个医生，于是毫不犹豫说没问题，过两天就做手术。

## 第一个手术 （半月板修复）

第一个手术写着是meniscectomy (半月板切除术), 也就是说医生觉得大概率会切半月板。之前从来没有做过全麻手术，听说会真切地体会到死亡。我术前两小时就躺在了手术床上，非常紧张，医生给了两针镇定剂。我还记得我清醒的时候问主刀医生最后一个问题：我之后还可以滑雪吗？他说Absolutely you can.之后在麻药注入之后我立刻失去了意识，醒来就像睡了个好觉，一看天已经黑了，男护士看到我醒了第一句话就是 "I got a great news for you. Dr.Abrams was able to fix your meniscus." 我非常的惊讶和喜悦，问他："Really? Is it a meniscus repair?". "Yes!""That's awesome!"随后护士又说"I had a best cure for you" 推着轮椅带我走向一楼的钢琴,弹了一小段，我也很开心，在轮椅上弹了千与千寻的Reprise, 这首曲子是千寻在鬼城历尽磨难，最后成功地找到了父母和回家的路时的bgm. 护士鼓了掌，觉得我弹的很好。



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
