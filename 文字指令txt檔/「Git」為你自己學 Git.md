#git #筆記

參考資源：
- [為你自己學 Git](https://gitbook.tw/)
- [連猴子都能懂的 Git 入門](https://backlog.com/git-tutorial/tw/)
- [ Git & GitHub 教學手冊（六角學院）](https://w3c.hexschool.com/git/cfdbd310)
- [30 天精通 Git 版本控管](https://github.com/doggy8088/Learn-Git-in-30-days/blob/master/zh-tw/README.md)
- [Git Tutorial for Beginners: Learn Git in 1 Hour](https://www.youtube.com/watch?v=8JJ101D3knE&ab_channel=ProgrammingwithMosh)
- [Learn Git Branching]
- (https://learngitbranching.js.org/)![[為你自己學git.pdf]]![[為你自己學Git 1.pdf]]
## 一、入門篇

### 什麼是 Git？ 為什麼要學習它？
- Git 是一種分散式版本控制系統，方便備份及控管檔案的進度![](https://i.imgur.com/Q9sF230.png)

- 適合與他人協作時的進度管理

![](https://i.imgur.com/f2H0Mrp.png)
<center>Git 改善協作時上傳版本不一致的問題</center>

#### Git 的優點
- 版本控管
- 分散式架構
- 開源
- 容量小且快速

> Git 特別的設計，在於它並不是記錄版本的差異，而是記錄檔案內容的「快照」（snapshot），它可以讓 Git 在非常快速的切換版本。至於什麼是「快照」，在後面的章節會有更仔細的介紹。）

### 如何使用 Git ?
1. 下載並安裝git
2. 安裝圖形化介面
3. 學習終端機指令

## 二、安裝 git
＊ 以下以Mac OS X 系統為例
1. 從 Git [官方網站下載 Git](https://git-scm.com/download/mac)
2. 使用 [Homebrew 安裝 Git ](https://brew.sh/index_zh-tw.html)
    - 安裝 Homebrew
        ```
        $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
        ```
    - 透過 Homebrew 安裝 Git
        ```
        $ brew install git
        ```
3. 安裝圖形化工具
   - 安裝 [Sourcetree](https://www.sourcetreeapp.com/)

## 三、學習終端機指令

### 開啟終端機
在 MacOS 開啟終端機的方式，可以點擊從右上角的「放大鏡」功能，搜尋「terminal」：
![](https://i.imgur.com/7QxROJd.png)

### 常用終端機命令列指令

| Windows | MacOS / Linux | 說明               |
| ------- | ------------- |:------------------ 
| cd      | cd            | 切換目錄           |
| cd      | pwd           | 取得目前所在的位置 |
| dir     | ls            | 列出目前的檔案列表 |
| mkdir   | mkdir         | 建立新的目錄       |
| 無      | touch         | 建立檔案           |
| copy    | cp            | 複製檔案           |
| move    | mv            | 移動檔案           |
| del     | rm            | 刪除檔案           |
| cls     | clear         | 清除畫面上的內容   |

## 四、設定 Git
### 使用者設定
終端機指令：
```
$ git config --global user.name "Eddie Kao"
$ git config --global user.email "eddie@5xruby.tw"
```

Sourcetree：
![](https://i.imgur.com/FMLbMJu.png)


## 五、開始使用 Git
### 新增、初始 Repository
終端機指令：
```
$ cd /tmp                  # 切換至 /tmp 目錄
$ mkdir git-practice       # 建立 git-practice 目錄
$ cd git-practice          # 切換至 git-practice 目錄
$ git init                 # 初始化這個目錄，讓 Git 對這個目錄開始進行版控
Initialized empty Git repository in /private/tmp/git-practice/.git/
```
Sourcetree：
- 選擇 New -> Create Local Repository：
![](https://i.imgur.com/tQ9ooy8.png)
- 填寫路徑，並選擇使用 Git：
![](https://i.imgur.com/n2fpD7s.png)
<center>/tmp 資料夾是暫存的資料夾，重新開機後資料便會被清空</center>

### 將原本即存在的檔案進行版控
終端機指令：
- 到該目錄執行 `git init`

Sourcetree：
- 直接將該目錄拉到Sourcetree的介面即可：
![](https://i.imgur.com/A1PGKLe.png)
### 把檔案交給 Git 控管
1. 先確認檔案的狀態：`$ git status`
    - 還未被Git追蹤： `Untracked files`
    - 已經被Git追蹤： `new file `
2. 把檔案交到 git 的暫存區域 (Staging Area)
    - 終端機指令：`$ git add 檔案名稱
    `
    - Sourcetree：點右鍵，選擇Add to index
    ![](https://i.imgur.com/FpeA4n2.png)
    
3. 把檔案提交到倉庫（Repository）存檔
     - **commit 只會儲存已經被放到 Staging Area 的內容**
    - 終端機指令： `$ git commit -m "commit 訊息"`
    - Sourcetree： 點選左上角的 commit 開始輸入訊息，並點選右下角的 commit 完成 commit。
      ![](https://i.imgur.com/EnlqXBw.png)
        - commit 訊息請參照：[前端開發指南 / Git 規範](https://hackmd.io/Sl7p7dMFS8-n5HoFx-XTew)
        - 在 OS X 系統中，檔案系統是無視檔名大小寫的差別的（case insensitive），所以建立檔案要注意檔名的大小寫 
### 工作區、暫存區 (Staging Area) 與儲存庫
- 在 Git 裡，主要可以分成：
    - 「工作目錄（Working Directory）」
    - 「暫存區（Staging Area）」
    - 「儲存庫（Repository）」
- 透過不同的 Git 指令，可以把檔案移往不同的區域：
![](https://i.imgur.com/KUEkGpX.png)
請記得，要執行 Commit 指令，也就是要存放到 Repository 才算是完成整個流程喔。

#### 什麼時候要 Commit ?
1. 完成一個「任務」的時候
2. 下班的時候

### 檢視 Commit 紀錄
以下功能皆可以透過圖形介面(Sourcetree)直接查詢
#### 檢視 Git 紀錄：
終端機指令：
- `$ git log`，會顯示以下資訊：
    - Commit 作者
    - 什麼時候 Commit 
    - 每個 Commit 做了些什麼事

Sourcetree：
- 點選 "History" 可以看到所有歷史紀錄
    ![](https://i.imgur.com/ofnh7Y4.png)
#### 查詢指令：
- 查作者：`$ git log --online --author="作者名稱"`
- 查 commit 訊息(標題）： `$ git log --online --grep="訊息文字"`
- 查 commit 內容：`$ git log -S "內容文字"`
- 查 commit 歷史： `$ git log --oneline --since="9am" --until="12am"`
    - 增加 after 時間： `$ git log --oneline --since="9am" --until="12am" --after="2017-01"
`
- 查程式碼作者： `$ git blame 檔案名稱`

### 刪除及變更檔名
在 Git 裡，不管是刪除檔案或是變更檔名，對 Git 來說都是一種「修改」。

#### 刪除
- 終端機指令：`$ git rm 檔案名稱`
- Sourcetree：在檔案上按右鍵，選擇「Remove」
    ![](https://i.imgur.com/3NAvZtl.png)
#### 變更檔名：
- 終端機指令： `$ git mv 舊名稱 新名稱`
- Sourcetree：在檔案上按右鍵，選擇「Move」功能：
    ![](https://i.imgur.com/0Wo9ESB.png)
### 修改 Commit 紀錄
修改Commit有多種方法：
- 使用 `git rebase` 來修改歷史。
- 先把 **Commit** 用` git reset` 拆掉，整理後再重新 **Commit**。
- 使用 `--amend` 參數來修改最後一次的 **Commit**。
詳細請參考[七、修改歷史訊息](#七、修改歷史訊息)

### 只 Commit 部分的內容
用滑鼠選取想要加入的內容，按滑鼠右鍵選擇「Stage Selected Lines」
![](https://i.imgur.com/upSdtCS.png)

## 六、分支
![](https://i.imgur.com/0qp8yNl.png)

### 分支是什麼？為什麼要使用？
- 分支是為了將修改記錄的整體流程分開儲存，讓分開的分支不受其他分支的影響，所以在同一個數據庫裡可以同時進行多個不同的修改。
- 分開的分支可以和其他分支合併。

> 所以分支是什麼？有人可能認為，所謂的「開分支」是把檔案先複製到另外的目錄，然後進行修改之後再合併，把檔案跟原本的檔案比對之後放回原本的目錄...。其實Git不是這樣
> 
#### 分支像貼紙一樣
- 你可以把分支想像成一張貼紙，它是貼在某一個 Commit 上面
- 當做了一次新的 Commit 後，這個新的 Commit 會指向它的前一個commit
- 「目前的分支」，也就是HEAD所指的這個分支，會跟著貼到剛剛做的那個 Commit上，同時 HEAD也跟著前進

### 使用分支
![](https://i.imgur.com/i35WH0K.png)
- 建立分支前的歷史紀錄

#### 1. 建立分支
![](https://i.imgur.com/oN27sa5.png)
- 建立分支後可以看到歷史紀錄增加了分支，但 HEAD 仍然指向 master
- 建立分支指令：
`
$ git branch <branchname>
`
- or 建立並且 checkout 到該分支：
`
& git checkout -b <branchname>
`

#### 2. 切換分支
![](https://i.imgur.com/d3ztQOj.png)
- 將 HEAD checkout 到新的分支
- 指令：`
$ git checkout <branchname>
`
#### 3. 合併分支
如果想將新分支合併到 master，先切換回 master，再 merge
 1. 先切換回 merge：
`$ git checkout master`
 2. 合併分支至當前使用的分支：
`$ git merge <branchname>`

![](https://i.imgur.com/cGEKeFu.png)

#### 4. 刪除分支
只能刪除不是checkout中的分支
`$ git branch -d <branch>`

#### 5. 解決合併的衝突
合併分支後可能會出現衝突
```
add 修改加入索引
<<<<<<< HEAD
commit 記錄索引的狀態
=======
pull 取得遠端數據庫的內容
>>>>>>> issue3
```

回到 VS CODE 修改，完成後重新加入暫存庫並且再推一次

#### 6. 使用 rebase 合併
如果想將新分支 rebase 合併到 master，HEAD須指向新分支，在新分支上使用 rebase。
- 指令： `$ git rebase master`

### 還原被刪除的分支
刪掉分支，那些 Commit 還是在，只需知道該 Commit 的 SHA-1 值便可叫回來。

終端機指令：
- 重新為要還原的 Commit 建立分支：
`$ git branch <branchname> b174a5a`
b174a5a 的部分填上該 Commit 的 SHA-1 值

Sourcetree:
- 點擊上面選單的「Branch」按鈕後會看到這個對話框，Specified commit 中填入原本 Commit 的 SHA-1值，再按「Create Branch」
![](https://i.imgur.com/cRS7yCB.png)

### 使用 rebase 合併
![](https://i.imgur.com/O33AOH2.png)
所謂「base」就是指「你這分支是從哪裡生出來的」，以上面這個例子來說，cat 跟 dog 這兩個分支的 base 都是 master。

#### git rebase
使用`git rebase`來組合兩個分支

```
$ git rebase dog
```
- 將 cat rebase 到 dog 上
- 白話文翻譯：「我，就是 cat 分支，我現在要重新定義我的參考基準，並且將使用 dog 分支當做我新的參考基準
- Sourcetree：
    - 可在左邊選單找到想要 Rebase 的對象，按滑鼠右鍵並選擇「Rebase current branch onto dog」：
    ![](https://i.imgur.com/ZXz3UzH.png)
    - 它會跳出一個對話框：
    ![](https://i.imgur.com/qiwEjrT.png)
    - 因為 Rebase 指令等於是修改歷史，不應該隨便對已經推出去給別人內容進行 rebase，因為這很容易造成其它人的困擾。
    - 按下 OK 鈕便會完成。完成之後，cat 分支將會接到 dog 分支上，像這樣：
![](https://i.imgur.com/ksJzovq.png)
#### 誰 Rebase 誰有差嗎？
就以最後的檔案來說是沒什麼差別，但以歷史紀錄來說有差別，誰 Rebase 誰，會造成歷史紀錄上先後順序不同的差別。

#### 怎麼取消 rebase？
1. 使用 Reflog
使用指令看紀錄，找到rebase前一次的紀錄，使用 reset 切回去
`git reset b174a5a --hard`
2.  ORIG_HEAD
ORIG_HEAD 會記錄「危險操作」之前 HEAD 的位置，使用reset 切回 ORIG_HEAD 的位置
`$ git reset ORIG_HEAD --hard`
#### 使用 Rebase 時機？
優點：
- 它不像一般合併可能會產生額外的合併專用的 Commit
- 而且歷史順序可以依照誰 Rebase 誰而決定

缺點：
- 它相對的比一般的合併來得沒那麼直覺，一個不小心可能會弄壞掉而且還不知道怎麼 Reset 回來
- 或是發生衝突的時候就會停在一半，對不熟悉 Rebase 的人來說是個困擾。
衝突修改請參考[解決合併的衝突](#5.解決合併的衝突)
### 遠端數據庫
#### Pull
- 執行 pull 命令可以取得遠端數據庫的歷史記錄
- 執行 pull 時，如果內容沒有衝突，就會自動建立合併提交。如果發生衝突的話，需先解決衝突然後再手動提交。
#### Fetch
- 有時候只是想確認遠端數據庫的內容卻不是真的想合併，在這種情況下，請使用 fetch。
#### Push
- push 命令會將 commit 的資料提交到遠端數據庫。
- 在push 提交到遠端數據庫前，您可以在您的本地端分支任意地提交或是建立分支，不會因自己的時間或步驟而影響其他成員。
- Git會把 push 的分支與遠端數據庫以 fast-forward 合併，如果發生衝突， push 會被拒絕
    - 需要先pull最新的遠端變更，並再進行一次push。
## 七、修改歷史訊息
### 1. Commit --amend 
此方法只能修改最後一次 Commit 的內容
- 終端機指令：
`$ git commit --amend -m "Welcome To Facebook"`

- Sourcetree: 
    - 先點選左上角的 Commit 按鈕進行 Commit 畫面，然後在右上角的「Commit Options」選擇「Amend last commit」：
    ![](https://i.imgur.com/ASlZZ1S.png)
    按下右下的 Commit 按鈕後就可修改。
### 2. Revert
Revert : 再做一個新的 Commit ，來取消不要的 Commit
- 終端機指令：`$ git revert HEAD --no-edit
`
- Sourcetree：在想要取消的 Commit 上按滑鼠右鍵，然後選擇「Revert Commit…」![](https://i.imgur.com/DD1oPx7.png)

Revert 後最新的Commit內容會變成想要修改的Commit，但也會因此而新增更多 Commit 
   - ![](https://i.imgur.com/rbWZbTm.png)

### 3. Reset
- 終端機指令：
    - 相對做法：
    `$ git reset e12d8ef^`
    倒退到 e12d8ef 的前一個 Commit 
    `$ git reset e12d8ef~5`
    倒退到 e12d8ef 前的第五個 Commit 
    - 絕對做法：

- Sourcetree：在想要 reset 到的 Commit 上按滑鼠右鍵，選擇「Reset master to this commit」：![](https://i.imgur.com/VTTM5tE.png)

### 4. Cherry-pick
撿別的分支中的 Commit 來用
- 終端機指令：
    ```
    $ git checkout master
    Switched to branch 'master'
    $ git cherry-pick 99daed2
    ```
- Sourcetree：
![](https://i.imgur.com/FRTlW2O.png)

### 5. 使用 rebase -i 合併提交
![](https://i.imgur.com/SP39nA9.png)

- 若要合併過去的提交，請使用rebase -i命令。
`$ git rebase -i HEAD~~`
- 預設的文字編輯器會自動開啟，您將看到HEAD 到 HEAD~~ 的提交如下圖顯示。
```
pick 9a54fd4 添加commit的說明
pick 0d4a808 添加pull的說明

# Rebase 326fc9f..0d4a808 onto d286baa
#
# Commands:
#  p, pick = use commit
#  r, reword = use commit, but edit the commit message
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#  f, fixup = like "squash", but discard this commit's log message
#  x, exec = run command (the rest of the line) using shell
#
# If you remove a line here THAT COMMIT WILL BE LOST.
# However, if you remove everything, the rebase will be aborted.
#
```
將第二行的 "pick" 改為 "squash"，儲存後並退出。由於合併後要提交，所以編輯器會提醒您編輯這個最新的提交訊息，請編輯訊息後儲存並退出。

這樣，兩個提交就合併成一個提交了。請用 log 命令確認歷史記錄。
![](https://i.imgur.com/fvHIJNw.png)


### 6. 使用 rebase -i 修改提交
- SourceTree
    - 在指定的 Commit 上按滑鼠右鍵，選擇「Rebase children of SHA-1 interactively…」：
    ![](https://i.imgur.com/76sn0aY.png)
    - 接著找到你想要修改訊息的 Commit 上，按滑鼠右鍵選擇「Edit message…」：
![](https://i.imgur.com/GnlfWF6.png)
    - 編輯內容…
![](https://i.imgur.com/seg4PSJ.png)

    可以再繼續選擇其它 Commit 繼續進行修改訊息，待全部都完成之後，按下右下角的 OK 鈕，即可開始進行 Rebase。



### 7. Merge --squash 把多個 Commit 合併成一個 Commit
- SourceTree:
    - 在歷史紀錄上的 Commit 上按滑鼠右鍵，選擇「Rebase children of SHA-1 interactively…，進入互動模式。
    - 這時，我先在 add dog 2 這個 Commit 上按滑鼠右鍵並選擇「Squash with previous commit…」：
![](https://i.imgur.com/YahGHV6.png)
    - 接著是在 add cat 2 上做一樣的事：
    ![](https://i.imgur.com/AtAysEV.png)
    - 再來是 add 2 cats：
    ![](https://i.imgur.com/75fXg3q.png)
    > **注意！**
    >
    >因為這邊是要合併三個 Commit，如果上面這兩個步驟反過來，你會發現沒辦法順利的「Squash」，這時只要按下 Cmd + Z 就可以回到上一步再重來一次。
    - 接著，編輯剛剛「濃縮」的這兩個 Commit 的訊息，這是編輯完成的 Commit 訊息之後的樣子：
![](https://i.imgur.com/C8VSaTM.png)
    - 全部完成之後，按下右下角的 OK 鈕就會開始進行 Rebase，這樣就可以把多個 Commit 合併成一個了。

### 8. Reset、Revert 跟 Rebase 指令有什麼差別？


| 指令   | 改變歷史紀錄 |  說明  |
| ------ | ------------ |:--------|
| Reset  | 是           |                                                                          把目前的狀態設定成某個指定的 Commit 的狀態，通常適用於尚未推出去的 Commit。  |
| Rebase | 是           |                                                 不管是新增、修改、刪除 Commit 都相當方便，用來整理、編輯還沒有推出去的 Commit 相當方便，但通常也只適用於尚未推出去的 Commit。                                                  |
| Revert | 否           | 新增一個 Commit 來反轉（或說取消）另一個 Commit 的內容，原本的 Commit 依舊還是會保留在歷史紀錄中。雖然會因此而增加 Commit 數，但通常比較適用於已經推出去的 Commit，或是不允許使用 Reset 或 Rebase 之修改歷史紀錄的指令的場合。|
## 八、標籤
### 使用標籤？
#### 標籤是什麼？
在 Git，「標籤（tag）」是一個指向某一個 Commit 的指標。
#### 什麼時候使用標籤？
通常在開發軟體有完成特定的里程碑，例如軟體版號` 1.0.0 `或是 `beta-release` 之類的，這時候就很適合使用標籤做標記。
#### 標籤有兩種
1. 輕量標籤（lightweight tag）
2. 有附註標籤（annotated tag）
#### 兩種標籤的差別
這兩種標籤的第一個差別，就是訊息量的不同
- 一般的輕量標籤：只有標籤指向的那個 Commit 的訊息
- 有附註的標籤：有附註的標籤比一般的輕量標籤多了一些資訊，看得出來是誰在什麼時候打了這張標籤。
#### 刪除標籤
不管是哪一種標籤，標籤基本上就是一張貼紙的概念，撕掉一張貼紙並不會造成 Commit 或檔案不見。要刪除只要給它`-d`參數就行了：
- 終端機指令：
`$ git tag -d 標籤名稱`
- SourceTree：
找到那個分支，按滑鼠右鍵選擇最下面「Delete..」
![](https://i.imgur.com/fIA5kov.png)
### 標籤跟分支有什麼不一樣？
標籤跟分支都是一種指標，也都是放在`.git/refs `目錄下，只是分支是在 `heads` 目錄，標籤則是在`tags` 目錄。
在被刪除的時候，也不會影響到被指到的那個物件。

標籤跟分支真正的差別：
- 是「分支會隨著 Commit 而移動，但標籤不會」。
- 當 Git 往前推進一個 Commit 的時候，它所在的分支會跟著往前移動。
- 標籤一旦貼上去之後，不管 Commit 怎麼前進，標籤還是留在原來貼的那個位置上。


## 九、其他常見狀況題
### Stash 暫存進度
#### 將資料暫存至 Stash
- 終端機指令：
`$ git stash`

    > Untracked 狀態的檔案預設沒辦法被 Stash，需要額外使用`-u`參數。

- Sourcetree
    在上方選單有一顆「Stash」按鈕，按下之後便會出現對話框
    ![](https://i.imgur.com/loDNp0i.png)
    填寫後按下 OK 即可完成。在左邊側邊欄可以看到一個「STASHES」選單，裡面會放著目前所有的 Stash 的內容：
![](https://i.imgur.com/HSJy6kr.png)
#### 從 Stash 中取用暫存的資料
- 終端機指令：
    - 查看目前 Stash 的列表
        - `$ git stash list` 
    - 取用 Stash
        -  pop： 
            -  `$ git stash pop <stash名稱>`
            - 使用 pop 指令，可以把某個 Stash 拿出來並套用在目前的分支上。套用成功之後，那個套用過的 Stash 就會被刪除。
            - 如果後面沒有指定要 pop 哪一個 Stash，會從編號最小的，也就是 stash@{0} 開始拿（也就是最後疊上去的那次）。
        - apply： 
            - `$ git stash apply <stash名稱>`
            - 會把 Stash 拿來套用在現在的分支上，但 Stash 不會刪除，還是會留在 Stash 列表上。

    - 刪除 Stash (drop)：`$ git stash drop <stash名稱>`
- Sourcetree：
    - 在指定的 Stash 上按滑鼠右鍵，然後選擇「Apply Stash
    ![](https://i.imgur.com/lLjC6bg.png)
    
### 刪除或修改大量 Commit
此方法只適用於還沒推出去的狀況
- **使用 filter-branch 指令**
    - 假設我想要把 config/database.yml 這個檔案從每個 Commit 裡把它拿掉
    - `$ git filter-branch --tree-filter "rm -f config/database.yml"`
        1. `filter-branch` 這個指令可以讓你根據不同的 filter，一個一個 Commit 的來處理它。
        2. 這裡使用了` --tree-filter` 這個 filter，它可以讓你在 Checkout 到每個 Commit 的時候執行你指定的指令，執行完後再自動幫你重新再 Commit。
            - 以上面這個例子來說，便是執行「強制刪除 config/database.yml 檔案」這個指令。
        3. 因為刪除了某個檔案，所以在那之後的 Commit 全部都會重新計算
            - 於是會產生一份新的歷史紀錄
- **回復 filter-branch 造成的結果**
    - `$ git reset refs/original/refs/heads/master --hard`

### 只想要某分支的某幾個 Commit 
#### cherry-pick
- 終端機指令
    - `$ git cherry-pick <commit的號碼>`
    - 撿過來但先不合併：加上 --no-commit
        - `$ git cherry-pick 6a498ec --no-commit`

- sourceTree：
    - ![](https://i.imgur.com/mLlWKZu.png)
        - 對想要撿的 commit 按滑鼠右鍵，選擇「Cherry Pick」功能

### 真正的將檔案真正的從 Git 中移除
#### 使用 Rebase 或 filter-branch 指令來整理
- 如果 Commit 的數量小，使用 Rebase 應該就足以進行編輯、重整。
`git filter-branch -f`
    

### detached HEAD（斷頭）是什麼？
 - 正常情况下，HEAD 會指向某一個分支，而分支會指向某一個 Commit。但 HEAD 偶爾會發生「沒有指到某個分支」的情況，這個狀態的 HEAD 便稱之「detached HEAD」。
    ![](https://i.imgur.com/OyTToOJ.png)
    
- 怎麼離開 detached HEAD 狀態？
    - 要脫離這個狀態，只要讓 HEAD 有任何分支可以指就行了，例如讓它回到 master 分支：
    `$ git checkout master
    Switched to branch 'master'`

## 十、遠端共同協作 - 使用 GitHub
### GitHub 是什麼？
https://github.com/
- 它是一個商業網站，是目前全球最大的 Git Server。
- 在這邊，你可以跟其它厲害的開發者們交朋友，你可以幫忙貢獻其它人的專案，其它人也可以回饋到你的專案，建立良性循環。
- 是開發者最好的履歷，曾經做過的專案及貢獻，一覽無遺。
### 上傳檔案至 GitHub
要上傳檔案到 GitHub，需要先在上面開一個新的專案。
- 在 GitHub 網站的右上角點選「+」號，並選擇「New repository」：
![](https://i.imgur.com/Mvhmd5X.png)
- 接著填寫專案名稱：
![](https://i.imgur.com/ofJthSb.png)
- 按下「Create repository」即可新增一新的 Repository。
    - 會看到的這個引導畫面：
    ![](https://i.imgur.com/1ZHDx77.png)
```
$ git init

$ git add README.md

$ git commit -m "first commit"

$ git remote add origin git@github.com:<你的名字>/<專案名稱>.git
```
`$ git push -u origin master`
#### Git 教學：使用 SourceTree
- 如果是使用 SourceTree，請按下右上角的「Settings」按鈕，跳出對話框後，選擇「Remote」頁籤：
![](https://i.imgur.com/MuEel3z.png)
- 點選「Add」按鈕：
![](https://i.imgur.com/EjZoV2r.png)
- 填寫「Remote name」以及「URL」欄位後，按下 OK 按鈕後，遠端節點即設定完成。接下來要把東西往上推，請點選上面工具列的「Push」按鈕：
![](https://i.imgur.com/mJumgcE.png)
- 勾選你想推的分支，按下 OK 鈕之後就會開始把指定的分支往指定的遠端節點推。成功之後再回來看，現在在 master 分支旁邊就多了一個 origin/master 的分支了：
![](https://i.imgur.com/jXiDPx8.png)

### 從 GitHub 下載檔案
下載前先使用 fetch 同步線上與本機進度
`$ git fetch`

#### Pull 指令
> git pull = git fetch + git merge
#### Pull + Rebase
`$ git pull --rebase`
### 進度衝突：無法 push
通常這個狀況會發生在多人一起開發的時候：
![](https://i.imgur.com/xqtOtB9.png)
#### 解決辦法一：先拉再推
#### 解決辦法二：git push --force
### 從伺服器取得 Repository
只要使用 Clone 指令就可以把整個專案複製一份回來了。在 GitHub 專案的頁面有一個「Clone or download」的按鈕：
![](https://i.imgur.com/vdPDSQl.png)

`$ git clone git@github.com:kaochenlong/dummy-git.git hello_kitty`

### Clone 和 Pull 指令的差異
 - Clone 是完整複製
     - 使用時機：第一次下載檔案
 - Pull 是更新本地檔案
     - 使用時機：已經下載檔案，想要更新進度
### 與其他開發者互動：Pull Request
- 第一步：複製（Fork）專案
    - ![](https://i.imgur.com/ESJwB7M.png)
- 第二步：Clone 回來修改
- 第三步：Push 回你自己的專案
- 第四步：發 PR 給原作者
    - 回到自己的專案頁面，可以找到一個「New pull request」的按鈕：
![](https://i.imgur.com/DARqF16.png)
    - 按下「Create pull request」後，可開始填寫 PR 的相關資訊，讓作者知道你這個 PR 大概做了什麼事：
![](https://i.imgur.com/v1lm8Q7.png)
    - 按下「Create pull request」後，可開始填寫 PR 的相關資訊，讓作者知道你這個 PR 大概做了什麼事：
![](https://i.imgur.com/ZxQp0di.png)
    - 填寫完畢後，按下「Create pull request」按鈕後，即算完成送出 PR：
![](https://i.imgur.com/ADio6Cg.png)
- 第五步：原作收下 PR
    - 切換回角色 A，也就是原作者，便可以在專案的頁面看到 Pull requests 的數量增加了：
![](https://i.imgur.com/ha3pUBy.png)
    - 如果覺得可以收，就只要按下 Merge pull request 按鈕後，就會合併這次的 Commit：
![](https://i.imgur.com/otXbwuP.png)

### 刪除遠端分支
- 點擊畫面中間的分支列表可以看到目前所有的分支，在分支旁邊有一顆紅色垃圾筒的圖示：
![](https://i.imgur.com/ZGZS65q.png)
- 若要使用 SourceTree 來刪除遠端分支，請在左邊的選單找到「REMOTES」，在你想要刪除的分支上按滑鼠右鍵：
![](https://i.imgur.com/TqoJ8nl.png)

### git push -f 的使用時機
#### 使用時機
1. 整理歷史紀錄
2. 只用在自己所在的分支上
#### 啟動保護機制
GitHub 網站有提供保護機制，可以避免某個分支被 Force Push。請到專案的「Settings」頁籤，左邊選擇「Branches」，接著可以選擇想要保護的分支：
![](https://i.imgur.com/8qyvphE.png)
- 勾選你想要保護的選項：
![](https://i.imgur.com/GVXLpf5.png)



### 使用 GitHub 製作免費個人網站

## 十一、Git Flow
### Git Flow 是什麼？為什麼需要 Git Flow？![](https://i.imgur.com/EpSJhen.png)
- gitflow 的目的是對 git 使用的流程進行規範
    - 不同分支之間的資料能夠保持井然有序、互不干擾
- 詳細規範請參考[前端 Git 規範](https://hackmd.io/Sl7p7dMFS8-n5HoFx-XTew)
#### Master 分支
- 主要是用來放穩定、隨時可上線的版本。
- 這個分支的來源只能從別的分支合併過來，開發者不會直接 Commit 到這個分支。

#### Develop 分支
- 這個分支主要是所有開發的基礎分支，當要新增功能的時候，所有的 Feature 分支都是從這個分支切出去的。
- Feature 分支的功能完成後，也都會合併回來這個分支。
#### Hotfix 分支
- 當線上產品發生緊急問題的時候，會從 Master 分支開一個 Hotfix 分支出來進行修復
- Hotfix 分支修復完成之後，會合併回 Master 分支，也同時會合併一份到 Develop 分支。

#### Release 分支
- 當認為 Develop 分支夠成熟了，就可以把 Develop 分支合併到 Release 分支。
- 測試完成後，Release 分支將會同時合併到 Master 以及 Develop 這兩個分支上。

#### Feature 分支
- 當要開始新增功能的時候，就是使用 Feature 分支的時候了。
- Feature 分支都是從 Develop 分支來的，完成之後會再併回 Develop 分支。
### 使用 Git Flow
#### 設定 Git Flow 按鈕
- 如果你在 SourceTree 上方看不到 Git Flow 的按鈕，請在工具箱按滑鼠右鍵：
![](https://i.imgur.com/hQMzC42.png)
- 選擇「Customize Toolbar…」
![](https://i.imgur.com/8s5GCQL.png)
- 把「Git Flow」的按鈕拖拉到工具箱，像這樣：
![](https://i.imgur.com/aB3UyVX.png)
#### Flow 初始化
- Git請按下上方工具箱的「Git Flow」按鈕，如果是第一次按的話，會進入初始化設定：
![](https://i.imgur.com/sAcO3lu.png)
#### 開始加功能
- 要開始加功能，請一樣按下上方工具箱那顆「Git Flow」按鈕後會跳出這個畫面：
![](https://i.imgur.com/5g3tyjw.png)
有一些選項可以選，因為要加功能，所以這裡選擇「Start a New Feature」，接著就是填寫這個 Feature 分支的名字：
![](https://i.imgur.com/oCsf3T9.png)
#### 完成功能
- 按下那個「Git Flow」按鈕：
![](https://i.imgur.com/EBqoh21.png)
- 選擇「Finish Current」，表示要完成這一個 Feature 分支的進度。按下後會再出現這個對話框：
![](https://i.imgur.com/tNWkqir.png)


## 十二、常用指令整理
### 查詢資料狀態
```
$ git status
```

### 建立分支：
```
$ git branch <branchname>
```
or 
```
& git checkout -b <branchname>
```
### 刪除本地分支：
```
$ git branch -D <branchname>
```

### 刪除遠端分支：
```
$ git push origin :<branchname>
```

### 推分支
```
$ git push origin <branchname>
```

### 更新本地分支（拉）
```
$ git pull
```

### 更新遠端分支狀態
```
$ git fetch
```