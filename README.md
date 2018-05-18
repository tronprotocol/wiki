[![Documentation Status](https://readthedocs.org/projects/tron-wiki/badge/?version=latest)](http://tron-wiki.readthedocs.io/en/latest/?badge=latest)
                
# TRON Wiki

## Getting Started

The documentation is currently hosted on http://wiki.tron.network

## How to participate

Guide to Wiki file revision

We encourage TRON community members to participate in the revision of our Wiki files regarding their content and format.

1, Sign in to Github. Enter [Wiki repository](https://github.com/tronprotocol/wiki) on TRON Protocol homepage and create a new fork.

![](https://raw.githubusercontent.com/ybhgenius/wiki/master/images/fork.jpg)

2, Clone the Wiki repository to your local repository.

![](https://raw.githubusercontent.com/ybhgenius/wiki/master/images/clone.jpg)

3, Submit your revised file to future branch in Wiki repository.

![](https://raw.githubusercontent.com/ybhgenius/wiki/master/images/future.jpg)

4, Revise the existing files or create new files in the docs folder. Save images to the img folder in the docs folder.

![](https://raw.githubusercontent.com/ybhgenius/wiki/master/images/docs.jpg)

5, Submit your revised file to the future branch in Wiki repository.

**Notes**

1.	Before getting down to revision, please first make sure you know how to [configure Git](https://help.github.com/articles/set-up-git/) and [create repository](https://guides.github.com/activities/forking/). Mac users can download Git [here](https://desktop.github.com).

2.	Before getting down to revision, please also acquaint yourself with [RST grammar](http://docutils.sourceforge.net/docs/user/rst/quickref.html) and the document generator [Sphinx](http://www.sphinx-doc.org/en/master/).

3.	Once you’ve completed your revision, please submit it to the future branch in Wiki repository.

4.	Please make sure to revise the existing files or create new files in docs folder.

对于不了解Sphinx的用户，我们希望你们直接参与到文档内容的修改，而无需关注文章排版以及展现形式。只需关注docs文件里的所有rst文档，不必对wiki文件夹的其他文件进行修改。

在docs文件下，请注意以下几点：

1. 请不要删除和改动rst格式以外的其他文档，比如conf.py，index.html，Makefile等等。

2. 通过修改index.rst文档内容可以直接改变文档目录。

![]()

3. 针对单一rst文档。

+ ====表示一级标题。----表示二级标题。~~~~表示三级标题。
+ ====下的标题可以通过改变index.rst内容改变文档的总目录形式。
+ ----与~~~~下的标题用来改变对单一rst文档目录展现形式。

![]()