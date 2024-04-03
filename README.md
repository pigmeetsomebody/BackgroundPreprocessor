# 1. 安装Python依赖
```
cd <BackgroundPreprocessor >
source <CondaRoot>/bin/activate
conda create -n background_processor python=3.9
conda activate background_processor
conda install conda-forge::ffmpeg # ffmpeg with libx264 codec to turn images to video

# 其他依赖项
pip install -r docs/prepare_env/requirements.txt -v
```
# 2. 推理测试
- 需要换背景的原图片所在的文件夹
- 背景图片文件夹
例如，需要替换背景的图片在`./images_512`文件夹下，其中有一张图片`test.png`, 存放对应的背景图片的文件夹为`./bg_img`, 文件夹下是待换背景图片对应的背景，注意待换背景图片的名称要与背景文件夹同名，程序会自动进行匹配，生成待换背景图片换背景后的所有图片，生成结果的图片存在`./results/com_imgs`文件夹下

##  命令行推理
```
cd BackgroundPreprocessor
conda activate background_processor
export PYTHON_PATH=./
python ./utils/process_image/extract_segment_imgs.py \
--img_dir ./images_512 \
----bg_dir ./bg_img \
--person_scale 0.8 \
```

### 一些可选参数注释：
`img_dir`: 源图片（.png）所在文件夹
`bg_dir`: 背景文件夹，其子文件夹要跟图片名对应
`person_scale`： 人物缩放比例