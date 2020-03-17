# 游宁小程序接口

[TOC]

## 用户模块

### 1. 显示

### 2. 查询

### 3.方法是

## 商品模块

### 1. 显示商品表里的所有的商品信息

+ URL = <http://localhost:8080/wxssm/Goods/selectAllGoodsInfo>
+ 支持格式：JSON
+ HTTP 请求方式 ：GET
+ 请求参数

>参数 | 类型 | 说明
>:-:|:-:|:-:
>无 |   |  

+ 返回参数【Goods类型】

>参数 | 类型 | 说明
>:-:|:-:|:-:
>goodsId |String | 商品id
>goodsName |String | 商品名称
>introduce |String | 商品介绍
>goodsPrice |Float | 商品价格
>firstLabel |String | 商品一级标签
>secondLabel |String | 商品二级标签
>oldOrNew |String | 商品新旧
>clickNumber | int | 点击查看量
>releaseTime |String | 上架时间
>sellTime |String | 出售时间
>goodsPictures . pictureId | String | 商品的每一个图片的id
>goodsPictures . address | String | 图片的地址
>goodsPictures . pictureNumber | String | 图片的序号

+ 返回数据实示例

```JSON
[
    {
        "goodsId": "1110",
        "goodsName": "iPhone xr",
        "introduce": "18年iphone XR 表面无磨损，长期贴膜，电池寿命98%，边缘有极小磨损",
        "goodsPrice": 3500.0,
        "firstLabel": "手机",
        "secondLabel": "iPhone",
        "oldOrNew": "旧",
        "clickNumber": 2,
        "releaseTime": "2020-02-15 19:39:16",
        "sellTime": null,
        "goodsComment": null,
        "goodsCommentTime": null,
        "goodsBooleanSell": false,
        "goodsPictures": []
    },
    {
        "goodsId": "1121",
        "goodsName": "联想Y7000 8G内存 128G固态硬盘 2T机械硬盘",
        "introduce": "2018年中秋节购买，整体无磕碰，自行升级了内存，现在是32G内存",
        "goodsPrice": 5555.0,
        "firstLabel": "数码",
        "secondLabel": "电脑",
        "oldOrNew": "旧",
        "clickNumber": 0,
        "releaseTime": "2020-02-15 22:44:27",
        "sellTime": null,
        "goodsComment": null,
        "goodsCommentTime": null,
        "goodsBooleanSell": false,
        "goodsPictures": [
            {
                "pictureId": "1",
                "goodsId": "1121",
                "address": "wechatapp-youning.oss-cn-hangzhou.aliyuncs.com/Goods/058d66e6c7c34027995e4a0d8e8dcb4c.png",
                "pictureNumber": 0
            }
        ]
    }
]
```

> 注：

### 2. 通过商品Id查单个商品的所有信息

+ URL = <http://localhost:8080/wxssm/Goods/byGoodsIdSelectGoodsInfo>
+ 支持格式：JSON
+ HTTP 请求方式 ：GET
+ 请求参数

>参数 | 类型 | 说明
>:-:|:-:|:-:
>goodsId | String | 商品Id，商品编号

+ 返回参数【Goods类型】

>参数 | 类型 | 说明
>:-:|:-:|:-:
>goodsId |String | 商品id
>goodsName |String | 商品名称
>introduce |String | 商品介绍
>goodsPrice |Float | 商品价格
>firstLabel |String | 商品一级标签
>secondLabel |String | 商品二级标签
>oldOrNew |String | 商品新旧
>clickNumber | int | 点击查看量
>releaseTime |String | 上架时间
>sellTime |String | 出售时间
>goodsComment | String | 商品的评论
>goodsCommentTime | String | 被评论时间
>goodsBooleanSell | Stirng |状态值 =【在售、下架、商家编辑中】
>goodsPictures . pictureId | String | 商品的每一个图片的id
>goodsPictures . address | String | 图片的地址
>goodsPictures . pictureNumber | String | 图片的序号

+ 返回数据实示例

```JSON
{
    "goodsId": "1121",
    "goodsName": "联想Y7000 8G内存 128G固态硬盘 2T机械硬盘",
    "introduce": "2018年中秋节购买，整体无磕碰，自行升级了内存，现在是32G内存",
    "goodsPrice": 5555.0,
    "firstLabel": "数码",
    "secondLabel": "电脑",
    "oldOrNew": "旧",
    "clickNumber": 0,
    "releaseTime": "2020-02-15 22:44:27",
    "sellTime": null,
    "goodsComment": null,
    "goodsCommentTime": null,
    "goodsBooleanSell": "在售",
    "goodsPictures": [
        {
            "pictureId": "1",
            "goodsId": "1121",
            "address": "wechatapp-youning.oss-cn-hangzhou.aliyuncs.com/Goods/058d66e6c7c34027995e4a0d8e8dcb4c.png",
            "pictureNumber": 0
        }
    ]
}
```

> 注：

### 3. 根据商品名称返回相关的商品信息,按照选项排序

+ URL = <http://localhost:8080/wxssm/Goods/byGoodsNameSelectGoods>
+ 支持格式：JSON
+ HTTP 请求方式 ：GET
+ 请求参数

>参数 | 类型 | 说明
>:-:|:-:|:-:
>goodsName | String | 帖子名称
>orderByOldOrNew | String | 根据新旧排序【可选项，三选一】{'全新','九成新','旧'}
>orderByPrice | String | 根据价格排序【可选项，三选一】{'ASC','DESC'}
>orderByTime | String | 根据时间排序【可选项，三选一】{'ASC','DESC'}
---

