# Git_myLearningNote
((((Git也有GUI的圖形化介面，但以下針對在終端機下指令的方式進行介紹))))
## 甚麼是Git?
針對檔案進行版本控制的軟體

## 甚麼是GitHub?
一個平台，可以邀請多人一起進行專案的版本控制

## CASE A. 自己一個人用 Git and GitHub
### 1.如果要上傳檔案，一定要先設定自己與GITHUB連結的帳號密碼
```
$ git config –global user.email “you@example.com”
$ git config –global user.name “your name”
```
### 2.每個要上傳檔案的該檔案夾要初始化為git檔案夾才可以操作git指令
```
$ git init
```
### 3.每個git folder基本有以下幾個設定檔：
#### 3-1. 遠端連結清單：
- 查看
```
$ git remote –v
```
- 新增: git會生成兩個功能的連結(fetch&push)
```
$ git remote add name “SSH_URL | HTTP_URL”
如果用SSH要事先在github登記自己的公鑰；如果用HTTP每次都要輸入github帳密
SSH 匯入方法參考: https://help.github.com/articles/checking-for-existing-ssh-keys/
```
- 刪除
```
$ git remote remove name
```
#### 3-2. 受 git 指令控制的檔案清單
- 查看
```
$ git ls-files
```
- 新增
```
$ git add file_name 
# 按tab可以秀出清單
```
-- 修改檔名：如果檔案更名了，你的git控制的檔案清單裡面也要一起改名才行!!
```
$ git mv old_name new_name
```
- 刪除
```
$ git rm file_name 
# 按tab可以秀出清單
```
### 4.每次檔案修改了之後，就可以用commit進行版本更新
```
$ git commit –m message –a –v
# -m 版本更新註解 -a 全部修改過的都更新 –v 看那些檔案有被修改過
```
### 5.commit完的檔案才可以上傳到GITHUB上面
```
超仔細介紹git push過程網頁：
https://gitbook.tw/chapters/github/push-to-github.html
$ git push –u origin master 
```

## CASE B. 多人共同維護 Repositorie on GitHub
### 1. GutHub 開啟專案的時候就必須邀請會參與專案的成員
Setting >> Collaborators >> Add collaborator（受邀請的人員必須到註冊的email進行確認的動作）
### 2. 本地端動作：先把平台上面的檔案拉下來
#### 2-1. 針對要執行版本控管的地方進行初始設定
```
git init >> git remote add & git config
```
#### 2-2. 先把要共同編輯的repository拉至本地端
```
$ git clone “HTTP_URL”
```
#### 2-3. 再執行平常git指令：
```
git add >> git commit >> git push
```
#### 2-4. 後面持續更新資料夾到本地端指令
```
注意git clone是第一次拉資料夾下來的指令，git pull是將資料更新到最近的狀況的指令
$ git pull “HTTP_URL”
```
