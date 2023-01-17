テンプレートからリポジトリを生成後
==================================
- ライセンスの設定
- デプロイキーの設定
    1. `ssh-keygen -t ed25519` で、秘密鍵ファイルと公開鍵ファイルを生成
	1. 生成したリポジトリへ秘密鍵を登録
		1. 生成したリポジトリで Settings → Security → Secrets and variables → Actions → Secrets → New repository secrets
		1. Name へ `DESTINATION_REPOSITORY_DEPLOY_KEY` と入力
		1. Secrets へ秘密鍵ファイルの中身を貼り付け
		1. Add secret
	1. デプロイ先のリポジトリへ公開鍵を登録
		1. デプロイ先のリポジトリで Settings → Security → Deploy keys → Add deploy key
		1. Title は任意
		1. Key へ公開鍵ファイルの中身を貼り付け
	    1. Allow write access へチェックを入れる
		1. Add key
	1. 鍵ファイルを抹消
- デプロイ先の設定
    1. 生成したリポジトリで Settings → Security → Secrets and variables → Actions → Variables → New repository variable
	1. Name へ `DESTINATION_REPOSITORY` と入力
	1. Value へデプロイ先の「ユーザー名/リポジトリ名」を入力
		+ 例: `esperecyan/esperecyan.github.io`
- [web-dev-server.config.js](web-dev-server.config.js) の `port` の値を、49152〜65535のランダムな値に変更
- README.md のこの項を削除

--------------------------------------------------

開発環境の構築
==============
1. [Node.js]のインストール
2. [Visual Studio Code]のインストール
3. Visual Studio Codeでフォルダを開いたときに推奨されるプラグインをインストール
4. ターミナルで `npm ci` を実行

[Node.js]: https://nodejs.org/ja/
[Visual Studio Code]: https://azure.microsoft.com/products/visual-studio-code/

ローカルサーバーの起動
======================
1. ターミナルで `npm start` を実行