>+ 'ASC' = 升序
>+ 'DESC' = 降序

+ 返回参数【Goods类型】

>参数 | 类型 | 说明
>:-:|:-:|:-:
>goodsId |String | 商品id
>goodsName |String | 商品名称
>introduce |String | 商品介绍
>goodsPrice |Float | 商品价格
>firstLabel |String | 商品一级标签
>secondLabel |String | 商品二级标签
>oldOrNew |String | 商品新旧
>clickNumber | int | 点击查看量
>releaseTime |String | 上架时间
>sellTime |String | 出售时间
>goodsComment | String | 商品的评论
>goodsCommentTime | String | 被评论时间
>goodsBooleanSell | Stirng |状态值 =【在售、下架、商家编辑中】
>goodsPictures.pictureId | String | 商品的每一个图片的id
>goodsPictures.address | String | 图片的地址
>goodsPictures.pictureNumber | String | 图片的序号

+ 返回数据实示例

```JSON
[
    {
        "goodsId": "1121",
        "goodsName": "联想Y7000 8G内存 128G固态硬盘 2T机械硬盘",
        "introduce": null,
        "goodsPrice": 5555.0,
        "firstLabel": null,
        "secondLabel": null,
        "oldOrNew": "旧",
        "clickNumber": 0,
        "releaseTime": "2020-02-15 22:44:27",
        "sellTime": null,
        "goodsComment": null,
        "goodsCommentTime": null,
        "goodsBooleanSell": null,
        "goodsPictures": [
            {
                "pictureId": "1",
                "goodsId": "1121",
                "address": "wechatapp-youning.oss-cn-hangzhou.aliyuncs.com/Goods/058d66e6c7c34027995e4a0d8e8dcb4c.png",
                "pictureNumber": 0
            }
        ]
    }
]
```

> 注：无

### 4. 发布商品

+ URL = <http://localhost:8080/wxssm/Goods/insertGoods>
+ 支持格式：JSON
+ HTTP 请求方式 ：POST
+ 请求参数【Goods类型】

>参数 | 类型 | 说明
>:-:|:-:|:-:
>goodsName |String | 商品名称
>introduce |String | 商品介绍
>goodsPrice |Float | 商品价格
>firstLabel |String | 商品一级标签
>secondLabel |String | 商品二级标签
>oldOrNew |String | 商品新旧
>file | MultipartFile[] | file是数组，可上传多图。

+ 返回参数

>参数 | 类型 | 说明
>:-:|:-:|:-:
>GoodsId | String | 商品id

+ 返回数据实示例

```JSON
1121
```

> 注：

### 5. 通过商品的goodsID更新数据

+ URL = <http://localhost:8080/wxssm/Goods/updateGoodsInfo>
+ 支持格式：JSON
+ HTTP 请求方式 ：GET
+ 请求参数

>参数 | 类型 | 说明
>:-:|:-:|:-:
>goodsId |String | 商品id
>goodsName |String | 商品名称
>introduce |String | 商品介绍
>goodsPrice |Float | 商品价格
>firstLabel |String | 商品一级标签
>secondLabel |String | 商品二级标签
>oldOrNew |String | 商品新旧
>clickNumber | int | 点击查看量
>releaseTime |String | 上架时间
>sellTime |String | 出售时间
>goodsComment | String | 商品的评论
>goodsCommentTime | String | 被评论时间
>goodsBooleanSell | Stirng |状态值 =【在售、下架、商家编辑中】
>goodsPictures.pictureId | String | 商品的每一个图片的id
>goodsPictures.address | String | 图片的地址
>goodsPictures.pictureNumber | String | 图片的序号

+ 返回参数【Post类型】

>参数 | 类型 | 说明
>:-:|:-:|:-:
>postId | String | 帖子id

+ 返回数据实示例

```JSON

```

> 注：

### 6

+ URL = <http://localhost:8080/wxssm/Goods/byPostIdSelectPostInfo>
+ 支持格式：JSON
+ HTTP 请求方式 ：GET
+ 请求参数

>参数 | 类型 | 说明
>:-:|:-:|:-:
>postId | String | 帖子id

+ 返回参数【Post类型】

>参数 | 类型 | 说明
>:-:|:-:|:-:
>postId | String | 帖子id

+ 返回数据实示例

```JSON

```

> 注：

## 帖子模块

### 1. 通过帖子编号得到帖子相关信息

+ URL = <http://localhost:8080/wxssm/Post/byPostIdSelectPostInfo>
+ 支持格式：JSON
+ HTTP 请求方式 ：GET
+ 请求参数

>参数 | 类型 | 说明
>:-:|:-:|:-:
>postId | String | 帖子id

+ 返回参数【Post类型】

>参数 | 类型 | 说明
>:-:|:-:|:-:
>postId | String | 帖子id

+ 返回数据实示例

```JSON

```

> 注：

### 2. 按照帖子先后发布顺序显示帖子

+ URL = <http://localhost:8080/wxssm/Post/byPostIdSelectPostInfo>
+ 支持格式：JSON
+ HTTP 请求方式 ：GET
+ 请求参数

>参数 | 类型 | 说明
>:-:|:-:|:-:
>postId | String | 帖子id

+ 返回参数【Post类型】

>参数 | 类型 | 说明
>:-:|:-:|:-:
>postId | String | 帖子id

+ 返回数据实示例

```JSON

```

> 注：

### 3. 通过热度(评论数量)显示帖子来先后显示帖子信息

### 4. 发布帖子

### 5. 发布帖子评论

### 6. 通过帖子Id删除一个帖子
