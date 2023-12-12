# Marvelous

> **这是一个用于给照片批量添加水印、处理照片像素比、图像色彩和质量的工具。**



### macOS/Linux

#### 使用 git

- **安装需要的依赖（正式运行前执行一次即可）**

  打开命令行/终端，输入：

  ```shell
  # 使用 git 将代码下载到本地，比如 ~/Marvelous，如果要下载到其他路径替换掉下面命令中的路径即可
  git clone --depth 1 git@github.com:wscffaa/Marvelous.git ~/Marvelous
  cd ~/Marvelous
  chmod +x install.sh
  ./install.sh
  ```

  > 你可以按下 command+空格键，打开 Spotlight 搜索栏，在搜索栏中输入 `终端` 即可。
  >
  > 如果命令运行出错可以参考 [常见问题](#常见问题)。

- 将需要添加水印的图片复制到 `~/Marvelous/input` 文件夹中

- 打开命令行/终端，输入

   ```shell
   cd ~/Marvelous
   python3 ~/Marvelous/main.py
   ```

- 按照提示输入 `y或回车` 开始执行

- 处理好的图片存放在 `~/Marvelous/output` 中

#### 手动下载

<details>
<summary>点击展开</summary>

- 下载[源码](http://file.lsvm.xyz/Marvelous-latest-source.zip)后解压，比如解压到 `~/Marvelous`，路径需要自行替换。

   > 你可以右键单击解压后的文件夹，按住 Opt 键-选择将xxx拷贝为路径名称 ，用剪贴板中的实际路径替换下面命令中的 `~/Marvelous`.

- **安装需要的依赖（正式运行前执行一次即可）**

   打开命令行/终端，输入：

   ```shell
   cd ~/Marvelous
   chmod +x install.sh
   ./install.sh
   ```

   > 你可以按下 command+空格键，打开 Spotlight 搜索栏，在搜索栏中输入 `终端` 即可。
   >
   > 如果命令运行出错可以参考 [常见问题](#常见问题)。

- 将需要添加水印的图片复制到 `~/Marvelous/input` 文件夹中

- 打开命令行/终端，输入

   ```shell
   cd ~/Marvelous
   python3 ~/Marvelous/main.py
   ```

- 按照提示输入 `y或回车` 开始执行

- 处理好的图片存放在 `~/Marvelous/output` 中


</details>

## 配置项

通过 `config.yaml` 配置。

<details>
<summary>点击展开</summary>

```yaml
base:
  alternative_bold_font: ./fonts/Roboto-Medium.ttf
  alternative_font: ./fonts/Roboto-Regular.ttf
  # 粗体
  bold_font: ./fonts/AlibabaPuHuiTi-2-85-Bold.otf
  # 粗体字体大小
  bold_font_size: 1
  # 常规字体
  font: ./fonts/AlibabaPuHuiTi-2-45-Light.otf
  # 常规字体大小
  font_size: 1
  # 输入文件夹
  input_dir: ./input
  # 输出文件夹
  output_dir: ./output
  # 输出图片质量，如果你觉得输出图片的体积过大，比如一张20M的图片，处理后变成了40M，那么你可以通过适当降低输出质量来减小图片体积
  quality: 100
global: # 全局设置，你可以在命令行中通过【更多设置】来修改这些设置
  focal_length:
    # 是否使用等效焦距
    use_equivalent_focal_length: false
  padding_with_original_ratio:
    # 是否使用原始图片的宽高比来填充白边
    enable: false
  shadow:
    # 是否使用阴影
    enable: false
  white_margin:
    # 是否使用白边
    enable: true
    # 白边宽度
    width: 3
layout:
  # 背景颜色，仅在布局为 normal（自定义）时有效
  background_color: '#ffffff'
  elements:
    # 左下角元素
    left_bottom:
      # 左下角文字颜色，仅在布局为 normal（自定义）时有效
      color: '#757575'
      # 是否使用粗体，仅在布局为 normal（自定义）时有效
      is_bold: false
      # 左下角文字内容，可选项参考下表
      name: Model
    # 下面三个元素的设置和上面是类似的
    left_top:
      color: '#212121'
      is_bold: true
      name: LensModel
    right_bottom:
      color: '#757575'
      is_bold: false
      name: Datetime
      value: Photo by NONE
    right_top:
      color: '#212121'
      is_bold: true
      name: Param
  # 是否使用 Logo，仅在布局为 normal（自定义）时有效，可选项为 true、false
  logo_enable: false
  # Logo 位置，仅在布局为 normal（自定义）时有效，可选项为 left、right
  logo_position: left
  # 布局类型，可选项参考下表，你可以在命令行中通过【布局】来修改它
  type: watermark_right_logo
logo:
  makes:
    canon: # 标识，用户自定义，不要重复
      id: Canon # 厂商名称，从 exif 信息中获取，和 exif 信息中的 Make 字段一致即可
      path: ./logos/canon.png # Logo 路径
    # 下同
    fujifilm:
      id: FUJIFILM
      path: ./logos/fujifilm.png
    hasselblad:
      id: HASSELBLAD
      path: ./logos/hasselblad.png
    huawei:
      id: HUAWEI
      path: ./logos/xmage.jpg
    leica:
      id: leica
      path: ./logos/leica_logo.png
    nikon:
      id: NIKON
      path: ./logos/nikon.png
    olympus:
      id: Olympus
      path: ./logos/olympus_blue_gold.png
    panasonic:
      id: Panasonic
      path: ./logos/panasonic.png
    pentax:
      id: PENTAX
      path: ./logos/pentax.png
    ricoh:
      id: RICOH
      path: ./logos/ricoh.png
    sony:
      id: SONY
      path: ./logos/sony.png

```

### Layout.Element.Name 可选项

| 可选项                   | 描述                             |
|-------------------------|----------------------------------|
| Model                   | 相机型号(eg. Nikon Z7)            |
| Make                    | 相机厂商(eg. Nikon)               |
| LensModel               | 镜头型号(eg. Nikkor 24-70 f/2.8)  |
| Param                   | 拍摄参数(eg. 50mm f/1.8 1/1000s ISO 100) |
| Datetime                | 拍摄时间(eg. 2023-01-01 12:00)   |
| Date                    | 拍摄日期(eg. 2023-01-01)         |
| Custom                  | 自定义                           |
| None                    | 无                               |
| LensMake_LensModel      | 镜头厂商 + 镜头型号(eg. Nikon Nikkor 24-70 f/2.8) |
| CameraModel_LensModel   | 相机型号 + 镜头型号(eg. Nikon Z7 Nikkor 24-70 f/2.8) |
| TotalPixel              | 总像素(MP)                       |
| CameraMake_CameraModel | 相机厂商 + 相机型号(eg. DJI FC123) |

### Layout.Type 可选项

| 可选项                      | 描述                                   | 效果                              |
|---------------------------|----------------------------------------|-----------------------------------|
|watermark_left_logo|normal|![1](images/1.jpeg)|
|watermark_right_logo|normal(Logo 居右)|![2](images/2.jpeg)|
|dark_watermark_left_logo|normal(黑红配色)|![3](images/3.jpeg)|
|dark_watermark_right_logo|normal(黑红配色，Logo 居右)|![4](images/4.jpeg)|
|custom_watermark|normal(自定义配置)|![5](images/5.jpeg)|
|square|1:1填充|![6](images/6.jpeg)|
|simple|简洁|![7](images/7.jpeg)|
|background_blur|背景模糊|![8](images/8.jpeg)|
|background_blur_with_white_border|背景模糊+白框|![9](images/9.jpeg)|

</details>

