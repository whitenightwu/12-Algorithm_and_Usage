# coco
COCO common objects Dataset(Common Objects in Context)
COCO数据集由微软赞助，其对于图像的标注信息不仅有类别、位置信息，还有对图像的语义文本描述，COCO数据集的开源使得近两三年来图像分割语义理解取得了巨大的进展，也几乎成为了图像语义理解算法性能评价的“标准”数据集。



有三大子集
1）目标检测（COCO Detection Challenge），包含两项比赛：用于目标检测、语义分割
2）图像标注（COCO Captioning Challenge） 
具体说来就是一句话准确描述图片上的信息（producing image captions that are informative and accurate）。那这个怎么评分呢？目前是靠人工评分
3）人体关键点检测（COCO Keypoint Challenge） 
比赛要求是找到人在哪，然后定位到人体的一些关键点位置（The keypoint challenge involves simultaneously detecting people and localizing their keypoints）

如下特点：
1）Object segmentation
2）Recognition in Context
3）Multiple objects per image
4）More than 300,000 images
5）More than 2 Million instances
6）80 object categories
7）5 captions per image
8）Keypoints on 100,000 people

## 格式解析
### segmentation字段
coco的segment格式有两种，RLE和polygon。主要是RLE（RunLengthEncoding），更省存储空间，并且可以编码压缩。
对于mask数据，不如VOC直观。因为coco中的mask是polygon来表示的，遇到环形物体就只能“将polygon一个一个画在mask上，相当于通过有个默认排序来生成mask，后面的polygon会更改之前的mask”。
见https://github.com/cocodataset/cocoapi/blob/8c9bcc3cf640524c4c20a9c40e89cb6a2f2fa0e9/common/maskApi.c#L49的merge函数。


### bbox字段
x, y, w, h

