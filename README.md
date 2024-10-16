## コンテナ内からGitを操作するための手順

### ssh-agentを起動
- URL: https://qiita.com/tmak_tsukamoto/items/c72399a4a6d7ff55fcdb
    - Windowsサービスを開く
    - OpenSSHを選択し、右クリックメニュー「プロパティ」
    - スタートアップの種類を「自動」に設定
    - OpenSSHを選択し、右クリックメニュー「開始」

### SSHキーをssh-agentに追加する
- URL: https://docs.github.com/ja/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
- 以下コマンドを実行
    - ssh-add c:/Users/YOU/.ssh/id_ed25519

### Dockerfileの編集
- URL: https://zenn.dev/benkey/articles/398c9bbc86e950）
- 以下の内容を追記する
    - RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    git \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
    RUN git config --global --add safe.directory /tmp/work
