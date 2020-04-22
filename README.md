# 3D InPainiting Demo

#### To try it on your own, follow these steps

- **Prepare environment**

```python
!pip install -r requirements.txt
```

```python
!pip install torch==1.4.0+cu100 torchvision==0.5.0+cu100 -f https://download.pytorch.org/whl/torch_stable.html
```

```python
!sudo apt install sed
```

- **Download script and pretrained model**

```python
%cd /content/
!git clone https://github.com/vt-vl-lab/3d-photo-inpainting.git
%cd 3d-photo-inpainting
!sh download.sh
```
- **Switch off off-screen rendering**

```python
!sed -i 's/offscreen_rendering: True/offscreen_rendering: False/g' 3d-photo-inpainting/argument.yml
```

- **Please upload `.jpg` files to `/content/3d-photo-inpainting-master/image/`**
  - You can run this step multiple times to upload multiple `.jpg` files.

```python
%cd 3d-photo-inpainting/image
from google.colab import files
uploaded = files.upload()
for fn in uploaded.keys():
  print('User uploaded file "{name}" with length {length} bytes'.format(
      name = fn, length = len(uploaded[fn])))
%cd ..
```

- **Execute the 3D Photo Inpainting**

```python
!python main.py --config argument.yml
```

#### References

```
@inproceedings{Shih3DP20,
  author = {Shih, Meng-Li and Su, Shih-Yang and Kopf, Johannes and Huang, Jia-Bin},
  title = {3D Photography using Context-aware Layered Depth Inpainting},
  booktitle = {IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
  year = {2020}
}
```
