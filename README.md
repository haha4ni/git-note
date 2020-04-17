# Git指令懶人大補帖

@(筆記)[Haha|Markdown]

**马克飞象**是一款专为印象笔记（Evernote）打造的Markdown编辑器，通过精心的设计与技术实现，配合印象笔记强大的存储和同步功能，带来前所未有的书写体验。特点概述：
 
- **功能丰富** ：支持高亮代码块、*LaTeX* 公式、流程图，本地图片以及附件上传，甚至截图粘贴，工作学习好帮手；
- **深度整合** ：支持选择笔记本和添加标签，支持从印象笔记跳转编辑，轻松管理。

-------------------
### 功能指令

#### 內建圖形化分支工具
``` C++
gitk --all
```
#### 設定上傳名稱與Email
``` C++
git config --global user.name "name"
git config --global user.email "email"
```

#### 查詢狀態
``` C++
git status
```

-------------------
###上傳四大步驟
#### 初始化
使用`init`來建立新環境以及使用`clone`去拷貝遠端Repository
``` C++
git clone <repository url>
```
#### 加入暫存區
``` C++
//兩者一樣
git add --all
git add .
```
#### 加入本地資料庫
```C++
git commit -m "comment"
```

#### 加入遠端資料庫
```C++
git push -u origin master
git push origin local_master:global_master//推上不同分支名稱

-u : 紀錄要推上去的位置，下次只需要打git push
```

-------------------
### 分支處理
```C++
git checkout <branch>
切換分支
git checkout -b <branch>
-b : 如果沒有就創建新分支

git branch
目前分支查看

git branch <branch>
新增分支

git branch <branch> <SHA-1>
新增分支指向SHA-1

git branch -m <old_branch> <new_branch>
修改分支名稱

git merge <branch>
與目標分支合併進來



git branch -d <branch>
刪除分支


```


-------------------
### 遠端設定
```C++
git remote add origin https://github.com/haha4ni/GitNote.git
加入一個遠端的節點，origin 是遠端資料庫的代名詞，指的是後面那串 GitHub 伺服器的位置
取什麼名字都沒關係
```

### GitHab相關設定




### CMD指令補帖
```C++
echo "# GitNote" >> README.md
```



[^demo]: 这是一个示例脚注。请查阅 [MultiMarkdown 文档](https://github.com/fletcher/MultiMarkdown/wiki/MultiMarkdown-Syntax-Guide#footnotes) 关于脚注的说明。 **限制：** 印象笔记的笔记内容使用 [ENML][5] 格式，基于 HTML，但是不支持某些标签和属性，例如id，这就导致`脚注`和`TOC`无法正常点击。


  [1]: https://gitbook.tw/
  [2]: 

