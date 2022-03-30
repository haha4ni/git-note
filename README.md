# Git指令懶人大補帖

1、2、3，**Git**指令豪簡單。


-------------------
## 上傳四大步驟
1. 建立存儲庫 (init/clone)
2. 加入至暫存區 (add)
3. 上傳至本地儲存庫 (commit)
4. 上傳至遠端儲存庫 (push)
5. 從遠端儲存庫更新至本地儲存庫 (pull)

### 建立存儲庫
使用`init`來建立新環境
```python
git init
```
或者使用`clone`去拷貝遠端Repository
```python
git clone <repository url>
```
### 加入暫存區
```python
git add <file>

git add --all
# --all or -A or . :
# 加入路徑內全部檔案
```
### 加入本地資料庫
```python
git commit -m "comment"

# -m or -message :
# 使用指定的註解
```

### 加入遠端資料庫
```python
git remote add origin <repository url>
# 如果是用init來創建repo, 需要先定義remote位置
# 此行的意思是, 遠端的repo(github)地址使用origin來代稱

git push origin <local_branch>
git push origin <local_branch:global_branch>
# 只打<local_branch>默認為與global branch同名稱

git push -u origin <local_branch>
# -u :
# 紀錄要推上去的地址(origin), 下次只需要打git push
```



-------------------
## 更新相關
### git status
查詢狀態
```python
git status
```

### git pull
```python
git pull
# pull是兩個指令的結合
# git fetch + git merge origin/master

git pull --rebase
# --rebase :
# git就會用rebase來解conflict, 預設是用merge來合併
# git fetch oirgin
# git rebase remotes/github/master
```

### git fetch
同步遠端分支
```python
git fetch <remote>
# <remote> : 
# ex. origin

git fetch --all
# --all :
# 更新全部遠端分支
```

### git rm
移除追蹤的檔案
```python
git rm -r --cached
# --cached :
# 單純不追蹤 檔案還在
# -r :
# 允許批量刪除(資料夾)
```

### git reset
反悔(commit相關操作)
```python
git reset <branch_SHA-1>

git reset --mixed "HEAD^"
# windows的換行符號是^所以要加""
# HEAD : 當下的branch_ID
# ^ : 前一個
	
# --mixed 工作目錄-保留 commit-丟棄 (預設)
# --soft  工作目錄-保留 commit-保留 (回到上一洞但commit出去的不會消失)
# --hard  工作目錄-丟棄 commit-丟棄

git reset --hard HEAD
# 回復到前一版本
```
### git push
```python
git push

git push -u <remote name> <branch name>
# -u, --set-upstream
# 設定 upstream 可以使分支開始追蹤指定的遠端分支

git push origin --delete new_branch 
# 刪除遠端的 branch
```

### git stash
```python
git stash list
git stash pop stash@{2}
git stash apply stash@{0}
git stash drop stash@{0}
# pop 指令看成「apply Stash + drop Stash」。
```

-------------------
## 分支處理


### git checkout
進入指定分支
```python
git checkout <branch>
#會自動下-t 以及從遠端拉取相對應的branch

git checkout -f <branch>
# -f or --force :
# 強拉下來蓋掉本地檔案

git checkout -b <branch>
# -b :
# 如果沒有此分支就創建新分支+進入

git checkout <origin/new_branch> -b <new_branch>
# 建立 local new_branch 並與遠端連接

git checkout -t <remote_branch>
# -t, --track :
# set upstream info for new branch
# 自動建立一個與遠端同名的local branch，並以此local branch追蹤remote branch
# ex : git checkout --track origin/develop
# 沒加上-t參數，則會出現Git HEAD detached的情況。
```

### git branch
分支操作
```python
git branch
# 查看目前分支

git branch -a
# -a :
# 查看全部分支

git branch -r
# 查看遠端分支

git branch <branch>
#新增分支

git branch <branch> <branch_SHA-1>
# 新增分支指向SHA-1

git branch -m <old_branch> <new_branch>
# 修改分支名稱

git merge <branch>
# 與目標分支合併進來

git branch -d <branch>
# 刪除分支


git.exe checkout --no-track -b D13_AIO_Dakar remotes/origin/D13_AIO_Dakar
#不追蹤分支給remote

git branch -vv
#檢查分支追蹤誰(配合遠端用)

git branch -u <remote/branch>
#給當前的本地端分支追蹤遠端分支
```

-------------------
## 衝突處理
```python
衝突發生status會顯示both modified
只要再add一次檔案衝突就會消失


衝突內容
<<<<<<< HEAD
commit 記錄索引的狀態
=======
pull 取得遠端數據庫的內容
>>>>>>> 遠端數據ID


之後須自行修改內容再add一次以解除衝突
```

-------------------
## 遠端設定
```python
git remote add origin https://github.com/haha4ni/GitNote.git
# 加入一個遠端的節點，origin 是遠端資料庫的代名詞，指的是後面那串 GitHub 伺服器的位置
# 取什麼名字都沒關係

git remote rm origin
# 想要修改就先移除
```

-------------------
## 功能指令
### git --version
查看版本

### gitk
內建圖形化查看工具
```Python
gitk  (只顯示自己)
gitk --all  (顯示全部)
```

### git reflog
版本日誌

### git config
設定使用者名稱與Email
```python
git config --list

$ git config user.name
$ git config user.email

git config --global user.name "name"
git config --global user.email "email"
```

### git diff
```python

git diff HEAD
# 工作目錄與最新分支差異
git diff <commit1> <commit2>
# commit id 1舊2新
git diff HEAD^ HEAD
# 比較前一版與最新版

git diff --relative > change.patch
# 只patch當前的工作目錄
```


-------------------
## GitHab相關設定
### SSH Key


-------------------
## CMD指令補帖
把字串寫至檔案內
```C++
echo "# GitNote" >> README.md
```

-------------------
### Reference
\[1] : [Git - Reference](https://git-scm.com/)

\[2] : [為你自己學 Git](https://gitbook.tw/)

\[3] : [簡介 · Git](https://zlargon.gitbooks.io/git-tutorial/content/)

\[4] : [連猴子都能懂的Git入門指南](https://backlog.com/git-tutorial/tw/)

\[5] : [Summer。桑莫。夏天](https://cythilya.github.io/2018/04/05/git/)
