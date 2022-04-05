## Python版植物大战僵尸

植物大战僵尸游戏的Python实现
  
`本项目为个人python语言学习所用的练习项目，仅供个人学习和研究使用，不得用于其他用途。如果这个游戏侵犯了版权，请联系我删除`
  
* 已有的植物：向日葵，豌豆射手，坚果墙，寒冰射手，樱桃炸弹，三线射手，大嘴花，小喷菇，土豆雷，地刺，胆小菇，倭瓜，火爆辣椒，阳光菇，寒冰菇，魅惑菇
* 已有的僵尸：普通僵尸，旗帜僵尸，路障僵尸，铁桶僵尸，读报僵尸
* 使用 JSON 格式的文件存储进度数据 (例如僵尸出现的位置和时间，背景信息)
* 支持选择植物卡片
* 支持白昼模式，夜晚模式，传送带模式和坚果保龄球模式
* 支持背景音乐播放
* 支持全屏模式
  * 按`F`键进入全屏模式，按`U`键恢复至窗口模式

## 环境要求

* `Python` >= 3.7 
* `Python-Pygame` >= 1.9

## 开始游戏

### 使用仓库源代码

```shell
python main.py
```

### 使用Windows可执行文件

在本仓库的`Release`页面中下载`pypvz.exe`文件，双击运行即可

## 方法

* 使用鼠标收集阳光,种植植物
* 你可以通过更改`source/constants.py`中的`START＿LEVEL＿NUM`的数值来更改起始关卡：
  * 冒险模式：
    * 1 和 2：白昼模式
    * 3：夜晚模式
  * 小游戏模式：
    * 1：传送带模式
    * 2：坚果保龄球模式
* **注意：目前单文件发布版本不支持自定义调整关卡**

## Windows单文件封装

编译依赖：
- `Python` >= 3.7
- `Python-Pygame` >= 1.9
- `Nuitka`
- `MinGW-w64`（或其他C编译器）
- `ccache`
- `depends`
- `python-zstandard`（可选）

**在编译环境安装不全时，Nuitka可以自动安装MinGW-w64、ccache和depends**

在仓库所在文件夹执行：

``` powershell
nuitka --mingw --standalone --onefile --show-progress --show-memory --windows-disable-console --output-dir=out --windows-icon-from-ico=pypvz.ico --include-data-dir=resources=resources main.py
```

加了背景音乐播放功能之后需要执行：

``` powershell
nuitka --mingw --standalone --onefile --show-progress --show-memory --output-dir=out --windows-icon-from-ico=pypvz.ico --include-data-dir=resources=resources --include-data-file=C:\Users\17265\AppData\Local\Programs\Python\Python310\Lib\site-packages\pygame\libogg-0.dll=libogg-0.dll --include-data-file=C:\Users\17265\AppData\Local\Programs\Python\Python310\Lib\site-packages\pygame\libopus-0.dll=libopus-0.dll --include-data-file=C:\Users\17265\AppData\Local\Programs\Python\Python310\Lib\site-packages\pygame\libopusfile-0.dll=libopusfile-0.dll --windows-disable-console main.py
```

* 其中`C:\Users\17265\AppData\Local\Programs\Python\Python310\Lib\site-packages\pygame\*.dll`应当替换为`*.dll`实际所在路径，当然
* 由于仅复制了opus的解码器，故要求所有背景音乐都要以opus编码

可执行文件生成路径为`./out/main.exe`

## 计划（不保证实施）：

### 长期

* 增加保存数据文件以存储用户进度的功能
* 更改僵尸生成方式
  * 使僵尸生成更随机化，由JSON记录改为随机数生成
* 增加更多植物、僵尸类型与游戏功能、模式，尽量符合原版基本设计

### 短期

* 给胜利和失败界面添加音乐
* 修复已经死亡的僵尸会触发大嘴花、土豆雷甚至小推车的问题
* 用蓝色滤镜标识冷冻的僵尸
* 修复暂停游戏时仍在计时的bug
* 修复魅惑菇的bug

## 截屏

![截屏1](/demo/demo1.webp)
![截屏2](/demo/demo2.webp)
![截屏3](/demo/demo3.webp)
![截屏4](/demo/demo4.webp)
![截屏5](/demo/demo5.webp)
![截屏6](/demo/demo6.webp)

## 开源协议

本软件代码采用[GPL v3](https://www.gnu.org/licenses/gpl-3.0.html)协议开源