# 可灵 Kling 4.0 提示词：X、fal.ai、kling4.video 和 Civitai 上收集的 275 条真实提示词

[English](README.md) · 简体中文 · [在 apimodels.app 上看带成片的版本](https://apimodels.app/zh/kling-4-0-prompts) · [在 GitHub Pages 上搜索、一键复制](https://apimodels.github.io/kling-4-0-prompts/)

本仓库收录 275 条可灵 Kling 4.0 视频提示词，来自 96 位作者和网站在 X（230 条）、fal.ai（27 条）、kling4.video（12 条）和 Civitai（6 条）上公开发布的内容，每条都逐字全文收录、署名作者，并附原帖链接。

说明：这个合集由 [apimodels.app](https://apimodels.app) 整理，我在这个 API 平台工作。apimodels.app 是多模型 API 平台，也提供 [Kling 4.0 的 API](https://apimodels.app/zh/models/kling-4.0)，API 能跑什么、不能跑什么，写在下面「[用 API 跑这些提示词](#用-api-跑这些提示词)」里。带成片、可以直接播放的在线版在 [apimodels.app 的 Kling 4.0 提示词库](https://apimodels.app/zh/kling-4-0-prompts)。

## 目录

- [电影感剧情](#电影感剧情)（54）
- [对白与口型](#对白与口型)（20）
- [动作与打斗](#动作与打斗)（47）
- [参考素材与 @ 点名](#参考素材与--点名)（22）
- [长片与多镜头](#长片与多镜头)（13）
- [动画与风格化](#动画与风格化)（36）
- [产品与广告](#产品与广告)（16）
- [手机实拍与社媒](#手机实拍与社媒)（28）
- [科幻与奇幻](#科幻与奇幻)（39）
- [这些提示词是怎么写的](#这些提示词是怎么写的)
- [用 API 跑这些提示词](#用-api-跑这些提示词)
- [怎么收集的](#怎么收集的)
- [出处、版权与许可](#出处版权与许可)

每条提示词在 [prompts/](prompts) 下有单独一页，写明作者、原帖、从哪里发现的、提示词的语言和长度，以及成片链接。全部 275 条也在 [data/prompts.json](data/prompts.json)，[index.html](index.html) 是可以搜索、筛选、一键复制的浏览页。

## 这些提示词是怎么写的

- **每份素材都用 @ 点名**：API 上的素材按它在请求里的位置编号:image_urls 里的是 @image_1、@image_2,video_urls 里的是 @video_1,帧是 @first_frame、@keyframe_1、@last_frame,elements 里的主体和 voices 里的音色用 @名字。提示词里每个 @ 都要对得上同一个请求里真有的素材,对不上的请求会在扣费前直接被拒。
- **「附上的图」要改成 @ 点名**：fal.ai 指南里不少提示词写的是「用 Video 1 的运镜,用附上的图片定场景」,离开那几个文件就跑不起来。在 API 上,把视频放进 video_urls、图片放进 image_urls,再按同样的顺序把说法改成 @video_1、@image_1。
- **角色交给具名主体来锁**：与其每句话都重新描述一遍那张脸,不如在 elements 里交一次:2 到 4 张不同角度的图、正面那张放第一,或者一段 3 到 8 秒、一镜到底的人物视频。之后她每次出场都写 @Mia。本库长提示词里反复强调「全程同一个人」,这一步就是在请求层面做同一件事。
- **声音关不掉,那就写清楚**：Kling 4.0 的声音没法关,所以效果好的提示词都把声音写出来:kling4.video 的例子结尾都有一行「Sound:」,台词放进引号并写明语种,比如 says in English: "Sorry, was that oat milk or almond?"。想让某个角色用指定的嗓音,Kling 4.0 用 voices 绑一段音频,Flash 用 elements[].voice_url。带参考视频时,keep_original_sound 可以保留它们的原声。
- **分镜写在正文里,时间要加得起来**：本库常见的写法,是在一条提示词里写「Shot 1 (0-5s):… Shot 2 (5-10s):…」。API 没有单独的分镜字段,这些分镜就是普通的提示词文字:每个镜头只放一个动作,所有时间段加起来要等于你请求的时长,3 到 30 秒(Flash 最多 20 秒)。
- **画幅和时长写进参数,别写在提示词里**：X 上的长提示词常常一开头就是「Format: 16:9, 30 seconds, 24fps, 1080p」,还有几条要 4K。在 API 上这些都是参数:duration、resolution(720p 或 1080p,没有 4K)和 aspect_ratio(auto、16:9、9:16、1:1、21:9)。在请求里设好,免得文字和参数打架。
- **定路线用关键帧,定长相用参考**：关键帧管镜头往哪走:一张首帧、最多 8 张中间帧、一张尾帧,总张数受时长限制,3 秒最多 4 张,9 秒及以上最多 10 张。参考素材管东西长什么样。两者不能放进同一个请求,Flash 只收首帧。

## 电影感剧情

| # | 提示词 | 作者 | 原帖 | 字符 | 成片 |
| --- | --- | --- | --- | --- | --- |
| KL014 | [雪日窗边相依的情侣](prompts/cinematic-story/KL014.md) | [@MahiraEhan](https://x.com/MahiraEhan) | [X](https://x.com/MahiraEhan/status/2118935687575593272) | 2138 | [视频](https://video.twimg.com/amplify_video/2118933715388624896/vid/avc1/1920x1080/aoabkD-PqZt8v18W.mp4?tag=29) |
| KL016 | [花园中为巨型布偶猫梳毛](prompts/cinematic-story/KL016.md) | [@itxsarmadd](https://x.com/itxsarmadd) | [X](https://x.com/itxsarmadd/status/2118572883878527376) | 2216 | [视频](https://video.twimg.com/amplify_video/2118572771966062592/vid/avc1/1280x720/b4Zb3CE5frJ3jIkL.mp4?tag=29) |
| KL026 | [女司机按下飞行按钮](prompts/cinematic-story/KL026.md) | [@AIwithSynthia](https://x.com/AIwithSynthia) | [X](https://x.com/AIwithSynthia/status/2113600946228138078) | 3523 | [视频](https://video.twimg.com/amplify_video/2113600898056474624/vid/avc1/1280x720/13nOC4GcJAKej57r.mp4?tag=29) |
| KL034 | [座头鲸跃出小船旁海面](prompts/cinematic-story/KL034.md) | [@umesh\_ai](https://x.com/umesh_ai) | [X](https://x.com/umesh_ai/status/2109174564307771477) | 1496 | [视频](https://video.twimg.com/amplify_video/2109174143891697664/vid/avc1/1280x720/XxctfSnIujkTatLv.mp4?tag=29) |
| KL054 | [窗边咖啡喜剧小剧场](prompts/cinematic-story/KL054.md) | [@MeenakshiYACS](https://x.com/MeenakshiYACS) | [X](https://x.com/MeenakshiYACS/status/2119681759256465716) | 2191 | [视频](https://video.twimg.com/amplify_video/2119681253255634944/vid/avc1/720x1280/dUb_zKHJBNhzYyTR.mp4?tag=29) |
| KL056 | [摩纳哥海岸警车追逐](prompts/cinematic-story/KL056.md) | [@Dheepanratnam](https://x.com/Dheepanratnam) | [X](https://x.com/Dheepanratnam/status/2118786119810580862) | 8289 | [视频](https://video.twimg.com/amplify_video/2118785368241623040/vid/avc1/1280x720/-mJ0eruJcM2NX3ek.mp4?tag=29) |
| KL067 | [母猫叼来蓝帽子](prompts/cinematic-story/KL067.md) | [@umesh\_ai](https://x.com/umesh_ai) | [X](https://x.com/umesh_ai/status/2106289723673313748) | 4248 | [视频](https://video.twimg.com/amplify_video/2106289577518563328/vid/avc1/1280x720/0_PDBSRac6RoIx4y.mp4?tag=29) |
| KL082 | [炼金术师召唤火焰精灵](prompts/cinematic-story/KL082.md) | [@shikoba\_86](https://x.com/shikoba_86) | [X](https://x.com/shikoba_86/status/2111101132223205663) | 1116 | [视频](https://video.twimg.com/amplify_video/2111100882435653633/vid/avc1/1920x1080/2fQSIAG2EuCVcNXF.mp4?tag=29) |
| KL083 | [露天体育场现场演唱会](prompts/cinematic-story/KL083.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2111471577522921832) | 6237 | [视频](https://video.twimg.com/amplify_video/2111468393941397504/vid/avc1/1920x1080/Ub5RVD1-dPaDJPBp.mp4?tag=29) |
| KL086 | [雨夜腊肠犬快递员](prompts/cinematic-story/KL086.md) | [@bmx\_ai13](https://x.com/bmx_ai13) | [X](https://x.com/bmx_ai13/status/2113727192639459801) | 4774 | [视频](https://video.twimg.com/amplify_video/2113726736806588416/vid/avc1/1280x720/aHn77eWcFL9uCXeT.mp4?tag=29) |
| KL097 | [粉色造型人物特写](prompts/cinematic-story/KL097.md) | [@ai\_artworkgen](https://x.com/ai_artworkgen) | [X](https://x.com/ai_artworkgen/status/2113730057071890909) | 473 | [视频](https://video.twimg.com/amplify_video/2113729718209884160/vid/avc1/1244x1660/Jb_-i3mDQX-ZktEU.mp4?tag=29) |
| KL098 | [女子奔逃黑木森林](prompts/cinematic-story/KL098.md) | [@EndFolding79421](https://x.com/EndFolding79421) | [X](https://x.com/EndFolding79421/status/2110781238374207618) | 2106 | [视频](https://video.twimg.com/amplify_video/2110776422536974336/vid/avc1/1920x1080/e3CK1SUJR-OGThkp.mp4?tag=29) |
| KL101 | [鳄面男子喂乌龟](prompts/cinematic-story/KL101.md) | [morg2625275](https://civitai.com/user/morg2625275) | [Civitai](https://civitai.com/images/147959773) | 1789 | [视频](https://image.civitai.com/xG1nkqKTMzGDvpLrqFT7WA/515adcd2-f192-4bb2-8767-1c302b473a8f/original=true/515adcd2-f192-4bb2-8767-1c302b473a8f.mp4) |
| KL103 | [圣诞恐龙服装浪漫喜剧](prompts/cinematic-story/KL103.md) | [@bmx\_ai13](https://x.com/bmx_ai13) | [X](https://x.com/bmx_ai13/status/2115657376309354759) | 4703 | [视频](https://video.twimg.com/amplify_video/2115542571221164032/vid/avc1/1920x1080/FTDCZI-gXKuQb10E.mp4?tag=29) |
| KL111 | [巨猫观看模型火车](prompts/cinematic-story/KL111.md) | [@Sleaper\_](https://x.com/Sleaper_) | [X](https://x.com/Sleaper_/status/2121150374539059502) | 1917 | [视频](https://video.twimg.com/amplify_video/2121150232570322944/vid/avc1/1280x1440/AwGDNpKZzqN9xxAY.mp4?tag=29) |
| KL112 | [长椅持玫瑰女子](prompts/cinematic-story/KL112.md) | [@EndFolding79421](https://x.com/EndFolding79421) | [X](https://x.com/EndFolding79421/status/2112371662452601207) | 1289 | [视频](https://video.twimg.com/amplify_video/2112370359307575296/vid/avc1/1924x1076/1wsskOdx1LegBeI1.mp4?tag=29) |
| KL113 | [日落屋顶踢踏舞](prompts/cinematic-story/KL113.md) | [@EndFolding79421](https://x.com/EndFolding79421) | [X](https://x.com/EndFolding79421/status/2110785773456838793) | 785 | [视频](https://video.twimg.com/amplify_video/2110784023521878016/vid/avc1/1920x1080/0cbXykV2h9gzMQhq.mp4?tag=29) |
| KL117 | [露西下班夜行回家](prompts/cinematic-story/KL117.md) | [@EndFolding79421](https://x.com/EndFolding79421) | [X](https://x.com/EndFolding79421/status/2110800090897973405) | 2441 | [视频](https://video.twimg.com/amplify_video/2110799519675830272/vid/avc1/1920x1080/FkzAe-IjFF8TJXsE.mp4?tag=29) |
| KL124 | [金雕草原追踪飞行](prompts/cinematic-story/KL124.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2104742876584218720) | 793 | [视频](https://video.twimg.com/amplify_video/2104742780660588544/vid/avc1/1920x1080/6cZN4k0r5uTU3R1R.mp4?tag=29) |
| KL139 | [黑色电影侦探点烟](prompts/cinematic-story/KL139.md) | [@sebatheepan](https://x.com/sebatheepan) | [X](https://x.com/sebatheepan/status/2104653412738666699) | 476 | [视频](https://video.twimg.com/amplify_video/2104652399608520704/vid/avc1/1280x720/9TbQR3m-a6yW3tmM.mp4?tag=29) |
| KL140 | [无人机飞向海浪悬崖](prompts/cinematic-story/KL140.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2112636119179575471) | 250 | [视频](https://video.twimg.com/amplify_video/2112636065391755264/vid/avc1/1920x1080/GCjzkaslMJZjm9T_.mp4?tag=16) |
| KL142 | [FPV无人机穿越仓库](prompts/cinematic-story/KL142.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2112636228931879403) | 370 | [视频](https://video.twimg.com/amplify_video/2112636173432832000/vid/avc1/1920x1080/e2-q9HxAJlYch3gM.mp4?tag=16) |
| KL143 | [水下女子面部特写](prompts/cinematic-story/KL143.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2115443305244946606) | 539 | [视频](https://video.twimg.com/amplify_video/2115443276551774208/vid/avc1/1920x1080/JQSv66K7HsxohCSo.mp4?tag=16) |
| KL144 | [圣殿骑士遇现代海军陆战](prompts/cinematic-story/KL144.md) | [coltonbi](https://civitai.com/user/coltonbi) | [Civitai](https://civitai.com/images/148845224) | 153 | [视频](https://image.civitai.com/xG1nkqKTMzGDvpLrqFT7WA/5af40e31-6797-4eec-84c6-b877599a6470/original=true/5af40e31-6797-4eec-84c6-b877599a6470.mp4) |
| KL148 | [公园长椅好友与狗](prompts/cinematic-story/KL148.md) | [@shikoba\_86](https://x.com/shikoba_86) | [X](https://x.com/shikoba_86/status/2111760138214293935) | 1830 | [视频](https://video.twimg.com/amplify_video/2111759618489597952/vid/avc1/1920x1080/7xn17mCK6wMQ66Yl.mp4?tag=29) |
| KL149 | [画室画笔连续镜头](prompts/cinematic-story/KL149.md) | [@sebatheepan](https://x.com/sebatheepan) | [X](https://x.com/sebatheepan/status/2104653416123551799) | 495 | [视频](https://video.twimg.com/amplify_video/2104652961645281280/vid/avc1/1280x720/AqZHEeIPLe85wX3s.mp4?tag=29) |
| KL154 | [微笑走向阳光门廊](prompts/cinematic-story/KL154.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2115443340883951720) | 235 | [视频](https://video.twimg.com/amplify_video/2115443318540947456/vid/avc1/1920x1080/5fwZkfFnzydYWDmh.mp4?tag=16) |
| KL156 | [雨滴脸庞烟花倒影](prompts/cinematic-story/KL156.md) | [InRioIstEsVollBio](https://civitai.com/user/InRioIstEsVollBio) | [Civitai](https://civitai.com/images/147571039) | 191 | [视频](https://image.civitai.com/xG1nkqKTMzGDvpLrqFT7WA/319362ad-3535-431e-bbd7-09e77d8c6b9f/original=true/319362ad-3535-431e-bbd7-09e77d8c6b9f.mp4) |
| KL163 | [岩石地上的小狗特写](prompts/cinematic-story/KL163.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 715 | [视频](https://v3b.fal.media/files/b/0aaf4d75/UlTSaTK6fXPjwPk9FPiop_86a7fce6addd5a588927ecab74be66149235ca8265ede8d97741362048aeee71.mp4) |
| KL166 | [红色跑车疾驰镜头](prompts/cinematic-story/KL166.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 453 | [视频](https://v3b.fal.media/files/b/0aaf4d92/ue2afsTMnkoeqPxZoeADM_61ef61635eebee715cb6ccd247c85a34dd4f904a255a5da82c00f91e41f82061.mp4) |
| KL178 | [老人吐槽人工智能](prompts/cinematic-story/KL178.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 28 | [视频](https://v3b.fal.media/files/b/0aaf4de2/eB2oq3ayoe10GxcL4-cyl_18beafe53e2a4fe4cf4b8cfb789ed7b32fbf943396d52f357931a2bcad4fa092.mp4) |
| KL179 | [黄昏街头老友重逢](prompts/cinematic-story/KL179.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 531 | [视频](https://v3b.fal.media/files/b/0aaf4de2/2CIGycIf2Mv2xyEQEcBXI_04843fffb8d1cefc62bd70c68767b64e048a5ef8bec49b19d17381ebb9f4b07a.mp4) |
| KL180 | [废弃走廊中的求生者](prompts/cinematic-story/KL180.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 814 | [视频](https://v3b.fal.media/files/b/0aaf4dd3/b9KC9AjCHPNWfDvXXM3-k_965472f316ae1508c4d599f20afd8aa43fb2acb3f4db42b63bebb32a6523b1c9.mp4) |
| KL192 | [维京长船风暴航行](prompts/cinematic-story/KL192.md) | [@PixVerse](https://x.com/PixVerse) | [X](https://x.com/PixVerse/status/2115126706935902551) | 22008 | — |
| KL193 | [月夜阳台飞吻星尘](prompts/cinematic-story/KL193.md) | [@art\_muse](https://x.com/art_muse) | [X](https://x.com/art_muse/status/2115398082779115973) | 1535 | — |
| KL202 | [船具店女店主夜归](prompts/cinematic-story/KL202.md) | [@sebatheepan](https://x.com/sebatheepan) | [X](https://x.com/sebatheepan/status/2113234965236449310) | 4540 | — |
| KL209 | [背包客雨林遇美洲豹](prompts/cinematic-story/KL209.md) | [@PixVerse](https://x.com/PixVerse) | [X](https://x.com/PixVerse/status/2115760876804604363) | 1949 | — |
| KL210 | [骑士夜赴哥特城堡](prompts/cinematic-story/KL210.md) | [@amynys](https://x.com/amynys) | [X](https://x.com/amynys/status/2116145595618566149) | 2234 | — |
| KL211 | [地铁站小猫对峙](prompts/cinematic-story/KL211.md) | [@openclipsai](https://x.com/openclipsai) | [X](https://x.com/openclipsai/status/2117243941045059656) | 1400 | — |
| KL215 | [暗巷门口的血色外套女人](prompts/cinematic-story/KL215.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2116621038180339741) | 1045 | — |
| KL220 | [浪人武士史诗预告](prompts/cinematic-story/KL220.md) | [@NigelWatsonTFTC](https://x.com/NigelWatsonTFTC) | [X](https://x.com/NigelWatsonTFTC/status/2111445384128069747) | 6323 | — |
| KL222 | [布列塔尼海岸小径对话](prompts/cinematic-story/KL222.md) | [@EricKerArt](https://x.com/EricKerArt) | [X](https://x.com/EricKerArt/status/2111110194516095384) | 2568 | — |
| KL228 | [俯冲进入设计商店](prompts/cinematic-story/KL228.md) | [@openclipsai](https://x.com/openclipsai) | [X](https://x.com/openclipsai/status/2115835395451543689) | 2082 | — |
| KL230 | [雨中屋顶芭蕾舞者](prompts/cinematic-story/KL230.md) | [@openclipsai](https://x.com/openclipsai) | [X](https://x.com/openclipsai/status/2116210866886492458) | 1510 | — |
| KL235 | [海岸沼泽火箭发射](prompts/cinematic-story/KL235.md) | [@sebatheepan](https://x.com/sebatheepan) | [X](https://x.com/sebatheepan/status/2113187765944779146) | 4818 | — |
| KL240 | [稻草人追逐乌鸦](prompts/cinematic-story/KL240.md) | [@SocialSight](https://x.com/SocialSight) | [X](https://x.com/SocialSight/status/2116561296485138837) | 1077 | — |
| KL243 | [酒吧香槟塔倾倒瞬间](prompts/cinematic-story/KL243.md) | [@openclipsai](https://x.com/openclipsai) | [X](https://x.com/openclipsai/status/2118758388649574819) | 956 | — |
| KL244 | [FPV无人机贴海追浪](prompts/cinematic-story/KL244.md) | [@openclipsai](https://x.com/openclipsai) | [X](https://x.com/openclipsai/status/2119092031192498613) | 1652 | — |
| KL246 | [雨后大阪小巷快递员](prompts/cinematic-story/KL246.md) | [kling4.video](https://kling4.video) | [kling4.video](https://kling4.video/prompts) | 403 | — |
| KL252 | [手工包饺子特写](prompts/cinematic-story/KL252.md) | [kling4.video](https://kling4.video) | [kling4.video](https://kling4.video/prompts) | 271 | — |
| KL253 | [冰川潟湖航拍](prompts/cinematic-story/KL253.md) | [kling4.video](https://kling4.video) | [kling4.video](https://kling4.video/prompts) | 259 | — |
| KL254 | [粗野主义图书馆推进](prompts/cinematic-story/KL254.md) | [kling4.video](https://kling4.video) | [kling4.video](https://kling4.video/prompts) | 300 | — |
| KL258 | [风暴潮猛击海堤](prompts/cinematic-story/KL258.md) | [@sebatheepan](https://x.com/sebatheepan) | [X](https://x.com/sebatheepan/status/2113038301154164960) | 6957 | — |
| KL269 | [慷慨贵族喜剧场景](prompts/cinematic-story/KL269.md) | [@airina\_xyz](https://x.com/airina_xyz) | [X](https://x.com/airina_xyz/status/2115476986751860751) | 3269 | — |

## 对白与口型

| # | 提示词 | 作者 | 原帖 | 字符 | 成片 |
| --- | --- | --- | --- | --- | --- |
| KL012 | [三种情绪肖像表演](prompts/dialogue-lipsync/KL012.md) | [@azed\_ai](https://x.com/azed_ai) | [X](https://x.com/azed_ai/status/2108924733588906180) | 6244 | [视频](https://video.twimg.com/amplify_video/2108924703683522560/vid/avc1/1280x720/vwXhvCPDX66vM1G4.mp4?tag=16) |
| KL028 | [女孩夜骑森林低语](prompts/dialogue-lipsync/KL028.md) | [@MahiraEhan](https://x.com/MahiraEhan) | [X](https://x.com/MahiraEhan/status/2114671326413701226) | 691 | [视频](https://video.twimg.com/amplify_video/2114670563952082944/vid/avc1/720x1280/eDXCxCu5F42yn6CK.mp4?tag=29) |
| KL033 | [黑帮老板怒斥信使](prompts/dialogue-lipsync/KL033.md) | [@MayorKingAI](https://x.com/MayorKingAI) | [X](https://x.com/MayorKingAI/status/2111902123520930061) | 9920 | [视频](https://video.twimg.com/amplify_video/2111902083398172672/vid/avc1/1920x1080/t85NioY91qHTv3Od.mp4?tag=16) |
| KL036 | [夜路失恋倾诉](prompts/dialogue-lipsync/KL036.md) | [@genel\_ai](https://x.com/genel_ai) | [X](https://x.com/genel_ai/status/2104595625379823855) | 2393 | [视频](https://video.twimg.com/amplify_video/2104591885327355904/vid/avc1/1920x1080/bsTSeS1LMdY3Ynm-.mp4?tag=29) |
| KL058 | [未来脱口秀对话女机器人](prompts/dialogue-lipsync/KL058.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2112833687502913915) | 1141 | [视频](https://video.twimg.com/amplify_video/2112832848407281664/vid/avc1/1920x1080/UWUcf5-Nd0QWtBCU.mp4?tag=29) |
| KL063 | [咖啡馆双人对话特写](prompts/dialogue-lipsync/KL063.md) | [@tanabe\_fragm](https://x.com/tanabe_fragm) | [X](https://x.com/tanabe_fragm/status/2110887676832543125) | 1692 | [视频](https://video.twimg.com/amplify_video/2110887184144506880/vid/avc1/1920x1080/gqbYU3ANQEQiq7l5.mp4?tag=29) |
| KL069 | [猫咪主播街头边走边聊](prompts/dialogue-lipsync/KL069.md) | [@AIwithSarah\_](https://x.com/AIwithSarah_) | [X](https://x.com/AIwithSarah_/status/2107724687984013347) | 1002 | [视频](https://video.twimg.com/amplify_video/2107724583063392256/vid/avc1/1076x1920/opxCZQMIL0M_FaPa.mp4?tag=29) |
| KL077 | [女子对镜头说话](prompts/dialogue-lipsync/KL077.md) | [5XTzQ](https://civitai.com/user/5XTzQ) | [Civitai](https://civitai.com/images/148054456) | 1761 | [视频](https://image.civitai.com/xG1nkqKTMzGDvpLrqFT7WA/4a7d8c65-b50e-4b34-ac5b-4f2ab967188d/original=true/4a7d8c65-b50e-4b34-ac5b-4f2ab967188d.mp4) |
| KL088 | [雨夜末班渡轮上的告白](prompts/dialogue-lipsync/KL088.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2104742167629435105) | 2197 | [视频](https://video.twimg.com/amplify_video/2104741972267184128/vid/avc1/1920x1080/tHT9BmvrRsR7ufmZ.mp4?tag=29) |
| KL094 | [冬夜河边分手对话](prompts/dialogue-lipsync/KL094.md) | [@tanabe\_fragm](https://x.com/tanabe_fragm) | [X](https://x.com/tanabe_fragm/status/2110893614671040886) | 1917 | [视频](https://video.twimg.com/amplify_video/2110893349444153344/vid/avc1/1080x1920/dSTwc-Y2f8LKrFX8.mp4?tag=29) |
| KL114 | [凌晨三点姐妹厨房坦白](prompts/dialogue-lipsync/KL114.md) | [@sebatheepan](https://x.com/sebatheepan) | [X](https://x.com/sebatheepan/status/2104706256963244436) | 2468 | [视频](https://video.twimg.com/amplify_video/2104706027337678848/vid/avc1/1280x720/513Ysks5HPHZdYxN.mp4?tag=29) |
| KL119 | [中世纪税务办公室喜剧](prompts/dialogue-lipsync/KL119.md) | [@airina\_xyz](https://x.com/airina_xyz) | [X](https://x.com/airina_xyz/status/2116549465003995238) | 1958 | [视频](https://video.twimg.com/amplify_video/2116549420124975104/vid/avc1/1920x1080/U4_L_Tug6WPl0fNm.mp4?tag=16) |
| KL127 | [健身房哑铃训练自拍](prompts/dialogue-lipsync/KL127.md) | [@RDV1113](https://x.com/RDV1113) | [X](https://x.com/RDV1113/status/2120439367537745972) | 1110 | [视频](https://video.twimg.com/amplify_video/2120439285782388736/vid/avc1/1080x1350/mdByUmT6zJu7um1U.mp4?tag=29) |
| KL134 | [雨天咖啡馆对话](prompts/dialogue-lipsync/KL134.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2112635851029221492) | 295 | [视频](https://video.twimg.com/amplify_video/2112635819257454592/vid/avc1/1920x1080/bUSOIQsIBb_XtQbc.mp4?tag=16) |
| KL170 | [录音棚说唱表演特写](prompts/dialogue-lipsync/KL170.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 409 | [视频](https://v3b.fal.media/files/b/0aaf4d8b/F9g22mVbrzwGS_x999AWX_35a0ed1536aecf56ad148e9fd39ebfa42674e87efe668ad74fafe429b4519eb2.mp4) |
| KL195 | [狐狸与猫头鹰书房对话](prompts/dialogue-lipsync/KL195.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2105981906869199107) | 899 | — |
| KL197 | [深夜厨房失业坦白戏](prompts/dialogue-lipsync/KL197.md) | [@MayorKingAI](https://x.com/MayorKingAI) | [X](https://x.com/MayorKingAI/status/2111427314248774100) | 7217 | — |
| KL198 | [外星中转站警告](prompts/dialogue-lipsync/KL198.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2110755047910900091) | 882 | — |
| KL201 | [恶魔伊芙客厅对话](prompts/dialogue-lipsync/KL201.md) | [@TheRogueA1](https://x.com/TheRogueA1) | [X](https://x.com/TheRogueA1/status/2111424984631460196) | 3536 | — |
| KL249 | [咖啡馆点单对话](prompts/dialogue-lipsync/KL249.md) | [kling4.video](https://kling4.video) | [kling4.video](https://kling4.video/prompts) | 374 | — |

## 动作与打斗

| # | 提示词 | 作者 | 原帖 | 字符 | 成片 |
| --- | --- | --- | --- | --- | --- |
| KL002 | [韩式餐厅近身激斗](prompts/action-fight/KL002.md) | [@Just\_sharon7](https://x.com/Just_sharon7) | [X](https://x.com/Just_sharon7/status/2118728208640291057) | 8612 | [视频](https://video.twimg.com/amplify_video/2118727503024136192/vid/avc1/1280x720/mOAiU3vdsrX_mozu.mp4?tag=29) |
| KL006 | [冰盾停车场战斗](prompts/action-fight/KL006.md) | [@itxabdullaa](https://x.com/itxabdullaa) | [X](https://x.com/itxabdullaa/status/2118202412058198119) | 2280 | [视频](https://video.twimg.com/amplify_video/2118202360740917248/vid/avc1/1280x720/8WIcD6LuhDSrtyyf.mp4?tag=29) |
| KL007 | [浴巾女英雄浴室剑战](prompts/action-fight/KL007.md) | [@itxabdullaa](https://x.com/itxabdullaa) | [X](https://x.com/itxabdullaa/status/2116502720823865475) | 1923 | [视频](https://video.twimg.com/amplify_video/2116502665157083136/vid/avc1/1080x720/bPkNnFIrrdUR09mh.mp4?tag=29) |
| KL008 | [莉卡战怪物大军](prompts/action-fight/KL008.md) | [@itxsarmadd](https://x.com/itxsarmadd) | [X](https://x.com/itxsarmadd/status/2118222132597657636) | 3156 | [视频](https://video.twimg.com/amplify_video/2118222074233909248/vid/avc1/1280x720/ijiB8J6E7tUfKbv7.mp4?tag=29) |
| KL010 | [战术射击游戏实况](prompts/action-fight/KL010.md) | [@higgsfield\_ai](https://x.com/higgsfield_ai) | [X](https://x.com/higgsfield_ai/status/2110905436371370009) | 3775 | [视频](https://video.twimg.com/amplify_video/2110904434981298176/vid/avc1/1920x1080/C35k5IEG4veU9154.mp4?tag=29) |
| KL011 | [草原超能力对决](prompts/action-fight/KL011.md) | [@itxabdullaa](https://x.com/itxabdullaa) | [X](https://x.com/itxabdullaa/status/2117966196683456710) | 2235 | [视频](https://video.twimg.com/amplify_video/2117966133643169792/vid/avc1/1280x720/AV4xjhDw45r8-x4U.mp4?tag=29) |
| KL032 | [僵尸雷电战场战斗](prompts/action-fight/KL032.md) | [@RizwanAly07](https://x.com/RizwanAly07) | [X](https://x.com/RizwanAly07/status/2112516449080348958) | 2656 | [视频](https://video.twimg.com/amplify_video/2112514991815540736/vid/avc1/1280x720/53HuficfwUYM5KWm.mp4?tag=29) |
| KL039 | [特种部队夜间突袭](prompts/action-fight/KL039.md) | [@iamrealsnow](https://x.com/iamrealsnow) | [X](https://x.com/iamrealsnow/status/2115300539902869533) | 2905 | [视频](https://video.twimg.com/amplify_video/2115300476023619584/vid/avc1/1280x720/i0TMyYIGUyXTuCFU.mp4?tag=29) |
| KL042 | [武士持刀连击士兵](prompts/action-fight/KL042.md) | [@itxabdullaa](https://x.com/itxabdullaa) | [X](https://x.com/itxabdullaa/status/2108154459268448461) | 2934 | [视频](https://video.twimg.com/amplify_video/2108154380474253312/vid/avc1/1280x720/tUN6SCCoJmjSYK8B.mp4?tag=29) |
| KL050 | [异星巨环下的沙漠战场](prompts/action-fight/KL050.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2114331347871469773) | 933 | [视频](https://video.twimg.com/amplify_video/2114330414286286849/vid/avc1/1280x720/8mcGFLA9CfjKncRT.mp4?tag=29) |
| KL059 | [面具战士对决死神](prompts/action-fight/KL059.md) | [@fromjtown](https://x.com/fromjtown) | [X](https://x.com/fromjtown/status/2112967291608666539) | 3900 | [视频](https://video.twimg.com/amplify_video/2112967044911996928/vid/avc1/3840x2160/PyNNzjy6oQGUggAi.mp4?tag=29) |
| KL060 | [骑士死守城堡大门](prompts/action-fight/KL060.md) | [@AiwithBloodline](https://x.com/AiwithBloodline) | [X](https://x.com/AiwithBloodline/status/2112796958045896801) | 2026 | [视频](https://video.twimg.com/amplify_video/2112796465299124224/vid/avc1/1280x720/URTTA0CfuKXeOM6t.mp4?tag=29) |
| KL061 | [直升机逃离火海平台](prompts/action-fight/KL061.md) | [@umesh\_ai](https://x.com/umesh_ai) | [X](https://x.com/umesh_ai/status/2108059420295102469) | 2549 | [视频](https://video.twimg.com/amplify_video/2108059327508729856/vid/avc1/1280x720/wKznvGz7PE9p9zEK.mp4?tag=29) |
| KL062 | [红黑跑车街头追逐](prompts/action-fight/KL062.md) | [@PromptSin](https://x.com/PromptSin) | [X](https://x.com/PromptSin/status/2111042013210825211) | 3613 | [视频](https://video.twimg.com/amplify_video/2111041977894797313/vid/avc1/1280x720/H_6xYpQX13XdhSuJ.mp4?tag=16) |
| KL064 | [清洁工大战银行劫匪](prompts/action-fight/KL064.md) | [@MayorKingAI](https://x.com/MayorKingAI) | [X](https://x.com/MayorKingAI/status/2104974096513872227) | 2068 | [视频](https://video.twimg.com/amplify_video/2104974061969584129/vid/avc1/1280x720/DFQT-krMlOo7t7z6.mp4?tag=16) |
| KL074 | [骑士逃离钢铁巨像](prompts/action-fight/KL074.md) | [@itsPixieVerse](https://x.com/itsPixieVerse) | [X](https://x.com/itsPixieVerse/status/2121975659484586290) | 4110 | [视频](https://video.twimg.com/amplify_video/2121973568808591360/vid/avc1/3380x1440/3s-PSt1VWJpFfJcp.mp4?tag=29) |
| KL078 | [两名女子徒手搏斗](prompts/action-fight/KL078.md) | [@boke\_ai](https://x.com/boke_ai) | [X](https://x.com/boke_ai/status/2112740231497859258) | 2646 | [视频](https://video.twimg.com/amplify_video/2112737360068894720/vid/avc1/1280x720/LwHo0kjhhcSAXoUY.mp4?tag=29) |
| KL081 | [城市跑酷极限跳跃](prompts/action-fight/KL081.md) | [@Ayu\_AI\_0912](https://x.com/Ayu_AI_0912) | [X](https://x.com/Ayu_AI_0912/status/2104860919058862373) | 1103 | [视频](https://video.twimg.com/amplify_video/2104860865417854977/vid/avc1/1280x720/JKjhTDN5jykChEdL.mp4?tag=29) |
| KL090 | [高速接吻格斗对决](prompts/action-fight/KL090.md) | [@misakin883](https://x.com/misakin883) | [X](https://x.com/misakin883/status/2113459306096173120) | 2270 | [视频](https://video.twimg.com/amplify_video/2113458537561284608/vid/avc1/1280x720/w3kyDaQb1V5oq3GK.mp4?tag=29) |
| KL099 | [跑酷者飞跃霓虹夜市](prompts/action-fight/KL099.md) | [@EndFolding79421](https://x.com/EndFolding79421) | [X](https://x.com/EndFolding79421/status/2110790580678574391) | 582 | [视频](https://video.twimg.com/amplify_video/2110789603237982208/vid/avc1/1920x1080/uVzvZeQtGYPwW-IW.mp4?tag=29) |
| KL104 | [竞技英雄射击游戏画面](prompts/action-fight/KL104.md) | [@ImaStudio\_ai](https://x.com/ImaStudio_ai) | [X](https://x.com/ImaStudio_ai/status/2110942886791647349) | 8579 | [图片](https://pbs.twimg.com/media/HUuTQ05akAANBTs.jpg?name=orig) |
| KL107 | [夜市间谍追逐](prompts/action-fight/KL107.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2104743085087560174) | 2048 | [视频](https://video.twimg.com/amplify_video/2104743016938213376/vid/avc1/1920x1080/SXTCXUlUfQQ36NUR.mp4?tag=29) |
| KL118 | [多镜头汽车漂移](prompts/action-fight/KL118.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2104743218722267597) | 50 | [视频](https://video.twimg.com/amplify_video/2104743157590052864/vid/avc1/1920x1080/vw5V37hYXrHqN2kJ.mp4?tag=29) |
| KL120 | [1981森林追杀](prompts/action-fight/KL120.md) | [@EndFolding79421](https://x.com/EndFolding79421) | [X](https://x.com/EndFolding79421/status/2116238431307157751) | 3819 | [视频](https://video.twimg.com/amplify_video/2116236875992006656/vid/avc1/1920x1080/jbHdyPoqJSD0EleG.mp4?tag=29) |
| KL121 | [滑板少年穿越公园](prompts/action-fight/KL121.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2111471588256207357) | 887 | [视频](https://video.twimg.com/amplify_video/2111470282657484800/vid/avc1/1920x1080/pDNs8JHtU5GQsvey.mp4?tag=29) |
| KL123 | [丛林持刀追逐奔跑](prompts/action-fight/KL123.md) | [@Sleaper\_](https://x.com/Sleaper_) | [X](https://x.com/Sleaper_/status/2122614457712984403) | 2648 | [视频](https://video.twimg.com/amplify_video/2122614367761952768/vid/avc1/1920x2160/r0YBeMR9djl7jGEs.mp4?tag=29) |
| KL135 | [雨夜屋顶雷火对决](prompts/action-fight/KL135.md) | [@tirtaVEX](https://x.com/tirtaVEX) | [X](https://x.com/tirtaVEX/status/2114267036046221716) | 1051 | [视频](https://video.twimg.com/amplify_video/2114264218623201280/vid/avc1/1920x1080/h4qbdW7GFd1JUJuh.mp4?tag=29) |
| KL137 | [一战双翼机空中追逐](prompts/action-fight/KL137.md) | [@PromptSin](https://x.com/PromptSin) | [X](https://x.com/PromptSin/status/2112499136620810684) | 2987 | [图片](https://pbs.twimg.com/media/HVEaxLRbwAAG8iB.jpg?name=orig) |
| KL145 | [黑白黑色电影警车追缉](prompts/action-fight/KL145.md) | [@PromptSin](https://x.com/PromptSin) | [X](https://x.com/PromptSin/status/2113216352832061872) | 2597 | [图片](https://pbs.twimg.com/media/HVOnEaIaEAArbya.jpg?name=orig) |
| KL153 | [拳击手三连击打靶](prompts/action-fight/KL153.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2112636052280365205) | 302 | [视频](https://video.twimg.com/amplify_video/2112636012186996736/vid/avc1/1920x1080/nhicE7rLQWJ3i4Un.mp4?tag=16) |
| KL159 | [丛林平台女子对决](prompts/action-fight/KL159.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 1089 | [视频](https://v3b.fal.media/files/b/0aaf4d96/jaH1Kh53uM44WJbxaI0Fc_3f043ce42d80cf4164f8dc153766f7a4205c9502bd65a06ee14edaf5e69d3b73.mp4) |
| KL167 | [篮球运动员强力扣篮](prompts/action-fight/KL167.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 346 | [视频](https://v3b.fal.media/files/b/0aaf4d98/wL8ZsQovsQfNZkR9vBzbJ_21c9adc38f37acf645241953586abf1b80cccc4d96d3f206328116f54013d66d.mp4) |
| KL182 | [道馆空手道对打](prompts/action-fight/KL182.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 502 | [视频](https://v3b.fal.media/files/b/0aaf4dd9/u7PnpD0cgoBjp0o9_ceUO_9e9fe5469d2e00673f0d312d9ed8a799a68f9b7e98526027e414bcb0d845b72a.mp4) |
| KL186 | [大逃杀第一人称游戏画面](prompts/action-fight/KL186.md) | [@AI\_\_TSUBAKI](https://x.com/AI__TSUBAKI) | [X](https://x.com/AI__TSUBAKI/status/2110918165706498200) | 9807 | [图片](https://pbs.twimg.com/media/HUt83MGaEAAIP8F.jpg?name=orig) |
| KL200 | [巨狮对抗黑暗神](prompts/action-fight/KL200.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2111372306761290098) | 230 | — |
| KL205 | [矮人森林对决编排](prompts/action-fight/KL205.md) | [@AibeginnerR8](https://x.com/AibeginnerR8) | [X](https://x.com/AibeginnerR8/status/2110935160434610592) | 2975 | — |
| KL206 | [军队阵型被爆炸冲散](prompts/action-fight/KL206.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2111358380656730513) | 247 | — |
| KL212 | [季风夜霓虹街头极速追逐](prompts/action-fight/KL212.md) | [@bmx\_ai13](https://x.com/bmx_ai13) | [X](https://x.com/bmx_ai13/status/2113620690129862944) | 4538 | — |
| KL227 | [地下拳击最终回合](prompts/action-fight/KL227.md) | [@PixVerse](https://x.com/PixVerse) | [X](https://x.com/PixVerse/status/2115821056053391623) | 17178 | — |
| KL229 | [办公室女郎动作逃脱](prompts/action-fight/KL229.md) | [@openclipsai](https://x.com/openclipsai) | [X](https://x.com/openclipsai/status/2116145694264180982) | 2127 | — |
| KL232 | [黎明武术对决](prompts/action-fight/KL232.md) | [@yourPlugAI](https://x.com/yourPlugAI) | [X](https://x.com/yourPlugAI/status/2105587110639985048) | 4440 | — |
| KL239 | [雨后屋顶跑酷](prompts/action-fight/KL239.md) | [@PixVerse](https://x.com/PixVerse) | [X](https://x.com/PixVerse/status/2116123043949162826) | 17284 | — |
| KL248 | [屋顶跑酷追逐](prompts/action-fight/KL248.md) | [kling4.video](https://kling4.video) | [kling4.video](https://kling4.video/prompts) | 330 | — |
| KL261 | [仓库写实动作对打](prompts/action-fight/KL261.md) | [@SilentNightX97](https://x.com/SilentNightX97) | [X](https://x.com/SilentNightX97/status/2111489279767761391) | 2670 | — |
| KL266 | [女怪盗跑酷追逐](prompts/action-fight/KL266.md) | [@Ayu\_AI\_0912](https://x.com/Ayu_AI_0912) | [X](https://x.com/Ayu_AI_0912/status/2112459281719230619) | 3389 | — |
| KL268 | [电视头快递员动漫打斗](prompts/action-fight/KL268.md) | [@baskojpeg](https://x.com/baskojpeg) | [X](https://x.com/baskojpeg/status/2114162856350589256) | 3910 | — |
| KL275 | [体操运动员田径场后空翻](prompts/action-fight/KL275.md) | [@openclipsai](https://x.com/openclipsai) | [X](https://x.com/openclipsai/status/2121516484354842969) | 800 | — |

## 参考素材与 @ 点名

| # | 提示词 | 作者 | 原帖 | 字符 | 成片 |
| --- | --- | --- | --- | --- | --- |
| KL043 | [爆炸背景中淡定行走](prompts/reference-elements/KL043.md) | [@MeenakshiYACS](https://x.com/MeenakshiYACS) | [X](https://x.com/MeenakshiYACS/status/2122662803949625675) | 1692 | [视频](https://video.twimg.com/amplify_video/2122662477574144000/vid/avc1/1280x720/_16kgaYgu9PRJhg0.mp4?tag=29) |
| KL044 | [静止女子与快进人群](prompts/reference-elements/KL044.md) | [@AIwithSynthia](https://x.com/AIwithSynthia) | [X](https://x.com/AIwithSynthia/status/2113237971449348351) | 1415 | [视频](https://video.twimg.com/amplify_video/2113237843116244992/vid/avc1/1920x1080/zgm_5gBhoXHVelsn.mp4?tag=29) |
| KL065 | [酒红皮裙走秀](prompts/reference-elements/KL065.md) | [@Diplomeme](https://x.com/Diplomeme) | [X](https://x.com/Diplomeme/status/2109983638242947120) | 7608 | [视频](https://video.twimg.com/amplify_video/2109983164592693248/vid/avc1/1280x720/4nSJqcJUioAZ1AaV.mp4?tag=29) |
| KL066 | [夜晚兄弟会门前人物场景](prompts/reference-elements/KL066.md) | [@EndFolding79421](https://x.com/EndFolding79421) | [X](https://x.com/EndFolding79421/status/2111091805928186144) | 3518 | [视频](https://video.twimg.com/amplify_video/2111091140690595840/vid/avc1/1280x720/R1630KsPT4o_sMkJ.mp4?tag=29) |
| KL068 | [装甲战士下厨烹饪](prompts/reference-elements/KL068.md) | [@tokyo\_Valentine](https://x.com/tokyo_Valentine) | [X](https://x.com/tokyo_Valentine/status/2115085471005159653) | 6700 | [视频](https://video.twimg.com/amplify_video/2115083824946425856/vid/avc1/3840x2160/QkSSEvHNm4nQ_LwT.mp4?tag=29) |
| KL075 | [王座厅哥特浪漫](prompts/reference-elements/KL075.md) | [@Kiber\_Alla](https://x.com/Kiber_Alla) | [X](https://x.com/Kiber_Alla/status/2114039729997881750) | 4505 | [视频](https://video.twimg.com/amplify_video/2114030388167282688/vid/avc1/1920x1080/bKu_iFmqVEo6KTLn.mp4?tag=29) |
| KL085 | [特效擦除转场分解](prompts/reference-elements/KL085.md) | [@onofumi\_AI](https://x.com/onofumi_AI) | [X](https://x.com/onofumi_AI/status/2108487186777846023) | 1536 | [视频](https://video.twimg.com/amplify_video/2108485683681832960/vid/avc1/1280x720/WSxNn9GxFEWBHUt4.mp4?tag=29) |
| KL129 | [仓鼠摇滚明星分镜](prompts/reference-elements/KL129.md) | [@EndFolding79421](https://x.com/EndFolding79421) | [X](https://x.com/EndFolding79421/status/2115559321916375478) | 2791 | [视频](https://video.twimg.com/amplify_video/2115559000557096960/vid/avc1/1080x1920/k5fAHbBrR0jhdPUr.mp4?tag=29) |
| KL132 | [废土跑酷女战士](prompts/reference-elements/KL132.md) | [@DjajaYerry75](https://x.com/DjajaYerry75) | [X](https://x.com/DjajaYerry75/status/2114992691801215463) | 6096 | [视频](https://video.twimg.com/amplify_video/2114986927648800768/vid/avc1/1920x1080/JrnySG28t7YyyhRf.mp4?tag=29) |
| KL147 | [风暴海岸怪物现身](prompts/reference-elements/KL147.md) | [@shikoba\_86](https://x.com/shikoba_86) | [X](https://x.com/shikoba_86/status/2107845423276634467) | 1484 | [视频](https://video.twimg.com/amplify_video/2107838776357613568/vid/avc1/1284x716/_wFgFFf4NC-RStgG.mp4?tag=29) |
| KL173 | [替换视频中的元素](prompts/reference-elements/KL173.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 155 | [视频](https://v3b.fal.media/files/b/0aaf4ddb/pZ6eA8gQuTL9pAc7mwxt-_63efb6a523d2b8105985ce9338117c25018bab8c606c66e1722301da9b708cca.mp4) |
| KL174 | [图像替换主体与场景](prompts/reference-elements/KL174.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 224 | [视频](https://v3b.fal.media/files/b/0aaf4ddc/Ub9zLlVyaO7w1xdDwoHqs_0b604d3b58724d192a863121dfca50310bf17e48eb657552018d186b108fef9e.mp4) |
| KL175 | [移除画面前景路人](prompts/reference-elements/KL175.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 276 | [视频](https://v3b.fal.media/files/b/0aaf4de0/NtiD1TTEfBcm8HkQIfY8Y_c296ed14aa010d1864766153e71a8e3e761230a753e55e6cced00f43cddc5709.mp4) |
| KL176 | [狗狗改为体素风格](prompts/reference-elements/KL176.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 200 | [视频](https://v3b.fal.media/files/b/0aaf4de1/eqvepK5gQ8IRw18BUeBjc_c88fba79a88c25f91ed2c83cda0295fd7d731193b5a143f21cc1462fd4aecbe3.mp4) |
| KL177 | [巨龙飞越海岸城市](prompts/reference-elements/KL177.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 127 | [视频](https://v3b.fal.media/files/b/0aaf4dcc/1ez6sD6nETCM85I-riTwE_334bcd65a302e2b6bf43d352225aa1f8407dc265a7790981a4a4c92a094aaccd.mp4) |
| KL183 | [两船疾驰海岸线](prompts/reference-elements/KL183.md) | [@shikoba\_86](https://x.com/shikoba_86) | [X](https://x.com/shikoba_86/status/2107845433938653337) | 855 | [视频](https://video.twimg.com/amplify_video/2107840134565507073/vid/avc1/1284x716/L2s4lj_akrvksk9B.mp4?tag=29) |
| KL184 | [黄昏海滩对话场景](prompts/reference-elements/KL184.md) | [@shikoba\_86](https://x.com/shikoba_86) | [X](https://x.com/shikoba_86/status/2107845428284715318) | 1477 | [视频](https://video.twimg.com/amplify_video/2107839380362493952/vid/avc1/1284x716/dVUK2M2BJy66Yloy.mp4?tag=29) |
| KL189 | [摄像机怪兽城市肆虐](prompts/reference-elements/KL189.md) | [@CaptainHaHaa](https://x.com/CaptainHaHaa) | [X](https://x.com/CaptainHaHaa/status/2113996003913179501) | 4037 | — |
| KL191 | [无人机航拍日本小镇](prompts/reference-elements/KL191.md) | [@boke\_ai](https://x.com/boke_ai) | [X](https://x.com/boke_ai/status/2117212528522547350) | 1400 | — |
| KL216 | [花海中的小女巫](prompts/reference-elements/KL216.md) | [@imhealmachine](https://x.com/imhealmachine) | [X](https://x.com/imhealmachine/status/2105659020359184617) | 4614 | — |
| KL224 | [双人东京屋顶跑酷](prompts/reference-elements/KL224.md) | [@Ayu\_AI\_0912](https://x.com/Ayu_AI_0912) | [X](https://x.com/Ayu_AI_0912/status/2112801128442425495) | 1552 | — |
| KL273 | [画廊晚宴双女主](prompts/reference-elements/KL273.md) | [@FlyAIgh](https://x.com/FlyAIgh) | [X](https://x.com/FlyAIgh/status/2117267250428186922) | 2230 | — |

## 长片与多镜头

| # | 提示词 | 作者 | 原帖 | 字符 | 成片 |
| --- | --- | --- | --- | --- | --- |
| KL018 | [旅行情侣接住场景](prompts/long-multishot/KL018.md) | [@itxsarmadd](https://x.com/itxsarmadd) | [X](https://x.com/itxsarmadd/status/2117848225176793451) | 2749 | [视频](https://video.twimg.com/amplify_video/2117848160576110593/vid/avc1/1280x720/WinLDwpoTMUDLSiV.mp4?tag=29) |
| KL021 | [料理学院爆笑喜剧场面](prompts/long-multishot/KL021.md) | [@yourPlugAI](https://x.com/yourPlugAI) | [X](https://x.com/yourPlugAI/status/2112030985751756819) | 4687 | [视频](https://video.twimg.com/amplify_video/2112028260959731712/vid/avc1/1920x1080/FMrU6GqxkxF_Vdke.mp4?tag=29) |
| KL093 | [黄金时刻滑雪剪辑](prompts/long-multishot/KL093.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2111471581461426236) | 3771 | [视频](https://video.twimg.com/amplify_video/2111469482438737920/vid/avc1/1920x1080/K-0LJVX-qJ4UJa5D.mp4?tag=29) |
| KL106 | [超自然谋杀悬疑预告](prompts/long-multishot/KL106.md) | [@EndFolding79421](https://x.com/EndFolding79421) | [X](https://x.com/EndFolding79421/status/2111482327842930903) | 5454 | [视频](https://video.twimg.com/amplify_video/2111481932999471104/vid/avc1/1280x720/mNUBlnHdGfK8eGqb.mp4?tag=29) |
| KL122 | [骑士与石化巨龙](prompts/long-multishot/KL122.md) | [@itsPixieVerse](https://x.com/itsPixieVerse) | [X](https://x.com/itsPixieVerse/status/2112260520502005807) | 3512 | [图片](https://pbs.twimg.com/media/HVA_XkpbgAEoCKj.jpg?name=orig) |
| KL133 | [复古机器人家庭悬疑](prompts/long-multishot/KL133.md) | [@obi\_ai6193](https://x.com/obi_ai6193) | [X](https://x.com/obi_ai6193/status/2110855814005342673) | 993 | [视频](https://video.twimg.com/amplify_video/2110852998725591040/vid/avc1/1916x1080/53OcAJZfT3TbHTkK.mp4?tag=29) |
| KL141 | [陶艺师拉坯制碗](prompts/long-multishot/KL141.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2112636160254312763) | 377 | [视频](https://video.twimg.com/amplify_video/2112636132286758912/vid/avc1/1920x1080/kFTA12Wpj6cJbItp.mp4?tag=16) |
| KL146 | [海岸线爆炸摧毁场景](prompts/long-multishot/KL146.md) | [@shikoba\_86](https://x.com/shikoba_86) | [X](https://x.com/shikoba_86/status/2107845437705097483) | 1630 | [视频](https://video.twimg.com/amplify_video/2107840669171527680/vid/avc1/1284x716/iC5OJL8a3nOiFahN.mp4?tag=29) |
| KL157 | [第三人称游戏演示](prompts/long-multishot/KL157.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 323 | [视频](https://v15-kling.klingai.com/bs2/upload-ylab-stunt-sgp/kling-userdoc/file/ef6e899e138631f78ec902bcb423b177eaed713e76e73aff571d7db046a84de9.mp4) |
| KL168 | [轮船钢琴多镜头](prompts/long-multishot/KL168.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 161 | [视频](https://v3b.fal.media/files/b/0aaf4d86/iGBXbJsT-8ZKl9K_uE7-o_79118979d9da8918cb88b44b9b53fd2c03388b47cf92b5838cb8f5c2caa33359.mp4) |
| KL194 | [夕阳住宅小巷告别戏](prompts/long-multishot/KL194.md) | [@agi\_aibusi](https://x.com/agi_aibusi) | [X](https://x.com/agi_aibusi/status/2111462820349124692) | 4214 | — |
| KL247 | [列车窗边的告别](prompts/long-multishot/KL247.md) | [kling4.video](https://kling4.video) | [kling4.video](https://kling4.video/prompts) | 361 | — |
| KL262 | [罗马尼亚民间黑暗喜剧](prompts/long-multishot/KL262.md) | [@airina\_xyz](https://x.com/airina_xyz) | [X](https://x.com/airina_xyz/status/2117270321573277946) | 2357 | — |

## 动画与风格化

| # | 提示词 | 作者 | 原帖 | 字符 | 成片 |
| --- | --- | --- | --- | --- | --- |
| KL001 | [90年代动画风海边人行道](prompts/animation-stylized/KL001.md) | [@ShamiWeb3](https://x.com/ShamiWeb3) | [X](https://x.com/ShamiWeb3/status/2112362909225652454) | 5936 | [视频](https://video.twimg.com/amplify_video/2112362771526668289/vid/avc1/2560x1440/sXe1W6zETdFenI4s.mp4?tag=29) |
| KL027 | [金色马车城市升降镜头](prompts/animation-stylized/KL027.md) | [@churvikv](https://x.com/churvikv) | [X](https://x.com/churvikv/status/2116177920976691286) | 656 | [视频](https://video.twimg.com/amplify_video/2116176696147628034/vid/avc1/1280x720/krx2aeNPcxxN5FXB.mp4?tag=29) |
| KL030 | [黑白动画雨中天台](prompts/animation-stylized/KL030.md) | [@itxabdullaa](https://x.com/itxabdullaa) | [X](https://x.com/itxabdullaa/status/2118357957901684816) | 2241 | [视频](https://video.twimg.com/amplify_video/2118357683627610112/vid/avc1/1280x720/ITvX_Pl0HKiF2ruE.mp4?tag=29) |
| KL035 | [男孩为妈妈烤生日蛋糕](prompts/animation-stylized/KL035.md) | [@aiwithaly](https://x.com/aiwithaly) | [X](https://x.com/aiwithaly/status/2115085490475217187) | 1164 | [视频](https://video.twimg.com/amplify_video/2115085276452429824/vid/avc1/1920x1080/cy0cTgkCjP-YOxSj.mp4?tag=29) |
| KL051 | [南瓜小怪物讨糖](prompts/animation-stylized/KL051.md) | [@RizwanAly07](https://x.com/RizwanAly07) | [X](https://x.com/RizwanAly07/status/2115710188162531472) | 3196 | [视频](https://video.twimg.com/amplify_video/2115710143849762816/vid/avc1/960x720/I40CdJs-SyyhFj-F.mp4?tag=29) |
| KL076 | [钟楼蝙蝠群文字](prompts/animation-stylized/KL076.md) | [@Shinebynous](https://x.com/Shinebynous) | [X](https://x.com/Shinebynous/status/2113746281663238357) | 334 | [视频](https://video.twimg.com/amplify_video/2113744473423233024/vid/avc1/1920x1080/LwrgqldctQbzOdOI.mp4?tag=29) |
| KL079 | [手绘火山峡谷冒险](prompts/animation-stylized/KL079.md) | [@itsPixieVerse](https://x.com/itsPixieVerse) | [X](https://x.com/itsPixieVerse/status/2105140021565194487) | 2201 | [视频](https://video.twimg.com/amplify_video/2105136637495869440/vid/avc1/1280x720/Qp9XFqQCINr1-bjr.mp4?tag=29) |
| KL087 | [少女与红龙烤牛排](prompts/animation-stylized/KL087.md) | [@Ukiyo\_il](https://x.com/Ukiyo_il) | [X](https://x.com/Ukiyo_il/status/2112483976912814115) | 3179 | [图片](https://pbs.twimg.com/media/HVDKe4qbAAE23fv.jpg?name=orig) |
| KL100 | [黏土小幽灵努力吓人](prompts/animation-stylized/KL100.md) | [@JasonHeatony7](https://x.com/JasonHeatony7) | [X](https://x.com/JasonHeatony7/status/2115812533533581757) | 1513 | [视频](https://video.twimg.com/amplify_video/2115812177206562816/vid/avc1/720x1280/3uL9a6qJaB1_XYwH.mp4?tag=29) |
| KL105 | [海盗船长宝藏动画](prompts/animation-stylized/KL105.md) | [@airina\_xyz](https://x.com/airina_xyz) | [X](https://x.com/airina_xyz/status/2116643437831438424) | 2188 | [视频](https://video.twimg.com/amplify_video/2116643375260798976/vid/avc1/1920x1080/_MMIM0vMZ6SzdO9S.mp4?tag=16) |
| KL108 | [油画质感天空之城女主角](prompts/animation-stylized/KL108.md) | [@itsPixieVerse](https://x.com/itsPixieVerse) | [X](https://x.com/itsPixieVerse/status/2105697908624617880) | 3705 | [图片](https://pbs.twimg.com/media/HTjwRT4aQAAGYz6.jpg?name=orig) |
| KL128 | [风中蓝眼女子特写](prompts/animation-stylized/KL128.md) | [leonel22](https://civitai.com/user/leonel22) | [Civitai](https://civitai.com/images/149006041) | 4098 | [视频](https://image.civitai.com/xG1nkqKTMzGDvpLrqFT7WA/10046d1b-2a88-4b5b-a288-01f15c8fb6cc/original=true/10046d1b-2a88-4b5b-a288-01f15c8fb6cc.mp4) |
| KL136 | [定格动画火鸡举牌求救](prompts/animation-stylized/KL136.md) | [@heathergreen](https://x.com/heathergreen) | [X](https://x.com/heathergreen/status/2119067188640268410) | 1135 | [视频](https://video.twimg.com/amplify_video/2119066067230154752/vid/avc1/1080x1920/IbITdNItmppP_816.mp4?tag=29) |
| KL150 | [少女看列车进站](prompts/animation-stylized/KL150.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2112635900165533768) | 303 | [视频](https://video.twimg.com/amplify_video/2112635864245587968/vid/avc1/1920x1080/MGVWPDWerS26BnuA.mp4?tag=16) |
| KL151 | [雪中狐狸](prompts/animation-stylized/KL151.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2112635951428362261) | 250 | [视频](https://video.twimg.com/amplify_video/2112635913427877890/vid/avc1/1920x1080/7l8dRYW7NwyUaUzD.mp4?tag=16) |
| KL155 | [走廊回眸的少女](prompts/animation-stylized/KL155.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2115443417849516282) | 595 | [视频](https://video.twimg.com/amplify_video/2115443395791634432/vid/avc1/1920x1080/BoMngBJX77avdLBJ.mp4?tag=16) |
| KL161 | [刺猬邮差穿越森林](prompts/animation-stylized/KL161.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 794 | [视频](https://v3b.fal.media/files/b/0aaf4dc4/KI9Rh7AqHkp8bSqBhjsIT_52878a899f4eff8cbf6841ba9094ad829e63fd78c995c488c2ebb2c4617df322.mp4) |
| KL164 | [粘土牧羊人与羊群](prompts/animation-stylized/KL164.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 623 | [视频](https://v3b.fal.media/files/b/0aaf4d77/ALqvzT2Gpx_QWbL588PCh_efb066795148d3cbca4d7ab9737d02c1f965a0a07dce2ccc62038a085dd96222.mp4) |
| KL165 | [故障风黑影动画](prompts/animation-stylized/KL165.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 513 | [视频](https://v3b.fal.media/files/b/0aaf4d77/ALqvzT2Gpx_QWbL588PCh_efb066795148d3cbca4d7ab9737d02c1f965a0a07dce2ccc62038a085dd96222.mp4) |
| KL172 | [花栗鼠探出地洞](prompts/animation-stylized/KL172.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 312 | [视频](https://v3b.fal.media/files/b/0aaf4d91/eSykwgz_brYiT4rNahtQB_83a6c30607e0c1ae7d238e87f91b3100f61b6775f2192db6c0c5773835a36f64.mp4) |
| KL181 | [动态文字标题卡](prompts/animation-stylized/KL181.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 436 | [视频](https://v3b.fal.media/files/b/0aaf4dd6/NT5UYxQgUUcYTl2k_dKEO_f665bad7131cdec1a10222d1517486b0b9308b643f09d3b5e33313c294089fb7.mp4) |
| KL196 | [动画少女吃拉面](prompts/animation-stylized/KL196.md) | [@minuitIA](https://x.com/minuitIA) | [X](https://x.com/minuitIA/status/2112963773568860421) | 1396 | — |
| KL218 | [体素万圣节怪物来访](prompts/animation-stylized/KL218.md) | [@SocialSight](https://x.com/SocialSight) | [X](https://x.com/SocialSight/status/2116515858079953349) | 1127 | — |
| KL225 | [小牛追蓝蝴蝶](prompts/animation-stylized/KL225.md) | [@openclipsai](https://x.com/openclipsai) | [X](https://x.com/openclipsai/status/2113350679133831357) | 1449 | — |
| KL226 | [羊毛毡小幽灵练胆](prompts/animation-stylized/KL226.md) | [@SocialSight](https://x.com/SocialSight) | [X](https://x.com/SocialSight/status/2115791624106049891) | 986 | — |
| KL231 | [老奶奶偷地精游戏画面](prompts/animation-stylized/KL231.md) | [@SocialSight](https://x.com/SocialSight) | [X](https://x.com/SocialSight/status/2119430398178415032) | 1215 | — |
| KL234 | [黏土牧羊人喜剧](prompts/animation-stylized/KL234.md) | [@bmx\_ai13](https://x.com/bmx_ai13) | [X](https://x.com/bmx_ai13/status/2105229919001203058) | 3033 | — |
| KL236 | [抽象爵士音符之旅](prompts/animation-stylized/KL236.md) | [@SocialSight](https://x.com/SocialSight) | [X](https://x.com/SocialSight/status/2115066851235406075) | 1244 | — |
| KL237 | [定格女孩灯笼森林](prompts/animation-stylized/KL237.md) | [@SocialSight](https://x.com/SocialSight) | [X](https://x.com/SocialSight/status/2115429311922541050) | 1014 | — |
| KL238 | [复古动画女巫之夜](prompts/animation-stylized/KL238.md) | [@ShamiWeb3](https://x.com/ShamiWeb3) | [X](https://x.com/ShamiWeb3/status/2115663194593304960) | 4885 | — |
| KL241 | [面包镇发射月亮](prompts/animation-stylized/KL241.md) | [@SocialSight](https://x.com/SocialSight) | [X](https://x.com/SocialSight/status/2116893788081693071) | 1050 | — |
| KL245 | [定格动画动物茶会](prompts/animation-stylized/KL245.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 286 | — |
| KL255 | [剪纸狐狸动画](prompts/animation-stylized/KL255.md) | [kling4.video](https://kling4.video) | [kling4.video](https://kling4.video/prompts) | 289 | — |
| KL263 | [别按按钮立体字动画](prompts/animation-stylized/KL263.md) | [@su\_nagomi](https://x.com/su_nagomi) | [X](https://x.com/su_nagomi/status/2110877883128574135) | 2721 | — |
| KL267 | [粉发科技风动漫少女](prompts/animation-stylized/KL267.md) | [@Iancu\_ai](https://x.com/Iancu_ai) | [X](https://x.com/Iancu_ai/status/2113988696479547703) | 2837 | — |
| KL274 | [立体书城市展开](prompts/animation-stylized/KL274.md) | [@kodavid](https://x.com/kodavid) | [X](https://x.com/kodavid/status/2117724837020127736) | 500 | — |

## 产品与广告

| # | 提示词 | 作者 | 原帖 | 字符 | 成片 |
| --- | --- | --- | --- | --- | --- |
| KL015 | [创作者红牛UGC广告](prompts/product-ads/KL015.md) | [@Diplomeme](https://x.com/Diplomeme) | [X](https://x.com/Diplomeme/status/2106963076520329457) | 6604 | [视频](https://video.twimg.com/amplify_video/2106962314478112768/vid/avc1/1280x720/Dbp3tFsOPSNhpKLD.mp4?tag=29) |
| KL023 | [奢华美妆ASMR微距](prompts/product-ads/KL023.md) | [@yourPlugAI](https://x.com/yourPlugAI) | [X](https://x.com/yourPlugAI/status/2114574940166840517) | 3958 | [视频](https://video.twimg.com/amplify_video/2114574288065871872/vid/avc1/1920x1080/D8a1AluVikN3a3Vm.mp4?tag=29) |
| KL029 | [起亚Seltos森林汽车广告](prompts/product-ads/KL029.md) | [@Diplomeme](https://x.com/Diplomeme) | [X](https://x.com/Diplomeme/status/2110947179057811727) | 5444 | [视频](https://video.twimg.com/amplify_video/2110946998937608192/vid/avc1/1920x1080/Z4DhqLJke2TyoCAz.mp4?tag=29) |
| KL038 | [香水瓶火箭冲上坡道](prompts/product-ads/KL038.md) | [@AIWithRay](https://x.com/AIWithRay) | [X](https://x.com/AIWithRay/status/2114672427964010805) | 2183 | [视频](https://video.twimg.com/amplify_video/2114671558106968064/vid/avc1/1080x1920/QEBXIzM8NwG7YXIs.mp4?tag=29) |
| KL046 | [首尔便利店动作广告](prompts/product-ads/KL046.md) | [@Diplomeme](https://x.com/Diplomeme) | [X](https://x.com/Diplomeme/status/2106253394403074307) | 12434 | [视频](https://video.twimg.com/amplify_video/2106251307271290881/vid/avc1/1280x720/eymu-W3-7LscSTTd.mp4?tag=29) |
| KL049 | [韩国旅行时尚大片](prompts/product-ads/KL049.md) | [@Diplomeme](https://x.com/Diplomeme) | [X](https://x.com/Diplomeme/status/2105902453770342795) | 12819 | [视频](https://video.twimg.com/amplify_video/2105901540355776512/vid/avc1/1280x720/I1ucY0jSmZbL1MYF.mp4?tag=29) |
| KL057 | [手势切换汽车广告](prompts/product-ads/KL057.md) | [@AiwithBloodline](https://x.com/AiwithBloodline) | [X](https://x.com/AiwithBloodline/status/2109550137601331267) | 2221 | [视频](https://video.twimg.com/amplify_video/2109549906105184256/vid/avc1/720x1280/dzQs0sBXRxXFkXYY.mp4?tag=29) |
| KL071 | [奢华客厅室内广告](prompts/product-ads/KL071.md) | [@WorldEverett](https://x.com/WorldEverett) | [X](https://x.com/WorldEverett/status/2105275472552542625) | 1543 | [视频](https://video.twimg.com/amplify_video/2105274711751917568/vid/avc1/1280x720/gWc-yHkVnts8TEhJ.mp4?tag=29) |
| KL102 | [猫咪骑扫地机器人](prompts/product-ads/KL102.md) | [@aiIgnatius](https://x.com/aiIgnatius) | [X](https://x.com/aiIgnatius/status/2114669067189584367) | 1127 | [视频](https://video.twimg.com/amplify_video/2114668907223031808/vid/avc1/720x1280/cuJoPPnd33ToqulR.mp4?tag=29) |
| KL109 | [冰箱到派对一镜到底](prompts/product-ads/KL109.md) | [@shikoba\_86](https://x.com/shikoba_86) | [X](https://x.com/shikoba_86/status/2113047628271198538) | 1523 | [视频](https://video.twimg.com/amplify_video/2113002921373712384/vid/avc1/1924x1076/DtxlIWvmfFNw7ZjR.mp4?tag=29) |
| KL116 | [白桦气泡水产品广告](prompts/product-ads/KL116.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2104742449562136796) | 1012 | [视频](https://video.twimg.com/amplify_video/2104742391592718336/vid/avc1/1080x1920/na7NzG_TFwgvju1f.mp4?tag=29) |
| KL131 | [越野车飞越静坐男子](prompts/product-ads/KL131.md) | [@kaanakz](https://x.com/kaanakz) | [X](https://x.com/kaanakz/status/2107204923146321922) | 3933 | [视频](https://video.twimg.com/amplify_video/2107204878653145088/vid/avc1/720x1280/E9EFZTLzuDRnudIp.mp4?tag=29) |
| KL138 | [哑光黑化妆品瓶特写](prompts/product-ads/KL138.md) | [@sebatheepan](https://x.com/sebatheepan) | [X](https://x.com/sebatheepan/status/2104653409227829496) | 444 | [视频](https://video.twimg.com/amplify_video/2104651572806389760/vid/avc1/1280x720/dMKcJGoOgq9H1Y10.mp4?tag=29) |
| KL152 | [易拉罐冷凝水珠](prompts/product-ads/KL152.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2112635999000072241) | 272 | [视频](https://video.twimg.com/amplify_video/2112635964560654336/vid/avc1/1920x1080/vDr8Oe7TYwfDIhpn.mp4?tag=16) |
| KL208 | [未来相机碎裂现实](prompts/product-ads/KL208.md) | [@openclipsai](https://x.com/openclipsai) | [X](https://x.com/openclipsai/status/2114725113736081634) | 1486 | — |
| KL251 | [陶瓷杯注咖啡特写](prompts/product-ads/KL251.md) | [kling4.video](https://kling4.video) | [kling4.video](https://kling4.video/prompts) | 327 | — |

## 手机实拍与社媒

| # | 提示词 | 作者 | 原帖 | 字符 | 成片 |
| --- | --- | --- | --- | --- | --- |
| KL003 | [男友夏日街头随手拍女友](prompts/ugc-social/KL003.md) | [@agi\_aibusi](https://x.com/agi_aibusi) | [X](https://x.com/agi_aibusi/status/2110924173619138656) | 7090 | [视频](https://video.twimg.com/amplify_video/2110923316307636224/vid/avc1/1920x1080/T0t0-x7idhPI3KVp.mp4?tag=29) |
| KL009 | [咖啡店手机前置镜头独白](prompts/ugc-social/KL009.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2111471573395755295) | 2234 | [视频](https://video.twimg.com/amplify_video/2111468111576563712/vid/avc1/1080x1920/ZG1drhw2mT6L5O-B.mp4?tag=29) |
| KL013 | [猫咪披萨外卖手机短片](prompts/ugc-social/KL013.md) | [@Strength04\_X](https://x.com/Strength04_X) | [X](https://x.com/Strength04_X/status/2105889942958440671) | 6121 | [视频](https://video.twimg.com/amplify_video/2105889193734107136/vid/avc1/1280x720/5_BavjXpTeFL-0J_.mp4?tag=29) |
| KL017 | [千禧DV风首尔周日街头](prompts/ugc-social/KL017.md) | [@AI\_\_TSUBAKI](https://x.com/AI__TSUBAKI) | [X](https://x.com/AI__TSUBAKI/status/2110752410021044724) | 3577 | [视频](https://video.twimg.com/amplify_video/2110751934378561537/vid/avc1/1920x1080/bK26XTyE0lyF2zMG.mp4?tag=29) |
| KL019 | [金发女子浴室时尚摆拍](prompts/ugc-social/KL019.md) | [@Sharjeelai\_786](https://x.com/Sharjeelai_786) | [X](https://x.com/Sharjeelai_786/status/2120383381049336285) | 1491 | [视频](https://video.twimg.com/amplify_video/2120383301709869056/vid/avc1/720x1280/oh1rpu_oxo6Hdjdt.mp4?tag=29) |
| KL025 | [手持跟拍猫咪夜间狂奔](prompts/ugc-social/KL025.md) | [@umesh\_ai](https://x.com/umesh_ai) | [X](https://x.com/umesh_ai/status/2110797373584887907) | 2232 | [视频](https://video.twimg.com/amplify_video/2110797232949891072/vid/avc1/1920x1080/PmoCWgQ7bvfE_u1w.mp4?tag=29) |
| KL031 | [相扑选手花样滑冰](prompts/ugc-social/KL031.md) | [@techhalla](https://x.com/techhalla) | [X](https://x.com/techhalla/status/2105808684680945905) | 592 | [视频](https://video.twimg.com/amplify_video/2105808245298286592/vid/avc1/1920x1080/pdVjrGX2DzzVGX7_.mp4?tag=29) |
| KL037 | [厨房咖啡洒落小插曲](prompts/ugc-social/KL037.md) | [@Sharjeelai\_786](https://x.com/Sharjeelai_786) | [X](https://x.com/Sharjeelai_786/status/2120333668518633659) | 1587 | [视频](https://video.twimg.com/amplify_video/2120333595181199360/vid/avc1/720x1280/9WQavDJWGqdJAY3d.mp4?tag=29) |
| KL041 | [偶像电玩城休息日](prompts/ugc-social/KL041.md) | [@Diplomeme](https://x.com/Diplomeme) | [X](https://x.com/Diplomeme/status/2107695270129709378) | 3331 | [视频](https://video.twimg.com/amplify_video/2107693763611213824/vid/avc1/1280x720/6QDIpVziHErJybg7.mp4?tag=29) |
| KL052 | [高定礼服派对视频](prompts/ugc-social/KL052.md) | [@Diplomeme](https://x.com/Diplomeme) | [X](https://x.com/Diplomeme/status/2108590903946559787) | 7796 | [视频](https://video.twimg.com/amplify_video/2108590587180167168/vid/avc1/1280x720/3DmJCNeQLiPRohkk.mp4?tag=29) |
| KL072 | [电梯隐藏摄像头恶作剧](prompts/ugc-social/KL072.md) | [@Zyvex\_0x](https://x.com/Zyvex_0x) | [X](https://x.com/Zyvex_0x/status/2115884074225017101) | 12219 | [视频](https://video.twimg.com/amplify_video/2115883976371863552/vid/avc1/1080x1920/EPOeNm-YvFnZJimy.mp4?tag=29) |
| KL080 | [巨指戳相扑小人](prompts/ugc-social/KL080.md) | [@AI\_\_TSUBAKI](https://x.com/AI__TSUBAKI) | [X](https://x.com/AI__TSUBAKI/status/2114177828946403423) | 2101 | [视频](https://video.twimg.com/amplify_video/2114171047570485248/vid/avc1/2160x3240/GWP6sg9IhsI3jY6N.mp4?tag=29) |
| KL091 | [雨中停车场自拍倾诉](prompts/ugc-social/KL091.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2111471592601534511) | 1835 | [视频](https://video.twimg.com/amplify_video/2111470541185880064/vid/avc1/1080x1920/XuFIWeDRWTZ9OmhZ.mp4?tag=29) |
| KL095 | [沙滩日落自拍手机视频](prompts/ugc-social/KL095.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2111471595755647205) | 2090 | [视频](https://video.twimg.com/amplify_video/2111470779518861312/vid/avc1/1080x1920/saaeOZRByExdV0ey.mp4?tag=29) |
| KL096 | [机场登机口清晨自拍](prompts/ugc-social/KL096.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2111471585001390367) | 2425 | [视频](https://video.twimg.com/amplify_video/2111470062619983872/vid/avc1/1080x1920/Ar1_HsBLRYsJscer.mp4?tag=29) |
| KL115 | [阳光街道漫步自拍](prompts/ugc-social/KL115.md) | [@minchoi](https://x.com/minchoi) | [X](https://x.com/minchoi/status/2104742701073564121) | 1861 | [视频](https://video.twimg.com/amplify_video/2104742584157458433/vid/avc1/1080x1920/r-YCE7sMmaguzsfx.mp4?tag=29) |
| KL130 | [女性面部特写眼神](prompts/ugc-social/KL130.md) | [@wataru\_ai\_film](https://x.com/wataru_ai_film) | [X](https://x.com/wataru_ai_film/status/2122997338574852359) | 254 | [视频](https://video.twimg.com/amplify_video/2122996847883284481/vid/avc1/720x1280/nFmQVRGx7-vzv-qR.mp4?tag=29) |
| KL162 | [伦敦街头漫步介绍](prompts/ugc-social/KL162.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 370 | [视频](https://v3b.fal.media/files/b/0aaf4d75/UlTSaTK6fXPjwPk9FPiop_86a7fce6addd5a588927ecab74be66149235ca8265ede8d97741362048aeee71.mp4) |
| KL171 | [开朗博主自我介绍](prompts/ugc-social/KL171.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 151 | [视频](https://v3b.fal.media/files/b/0aaf4d90/9iGSotNX0OPmGP9TXK9nb_02b772a36ab2ae2eff34fc7f9ef330249eac2d604068ca1da846ad5f4a48a059.mp4) |
| KL188 | [夜晚城市自拍漫步](prompts/ugc-social/KL188.md) | [@msjiaozhu](https://x.com/msjiaozhu) | [X](https://x.com/msjiaozhu/status/2114211413602324707) | 501 | — |
| KL217 | [纽约街头旅行短片](prompts/ugc-social/KL217.md) | [@PixVerse](https://x.com/PixVerse) | [X](https://x.com/PixVerse/status/2115171746299125899) | 7346 | — |
| KL233 | [中西部政治自拍视频](prompts/ugc-social/KL233.md) | [@bmx\_ai13](https://x.com/bmx_ai13) | [X](https://x.com/bmx_ai13/status/2105008976136126491) | 2476 | — |
| KL242 | [猫咪推杯掉落](prompts/ugc-social/KL242.md) | [@openclipsai](https://x.com/openclipsai) | [X](https://x.com/openclipsai/status/2117613705156338099) | 733 | — |
| KL250 | [夜市炒锅火焰](prompts/ugc-social/KL250.md) | [kling4.video](https://kling4.video) | [kling4.video](https://kling4.video/prompts) | 275 | — |
| KL264 | [2010年代精品店直播带货](prompts/ugc-social/KL264.md) | [@bmx\_ai13](https://x.com/bmx_ai13) | [X](https://x.com/bmx_ai13/status/2111824850222452968) | 2735 | — |
| KL270 | [路边皮卡时尚短片](prompts/ugc-social/KL270.md) | [@jhosephe](https://x.com/jhosephe) | [X](https://x.com/jhosephe/status/2116517016827736303) | 10282 | — |
| KL271 | [西西里小巷柠檬时尚](prompts/ugc-social/KL271.md) | [@jhosephe](https://x.com/jhosephe) | [X](https://x.com/jhosephe/status/2116517451395375367) | 10425 | — |
| KL272 | [阁楼试穿西装旋转](prompts/ugc-social/KL272.md) | [@kodavid](https://x.com/kodavid) | [X](https://x.com/kodavid/status/2117193561351315710) | 636 | — |

## 科幻与奇幻

| # | 提示词 | 作者 | 原帖 | 字符 | 成片 |
| --- | --- | --- | --- | --- | --- |
| KL004 | [拉拉对峙三头犬](prompts/scifi-fantasy/KL004.md) | [@chatgptpaglu](https://x.com/chatgptpaglu) | [X](https://x.com/chatgptpaglu/status/2118313794384593389) | 3042 | [视频](https://video.twimg.com/amplify_video/2118313756413624320/vid/avc1/1280x720/nyK8NE7d8I7bjH73.mp4?tag=29) |
| KL005 | [丛林瀑布与浮空岛屿](prompts/scifi-fantasy/KL005.md) | [@alixbuilds](https://x.com/alixbuilds) | [X](https://x.com/alixbuilds/status/2118580185176187124) | 1385 | [视频](https://video.twimg.com/amplify_video/2118579665241886720/vid/avc1/1438x1080/gw9T2dMWHnaSBHrA.mp4?tag=29) |
| KL020 | [瀑布后的魔法秘境](prompts/scifi-fantasy/KL020.md) | [@CaliraVal](https://x.com/CaliraVal) | [X](https://x.com/CaliraVal/status/2118575122462466442) | 1352 | [视频](https://video.twimg.com/amplify_video/2118574648699088896/vid/avc1/1438x1080/BfbiKoCJgxHa1gbs.mp4?tag=29) |
| KL022 | [迷你云朵生物卧室](prompts/scifi-fantasy/KL022.md) | [@Strength04\_X](https://x.com/Strength04_X) | [X](https://x.com/Strength04_X/status/2114623188202402063) | 1722 | [视频](https://video.twimg.com/amplify_video/2114622261684772864/vid/avc1/1920x1080/v7ZYRIWHTtxCniOB.mp4?tag=29) |
| KL024 | [飞船穿越带电气体风暴](prompts/scifi-fantasy/KL024.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2115004379686199661) | 320 | [视频](https://video.twimg.com/amplify_video/2115004099125026816/vid/avc1/1280x720/89lhNgbRJb0NF0GX.mp4?tag=29) |
| KL040 | [探险队抵达外星遗迹](prompts/scifi-fantasy/KL040.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2109581272578195961) | 572 | [视频](https://video.twimg.com/amplify_video/2109580661182828544/vid/avc1/1280x720/1ObfqMcAnayR86um.mp4?tag=29) |
| KL045 | [女仿生人在实验室苏醒](prompts/scifi-fantasy/KL045.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2112388227810410536) | 715 | [视频](https://video.twimg.com/amplify_video/2112387503269285888/vid/avc1/1280x720/AEqRfMiEdY0xIuNV.mp4?tag=29) |
| KL047 | [果园守护者暗黑奇幻](prompts/scifi-fantasy/KL047.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2106355884398141901) | 705 | [视频](https://video.twimg.com/amplify_video/2106355537579274240/vid/avc1/1280x720/q2YvQqy4WDY3bOby.mp4?tag=29) |
| KL048 | [女猎手与恐龙](prompts/scifi-fantasy/KL048.md) | [@TaliaAariz](https://x.com/TaliaAariz) | [X](https://x.com/TaliaAariz/status/2117896072622146004) | 1049 | [视频](https://video.twimg.com/amplify_video/2117895958918770688/vid/avc1/720x1280/xWUgY1urw4f1pHL4.mp4?tag=29) |
| KL053 | [巨神投石砸向村庄](prompts/scifi-fantasy/KL053.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2112122587333493236) | 253 | [视频](https://video.twimg.com/amplify_video/2112121385690554368/vid/avc1/1280x720/KqQZRXBtcjlVzzR-.mp4?tag=29) |
| KL055 | [地下神殿恐怖显现](prompts/scifi-fantasy/KL055.md) | [@itxsarmadd](https://x.com/itxsarmadd) | [X](https://x.com/itxsarmadd/status/2108520829604745408) | 3908 | [视频](https://video.twimg.com/amplify_video/2108520792929792000/vid/avc1/1280x720/lk0LtAlCnvpZFvC4.mp4?tag=29) |
| KL070 | [月球探险望巨行星](prompts/scifi-fantasy/KL070.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2108123933488689252) | 532 | [视频](https://video.twimg.com/amplify_video/2108121906041831424/vid/avc1/1280x720/VGiBTM6MjevVFJRu.mp4?tag=29) |
| KL073 | [海底水晶王国与巨龙](prompts/scifi-fantasy/KL073.md) | [@SadiaMalik182](https://x.com/SadiaMalik182) | [X](https://x.com/SadiaMalik182/status/2118788480792928401) | 745 | [视频](https://video.twimg.com/amplify_video/2118788028076544000/vid/avc1/1920x1080/uisv7NjOFMPs6lVg.mp4?tag=29) |
| KL084 | [银云之上悬浮悬崖](prompts/scifi-fantasy/KL084.md) | [@bmx\_ai13](https://x.com/bmx_ai13) | [X](https://x.com/bmx_ai13/status/2105168764681453666) | 4251 | [视频](https://video.twimg.com/amplify_video/2105063462594543616/vid/avc1/1280x720/BSTcQiX8lCjLQBwX.mp4?tag=29) |
| KL089 | [发光水之女潜海](prompts/scifi-fantasy/KL089.md) | [@EndFolding79421](https://x.com/EndFolding79421) | [X](https://x.com/EndFolding79421/status/2111076586514489818) | 769 | [视频](https://video.twimg.com/amplify_video/2111074992767086592/vid/avc1/1920x1080/fY549k3QjqAVPdSg.mp4?tag=29) |
| KL092 | [冰霜女子瞳孔变化](prompts/scifi-fantasy/KL092.md) | [leonel22](https://civitai.com/user/leonel22) | [Civitai](https://civitai.com/images/149001236) | 1288 | [视频](https://image.civitai.com/xG1nkqKTMzGDvpLrqFT7WA/a4e2e286-8bff-44b4-bff7-113104652565/original=true/a4e2e286-8bff-44b4-bff7-113104652565.mp4) |
| KL110 | [高管化身铬合金战士](prompts/scifi-fantasy/KL110.md) | [@sebatheepan](https://x.com/sebatheepan) | [X](https://x.com/sebatheepan/status/2107479571226558613) | 8079 | [视频](https://video.twimg.com/amplify_video/2107479016890351616/vid/avc1/1920x1080/iZ-rWwm1m-CGJ-Ck.mp4?tag=29) |
| KL125 | [水墨瀑布化作真流](prompts/scifi-fantasy/KL125.md) | [@opener\_ai](https://x.com/opener_ai) | [X](https://x.com/opener_ai/status/2111666343447818617) | 1045 | [视频](https://video.twimg.com/amplify_video/2111662273332961280/vid/avc1/720x1280/Ic3WInBpCM_1f40b.mp4?tag=29) |
| KL126 | [魔法森林中飞舞的发光精灵](prompts/scifi-fantasy/KL126.md) | [@EndFolding79421](https://x.com/EndFolding79421) | [X](https://x.com/EndFolding79421/status/2110796791100711098) | 2298 | [视频](https://video.twimg.com/amplify_video/2110794969111740417/vid/avc1/1920x1080/FOM3qflnz9pVhrvZ.mp4?tag=29) |
| KL158 | [红衣女子未来逃亡](prompts/scifi-fantasy/KL158.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 547 | [视频](https://v3b.fal.media/files/b/0aaf4d9a/6AxPZRMkV9ArWsJBF8gzt_872b78d316fa5af78df95fccaf7deaf57fb0a18a84c3f15d9fbae66b9638dfc4.mp4) |
| KL160 | [古寺奇幻剑客对决](prompts/scifi-fantasy/KL160.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 431 | [视频](https://v3b.fal.media/files/b/0aaf4d70/qwtzRHNPw5PqT8gbpgxSO_3ac64c5ff30cde5566645303510f1d35cc3c12fdfeb5122fc278338ccd1f0dbd.mp4) |
| KL169 | [月下女巫施法](prompts/scifi-fantasy/KL169.md) | [fal.ai](https://fal.ai) | [fal.ai](https://fal.ai/learn/devs/kling-4-prompting-guide) | 293 | [视频](https://v3b.fal.media/files/b/0aaf4d87/k_AccqIiYmZKOfeusEV2Z_ddfbca5ef131ddbf9355451ac64cd4bebe32fcc4f510650729115a1dfbdc711d.mp4) |
| KL185 | [雷云巨牛狂奔](prompts/scifi-fantasy/KL185.md) | [@7A7PIcreates](https://x.com/7A7PIcreates) | [X](https://x.com/7A7PIcreates/status/2106662981517856989) | 2126 | [视频](https://video.twimg.com/amplify_video/2106662937024741376/vid/avc1/1464x628/X28UbUzm-8MTLYsP.mp4?tag=29) |
| KL187 | [沉没城市水下下潜](prompts/scifi-fantasy/KL187.md) | [@HBCoop\_](https://x.com/HBCoop_) | [X](https://x.com/HBCoop_/status/2115443382445387842) | 529 | [视频](https://video.twimg.com/amplify_video/2115443353949208576/vid/avc1/1920x1080/hzMhOOrwijNVYQ8V.mp4?tag=16) |
| KL190 | [幽灵马南瓜过山车](prompts/scifi-fantasy/KL190.md) | [@PixVerse](https://x.com/PixVerse) | [X](https://x.com/PixVerse/status/2115436072486531080) | 16295 | — |
| KL199 | [外星丛林机械掠食者](prompts/scifi-fantasy/KL199.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2110996674558530007) | 555 | — |
| KL203 | [外星长颈巨兽涉水穿过潟湖](prompts/scifi-fantasy/KL203.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2110982744247353611) | 614 | — |
| KL204 | [异星集市中的旅行者](prompts/scifi-fantasy/KL204.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2116029599104561566) | 325 | — |
| KL207 | [沙漠公路飞车追逐](prompts/scifi-fantasy/KL207.md) | [@openclipsai](https://x.com/openclipsai) | [X](https://x.com/openclipsai/status/2112980625904767186) | 2144 | — |
| KL213 | [日出外星聚居地](prompts/scifi-fantasy/KL213.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2110997691274580344) | 568 | — |
| KL214 | [探险者遇见外星兽群](prompts/scifi-fantasy/KL214.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2115723998700949688) | 331 | — |
| KL219 | [赛博朋克屋顶追逐](prompts/scifi-fantasy/KL219.md) | [@openclipsai](https://x.com/openclipsai) | [X](https://x.com/openclipsai/status/2116544976331145464) | 1307 | — |
| KL221 | [霓虹雨夜科幻射击游戏画面](prompts/scifi-fantasy/KL221.md) | [@aymducking](https://x.com/aymducking) | [X](https://x.com/aymducking/status/2117008462701810159) | 3579 | — |
| KL223 | [双日星球上的初次接触](prompts/scifi-fantasy/KL223.md) | [@Alin\_Reaper05](https://x.com/Alin_Reaper05) | [X](https://x.com/Alin_Reaper05/status/2114038906366693737) | 902 | — |
| KL256 | [灯笼巨鲸掠过村庄](prompts/scifi-fantasy/KL256.md) | [kling4.video](https://kling4.video) | [kling4.video](https://kling4.video/prompts) | 301 | — |
| KL257 | [火星温室的宇航员](prompts/scifi-fantasy/KL257.md) | [kling4.video](https://kling4.video) | [kling4.video](https://kling4.video/prompts) | 286 | — |
| KL259 | [小提琴碎裂化光](prompts/scifi-fantasy/KL259.md) | [@NigelWatsonTFTC](https://x.com/NigelWatsonTFTC) | [X](https://x.com/NigelWatsonTFTC/status/2111149088569766380) | 365 | — |
| KL260 | [巨月牵引海滨城市](prompts/scifi-fantasy/KL260.md) | [@FlyAIgh](https://x.com/FlyAIgh) | [X](https://x.com/FlyAIgh/status/2115849741925781584) | 1849 | — |
| KL265 | [黑暗奇幻电影预告](prompts/scifi-fantasy/KL265.md) | [@NigelWatsonTFTC](https://x.com/NigelWatsonTFTC) | [X](https://x.com/NigelWatsonTFTC/status/2111226213511630938) | 20867 | — |

## 用 API 跑这些提示词

这里链接的成片，是作者在自己用的工具里跑出来的，不是在我们的 API 上跑的。apimodels.app 上对应的模型是 [Kling 4.0](https://apimodels.app/zh/models/kling-4.0)（模型名 `kling-4.0`，[API 文档](https://apimodels.app/zh/docs/kling-4-0)），另有轻量档 [Kling 4.0 Flash](https://apimodels.app/zh/models/kling-4.0-flash)（`kling-4.0-flash`），端点和请求格式都一样：

- 一个模型名三种用法：只写提示词是文生视频；带参考素材是参考生视频，最多 10 张图、5 段视频、7 个具名主体和 3 段音色，在提示词里用 @ 点名；带一张首帧、最多 8 张中间帧和一张尾帧是关键帧生视频。帧和参考素材不能放进同一个请求。
- 时长 3 到 30 秒，720p 或 1080p，提示词最长 10000 字符。时长、分辨率和画幅（auto、16:9、9:16、1:1、21:9）都是请求参数，提示词开头那行「Format: 16:9, 30 seconds, 1080p」应该挪进请求里。
- 不带视频输入时，720p 每秒 $0.157、1080p 每秒 $0.235：720p 5 秒 $0.785，1080p 10 秒 $2.35，720p 30 秒 $4.71。带参考视频时每计费秒 $0.094 或 $0.141；输入视频不长于成片时，计费秒数是成片 × 2，更长时是输入 + 成片，所以 720p 出 10 秒、带一段 5 秒参考视频是 $1.88。参考图和关键帧不另外收费，失败不扣费。
- Kling 4.0 Flash 只有 720p、3 到 20 秒，提示词最长 8000 字符，关键帧只收首帧，也不收单独的音色列表；每秒 $0.094（5 秒 $0.47，10 秒 $0.94），带参考视频每计费秒 $0.063。
- 声音总是生成，关不掉。没有负面提示词、多镜头分镜模式和视频续写，也没有 4K，围绕这些功能写的提示词，要改写成一条普通的提示词。
- 提示词里每个 @ 都要对得上同一个请求里真有的素材，对不上的请求会在扣费前直接被拒。写着「the supplied image」「Video 1」的提示词，要你自己准备素材，放进 `image_urls`、`video_urls` 或 `elements`。只上传你有权使用的人像和声音。
- 本库有 16 条超过 8000 字符，放不进 Flash；其中 10 条超过 10000 字符，在 Kling 4.0 上也要先删短。最长的一条 22008 字符。

```bash
curl -X POST https://api.apimodels.app/v1/video/generations \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "kling-4.0",
    "prompt": "An exploration ship maneuvers through a vast cloud of charged gas and floating debris. Inside the cockpit, the pilot moves the controls while the captain braces against the console and an alien crew member monitors the storm. The camera moves from the crew toward the forward window, cinematic tension, realistic motion.",
    "duration": 10,
    "resolution": "720p",
    "aspect_ratio": "16:9"
  }'
# 720p、10 秒、不带视频输入：$1.57。返回里有 taskId，轮询到 state 为 "completed"：
curl "https://api.apimodels.app/v1/video/generations?task_id=TASK_ID" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

示例里的提示词是本库的 KL024，作者 @Alin_Reaper05，原样引用。

## 怎么收集的

提示词来自四类出处。X 上的帖子一部分是搜出来的，一部分来自 GitHub 上的三个社区合集：[awesome-kling-4.0-prompts](https://github.com/tong0619453646-dev/awesome-kling-4.0-prompts)、[awesome-kling-4-prompts](https://github.com/kingvid-ai/awesome-kling-4-prompts) 和 [awesome-kling-4-0-prompts](https://github.com/BravoNeo/awesome-kling-4-0-prompts)。合集里的每一条都回到 X 原帖核对过：提示词取原帖正文，或作者在原帖下自己的回复；原帖里找不到这段文字的不收，因为那多半是翻译或改写过的版本。[kling4.video 的提示词库](https://kling4.video/prompts)和 [fal.ai 的 Kling 4 提示词指南](https://fal.ai/learn/devs/kling-4-prompting-guide)直接照页面原文收录。Civitai 上的条目取帖子公开的生成信息里的提示词，只收生成信息里写明 Kling 4.0、而且没有挂 LoRA 或其他附加模型的。

没收的：不是可用提示词的帖子（广告、教程、新闻、多模型对比、闲聊、残缺片段）、推广和邀请码、夹着大量评论的提示词、色情内容、涉及未成年人的内容、真人肖像、血腥画面、不到 25 个字符的提示词，以及重复项（同一条帖子，或同一段文字被再发一次）。X 上提示词前面的「Prompt:」之类的标签、结尾的话题标签和 t.co 媒体链接不算提示词正文；提示词本身一个字没改。标题和分类是我们起的，编号顺序与 apimodels.app 上的提示词库一致。

## 出处、版权与许可

- **每条提示词的版权归作者**，视频和图片也归各自的作者。每条都写明作者、附原帖链接，媒体只链接到它原本所在的地方，没有任何文件拷进本仓库。
- **全文收录**：每条提示词都按原帖或原页面逐字全文收录。商用前请先看原帖。
- **我们自己写的内容**（写法说明、标题、分类表、数据文件和浏览页）按 [CC BY 4.0](LICENSE) 许可，引用请注明 apimodels.app 并附链接。
- 如果你是其中某条提示词的作者，想删除或更正署名，请开一个 issue，我们会尽快处理。
