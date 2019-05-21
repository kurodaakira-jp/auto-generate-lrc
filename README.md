# 歌词一键生成脚本（网易 API）

### 本脚本通过调用网上大佬写的 Node.js 版网易云音乐 API ，来实现自动匹配歌曲歌词，在本地生成同名的、相对纯净的 LRC 文件

### 目前匹配含有详细信息的歌曲准确率可达到95+，已测试了2000+首Hi-Res歌曲和少部分整轨切出来的单曲，但都含有详细信息的歌曲，匹配效果很好，没有详细信息的歌曲匹配效果很差

### 说明：
该脚本只适用于有详细属性的音乐文件  
需要用到的属性有：标题（歌曲名）、参与创作的艺术家、唱片集（专辑）、唱片集艺术家（windows 右键属性 转 详细信息）  
如果没有上述四个属性，则只会匹配歌曲名和时长  
目前可供匹配的格式的只有 flac、wav、mp3，其他未测试（代码做了限制直接跳过）

### 运行环境
PHP（我用的是 7+）  
由于程序需要长时间不断调用 API，所以执行时间随文件数量直线增加，请更改 php.ini 的 max_execution_time 到比较合适的值（调大点就对了）

### 需要的插件
getID3（用于读取歌曲信息）  
PHP 的 OpenCC 拓展（当然，也可以选择不使用 OpenCC）

### OpenCC
在之前生成歌词的时候（我主要是 Anime 的 Hi-Res 歌曲）一些歌曲名字里面含有日本汉字（也就是繁体），但是网易上面是简体，所以就会匹配不到，所以转换一下，增大匹配到的几率

### PHP 环境搭建
Windows 推荐 WAMP  
Mac 推荐 XAMPP  
Linux 自己搭

### 匹配精度
歌曲名字和艺术家名字最小匹配精度 0（无限制），最大匹配精度 100（完全匹配），不需要 %  
歌曲时长偏移量，0（时长完全一致），最大误差半分钟，前后误差 N 秒以内（以本地歌曲时长作为标准值，API获取到的时长上做增减），不需要 s

### Node.js 版 网易云音乐 API
https://github.com/Binaryify/NeteaseCloudMusicApi  

### PHP OpenCC Win 版编译
https://github.com/NauxLiu/opencc4php/pull/16

### PHP OpenCC Linux 安装
想看屁话少的教程本人网站有，不想请自行 百度、Google

### getID3
http://getid3.sourceforge.net/<br>
下载后解压到和脚本同级目录，文件夹命名为：getid3（路径在脚本229行，请自行修改）
