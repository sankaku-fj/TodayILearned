# GitHub連携

## 既存のSSHキーの削除

<https://docs.github.com/ja/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys>

```powershell
SSHファイルのあるディレクトリに移動
cd ~/.ssh

ディレクトリ内のファイルを列挙
ls

必要に応じてファイルを削除
rm SSHキー名（GitHubに対応する.pubファイル）
```

GitHubで使われるSSHファイル

* id_rsa.pub
* id_ecdsa.pub
* id_ed25519.pub
  
## SSHキーの作成

<https://docs.github.com/ja/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent>

キーの作成

```powershell
ssh-keygen -t ed25519 -C "GitHubで使用しているメールアドレス"
```

次のメッセージが表示される。

```powershell
ファイルの保存場所（未入力でデフォルトに保存）
Enter a file in which to save the key (c:\Users\YOU\.ssh\id_ALGORITHM):[Press enter]

パスワードの設定
Enter passphrase (empty for no passphrase): [Type a passphrase]

パスワード再度入力
Enter same passphrase again: [Type passphrase again]
```

## GitHubとの連携

<https://docs.github.com/ja/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account>

SSH公開鍵をクリップボードにコピーする。

```powershell
clip < ~/.ssh/id_ed25519.pub
```

次のエラーが表示されるときは、下のコマンドを試す： `The '&lt;' operator is reserved for future use.`  

```powershell
cat ~/.ssh/id_ed25519.pub | clip
```

GitHub上で、`アカウント > Setting > アクセス > SSHキーとGPGキー`

`New SSH Key` もしくは `Add SSH Key` を選択し、Keyフィールドにコピーしたキーを貼り付ける。

## GitHubとの連携の確認

<https://docs.github.com/ja/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection>

次のコマンドで、GitHubのアカウント名が表示されればOK。

```powershell
ssh -T git@github.com
```

次のエラーが出る場合は、`yes`と入力する。

```
> The authenticity of host 'github.com (IP ADDRESS)' can't be established.
> ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
> Are you sure you want to continue connecting (yes/no)?
```

## contributions に反映されないとき

Gitの`user.name`, `user.email`を確認して、Githubで使っているものに変更する。

[Gitのユーザー名・アドレスの変更](../Git/ユーザー名・アドレス変更.md)