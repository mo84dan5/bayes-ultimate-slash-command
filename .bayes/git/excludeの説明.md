# .git/info/exclude について

`.git/info/exclude` は、`.gitignore` に記載せずに特定のファイルやディレクトリをGitの追跡対象から除外するためのファイルです。

## 使用方法

```bash
# .git/info/exclude ファイルを編集
echo "path/to/directory/" >> .git/info/exclude
```

## .gitignore との比較

| 項目 | `.gitignore` | `.git/info/exclude` |
|------|-------------|---------------------|
| リポジトリに含まれる | はい | いいえ |
| 他の開発者と共有 | される | されない |
| 構文 | 同じ | 同じ |

## 使用例

```bash
# 例: tmp/ ディレクトリを除外
echo "tmp/" >> .git/info/exclude

# 例: 特定のファイルパターンを除外
echo "*.local" >> .git/info/exclude
```

## 注意点

- 既に追跡されているファイルには効果がありません
- 既に追跡中のファイルを除外するには、先にキャッシュから削除が必要です：

```bash
git rm -r --cached path/to/directory/
```

## ユースケース

この方法は、以下のような場合に便利です：

- 個人の開発環境固有の設定ファイル（IDEの設定等）を除外したい場合
- チームで共有する必要のない個人的な除外設定を行いたい場合
- `.gitignore` を変更せずにローカルでのみファイルを除外したい場合
