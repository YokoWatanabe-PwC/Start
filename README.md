### ローカルリポジトリのセットアップ
* フォルダ作成
```
# mkdir 任意のフォルダ
（例） mkdir ~/Documents/JRC/git/devXX/src
```
* Git設定
```
# cd ~/Documents/JRC/git/devXX/src
# git init
# git config --global user.name "各自のユーザ名"
# git config --global user.email "各自のメールアドレス"
# git config --global core.quotepath false
# git config --global http.sslVerify false
```
* Githubからmasterブランチのチェックアウト
```
# git remote add origin https://github.com/pwcjrccmssys/cms.git
# git fetch
# git checkout master
```
* IDE・エディタの設定
```
Eclipseの場合は上記フォルダを指定し、GeneralプロジェクトやForce.comプロジェクトなど個人のスタイルで作成
```
* SourceTreeの設定
```
ファイル > 開く
で上記フォルダを開く
```
### 開発フロー
* ブランチの確認
```
# cd ~/Documents/JRC/git/devXX/src
# git branch
\* master
```
* masterブランチの最新化
```
# git pull origin master
```
* 開発機能のブランチをmasterを基に作成
```
# git checkout -b bugfix_S000001_pointrule
　※ 主目的_管理番号_わかりやすい作業名
# git branch
\* bugfix_S000001_pointrule
   master
```
* 開発機能のコミットとGithubへのpush（SourceTreeの方が楽）
```
# git add xxx
# git commit
# git push origin bugfix_S000001_pointrule
```
* GithubのWebサイトでPull Request操作
```
1. 「Code」タブを開く
2. 「New pull request」ボタンをクリック
3. 「base」プルダウンはmaster。「compare」プルダウンにpushしたブランチを選択
4. 修正内容を確認し、「Create pull request」ボタンをクリック
```
* GithubのWebサイトでPull Requestをmasterにマージ
```
1. 「Pull requests」タブを開く
2. 対象のPull Requestをクリック
3. 「Files changed」タブをクリックし、修正内容を確認する
4. 「Merge pull request」ボタンをクリックしマージする
5. 「Delete branch」ボタンをクリックしてブランチを削除する
```
* マージされたので、ローカルのmasterブランチを最新化
```
# git branch
\* bugfix_S000001_pointrule
   master
# git checkout master
# git branch
   bugfix_S000001_pointrule
\* master
# git pull origin master
```
### Sandboxへの反映（force CLIの使い方）
* Sandboxへログイン
```
# force login -i=test.salesforce.com -u=xxx@jrc.1.devXX -p=xxxxxxxx
```
* Metadataの反映
```
# force push -f classes/xxx.cls \
             -f pages/xxx.page
```
