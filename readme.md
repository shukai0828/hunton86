# 恒拓礼品站信息 #

---
## 参考模板 ##
1. [Crisp-cool](http://bombdiggitydesign.com/crisp/Crisp-cool/index.html)

---
## 图片类型及组织结构 ##

### 图片类型 ###
1. 产品图
- 原图，900*675，产品名-lrg.jpg
- 产品页展示图，700*525，产品名.jpg
- 产品页缩略图，100*75，产品名-sm.jpg
1. 产品分类图
- 首页底部缩略图，300*100，分类名-ism.png
- 首页滚动展示图，X*350，宽度不限
1. 二级分类图
- 列表页缩略图，300*Y，高度不限，产品名-sm.jpg

### 目录结构 ###
为配合Dede系统里为此模板自定义的文章类型，并且为了便于日常的管理，需要按如下结构组织图片。

* category-name1 // 拼音或单词，必须跟Dede栏目发布目录名称保持一致
 * index.png  // 用于首页滚动效果的背景图，高350像素，宽度不限，类型不限
    * product-name1 // 拼音或单词
     * list.jpg // 用于分类列表页的缩略图，宽300像素，高度不限，类型不限，一般把1-lrg.jpg的宽度等比例缩小到300像素
     * 1.jpg // 用于产品展示页的预览图，宽700像素，高525像素，类型不限，但要跟sm、lrg保持一致
     * 1-sm.jpg // 用于产品展示页的缩略图，宽100像素，高75像素
     * 1-lrg.jpg // 用于产品展示页的原图展示，宽900像素，高675像素
     * 2.jpg
     * 2-sm.jpg
     * 2-lrg.jpg
    * product-name2
     * list.jpg
     * 1.jpg
     * 1-sm.jpg
     * 1-lrg.jpg
     * 2.jpg
     * 2-sm.jpg
     * 2-lrg.jpg
* category-name2
 * index.png
    * product-name
     * list.jpg
     * 1.jpg
     * 1-sm.jpg
     * 1-lrg.jpg
     * 2.jpg
     * 2-sm.jpg
     * 2-lrg.jpg

注意事项：

1. 位于product_name目录下的图片类型除list文件外要完全保持一致
1. 每个产品图片必须同时具备sm和lrg图
1. 图片名称的排序必须从1开始，顺序递增，中间不能有中断，比如不允许1、3、4
2. 每个栏目的index.png需要移动或复制到栏目发布目录中，便于首页slider引用

---
## 产品分类 ##

下述分类说明里，一级分类名称后括号里面的内容为现在设定的图片目录名称，二级分类名称后括号里面的内容为具体作品的大类属性

* 生活用品（shenghuoyongpin）
* 饰品配件（shipinpeijian）
* 衣帽服装（yimaofuzhuang）
* 电子产品（dianzichanpin）
* 办公用品（bangongyongpin）

---
## Dede特殊配置 ##

### 创建频道内容模型 ###

在“核心->频道模型->内容模型管理”里面点击“增加新模型”。

* 基本设置
 1. 设定“频道名称”为“crisp_portfolio_single”
 1. 设定“文字标识”为“crisp_portfolio_single”
 1. 设定“附加表”名为“dede_crisp_portfolio_single”
 1. 其它值默认即可
* 字段管理
 1. 增加字段carousel，类型为“图片(仅网址)”，用于存储图片在网站的位置
 2. 增加字段carousel_num，类型为“整数类型”，用于存储展示在商品页上的图片数量
 3. 增加字段content，类型为“多行文本”，用于存储商品介绍性信息

### 修改pagelist的处理结果 ###

Dede默认的分页代码跟Crisp模板不匹配，需要进行修改。
将Dede安装目录下的include/arc.listview.class.php文件第1039行：

`$listdd.= "<li class=\"thisclass\">$j</li>\r\n";`

修改为：

`$listdd.= "<li class=\"active\"><span>$j</span></li>\r\n";`

### 增加首页标题 ###

在“系统->系统基本参数”里面点击“添加新变量”。

1. 变量名称：index_main_title
2. 变量值：根据实际需要填写
3. 变量类型：文本
4. 变量说明：用于保存在系统首页显示的主标题
5. 所属组：系统设置

### 上传图片 ###

1. 在upload目录下创建product目录
1. 将按照“图片类型及组织结构”要求准备好的图片复制到upload的product目录下

### 创建栏目 ###

1. 设定栏目的类型为：crisp_portfolio_single
2. 将upload/product下每个分类的index.png图片复制到该栏目的发布目录下

---
## 常用操作命令 ##

`
{dede:php}
file_put_contents("C:/wnmp/nginx1.3.6/html/dede57/a/varIndexGlobal.txt",print_r($GLOBALS, TRUE));
file_put_contents("C:/wnmp/nginx1.3.6/html/dede57/a/varIndexRefObj.txt",print_r($refObj, TRUE));
{/dede:php}
`

---
## 几个问题 ##

1. 列表页按特征筛选需要做二级分类或筛选分类
2. 首页底部的文字域怎么处理
3. 标准尾的信息提供
