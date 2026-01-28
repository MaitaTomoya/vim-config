# My Vim Configuration

個人用のVim設定ファイルとドキュメント。

## 📁 ディレクトリ構成

```
~/.vim/
├── vimrc                    # Vim設定ファイル
├── colors/                  # カラースキーム
│   ├── onedark.vim
│   └── molokai.vim
├── docs/                    # ドキュメント
│   └── vim-cheatsheet.md   # 操作方法チートシート
└── pack/                    # プラグイン（Git管理対象外）
    └── plugins/
        └── start/
```

## 🚀 セットアップ手順

### 前提条件

Vimがインストールされていることを確認：

```bash
vim --version
```

インストールされていない場合：

```bash
# macOS
brew install vim

# Ubuntu/Debian
sudo apt install vim

# CentOS/RHEL
sudo yum install vim
```

### 1. リポジトリをクローン

```bash
# 既存の.vimディレクトリがある場合はバックアップ（重要！）
[ -d ~/.vim ] && mv ~/.vim ~/.vim.backup

# リポジトリをクローン（~/.vimとして配置）
git clone https://github.com/YOUR_USERNAME/vim-config.git ~/.vim
```

**注意**: クローン先を`~/.vim`に指定することで、設定ファイルが正しい場所に配置されます。

### 2. プラグインをインストール

```bash
# プラグイン用ディレクトリを作成
mkdir -p ~/.vim/pack/plugins/start

# プラグインをインストール
cd ~/.vim/pack/plugins/start

# 基本プラグイン
git clone --depth 1 https://github.com/vim-airline/vim-airline.git
git clone --depth 1 https://github.com/vim-airline/vim-airline-themes.git

# ファイル操作
git clone --depth 1 https://github.com/preservim/nerdtree.git

# 検索・ファジーファインダー
git clone --depth 1 https://github.com/junegunn/fzf.git
git clone --depth 1 https://github.com/junegunn/fzf.vim.git
git clone --depth 1 https://github.com/jremmen/vim-ripgrep.git

# カーソル移動
git clone --depth 1 https://github.com/easymotion/vim-easymotion.git

# アイコン表示
git clone --depth 1 https://github.com/ryanoasis/vim-devicons.git
```

### 3. 動作確認

```bash
# Vimを起動
vim

# または、ファイルを開いて確認
vim ~/.vim/docs/vim-cheatsheet.md
```

**確認項目**:
- ✅ カラースキームが適用されているか
- ✅ ステータスライン（airline）が表示されているか
- ✅ `Space + e` でNERDTreeが開くか
- ✅ 折りたたみ機能が動作するか（`zR`で全展開、`zM`で全折りたたみ）

### 4. 初回起動時のトラブルシューティング

プラグインが正しく読み込まれない場合：

```bash
# プラグインディレクトリを確認
ls -la ~/.vim/pack/plugins/start/

# 8個のプラグインが存在することを確認
# - vim-airline
# - vim-airline-themes
# - nerdtree
# - fzf
# - fzf.vim
# - vim-ripgrep
# - vim-easymotion
# - vim-devicons
```

カラースキームが適用されない場合：

```bash
# カラースキームファイルを確認
ls -la ~/.vim/colors/
# onedark.vim と molokai.vim が存在することを確認
```

## 🎯 クイックスタート（初めてVimを使う方向け）

### 基本的な使い方

1. **Vimを起動**: `vim ファイル名`
2. **編集モードに入る**: `i`キーを押す
3. **テキストを入力**: 通常通り入力
4. **編集モードを抜ける**: `Esc`キーを押す
5. **保存して終了**: `:wq`と入力してEnter

### よく使うコマンド

| コマンド | 動作 |
|----------|------|
| `i` | 編集モード（インサートモード）に入る |
| `Esc` | ノーマルモードに戻る |
| `:w` | 保存 |
| `:q` | 終了 |
| `:wq` | 保存して終了 |
| `:q!` | 保存せずに終了 |
| `Space + e` | ファイルツリーを開く |

詳しい操作方法は[Vim操作チートシート](docs/vim-cheatsheet.md)を参照してください。

## 📝 主な機能

### カスタムキーバインド

| キー | 動作 |
|------|------|
| `Space + e` | NERDTreeをトグル（開く/閉じる） |
| `Space + f` | 現在のファイルをNERDTreeで表示 |

### インストール済みプラグイン

- **vim-airline** - ステータスライン・タブラインの見た目向上
- **vim-airline-themes** - airlineのテーマ集
- **nerdtree** - ファイルエクスプローラ
- **fzf + fzf.vim** - ファジーファインダー
- **vim-ripgrep** - 高速grep
- **vim-easymotion** - カーソル瞬間移動
- **vim-devicons** - アイコン表示

### カラースキーム

- **onedark** - Atom風のダークテーマ
- **molokai** - 人気のダークテーマ

変更方法：
```vim
:colorscheme onedark
:colorscheme molokai
```

## 📚 ドキュメント

詳しい操作方法は以下を参照：
- [Vim操作チートシート](docs/vim-cheatsheet.md)

## 🔧 カスタマイズ

### 設定ファイルの編集

```bash
vim ~/.vim/vimrc
```

### 設定の再読み込み

```vim
:source ~/.vim/vimrc
```

## 🛠️ トラブルシューティング

### プラグインが読み込まれない

```bash
# プラグインディレクトリを確認
ls -la ~/.vim/pack/plugins/start/

# Vimを再起動
```

### カラースキームが適用されない

```bash
# カラースキームファイルを確認
ls -la ~/.vim/colors/

# vimrcで設定を確認
grep colorscheme ~/.vim/vimrc
```

### NERDTreeが開かない

```vim
" vimrcにキーバインドが設定されているか確認
:verbose map <leader>e
```

## 📦 アンインストール

```bash
# 設定ファイルを削除
rm -rf ~/.vim

# バックアップがある場合は復元
[ -d ~/.vim.backup ] && mv ~/.vim.backup ~/.vim
```

## 🔗 参考リンク

- [元記事: やさしいvim入門](https://note.alhinc.jp/n/n489305295df4)
- [設定ファイルの元ネタ](https://github.com/serna37/vim/blob/master/.vimrc)
- [Vim公式ドキュメント](https://www.vim.org/docs.php)

## 📄 ライセンス

MIT License

## ✍️ 作成者

作成日: 2026-01-28
