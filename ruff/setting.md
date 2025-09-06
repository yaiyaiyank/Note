# 設定

## VSCodeエディター内レベル

ruffで以下の条件でフォーマットする
・保存時にフォーマット実行
・1行の文字の長さを120字まで耐えられるようにする


setting.jsonに

```json
    "[python]": {
        "editor.formatOnSave": true,
        "editor.codeActionsOnSave": {
            "source.fixAll.ruff": "explicit",
            "source.organizeImports.ruff": "explicit"
        },
        "editor.wordBasedSuggestions": "off",
        "editor.defaultFormatter": "charliermarsh.ruff"
    },
    "ruff.lint.enable": true,
    "ruff.lineLength": 120,
```

と書く

## プロジェクトレベル

VSCodeエディター内レベルの設定と同じ種類の設定があればこっちが優先される

ruffで以下の条件でフォーマットする
・pyproject.toml

pyproject.tomlに

```toml
[tool.ruff.lint]
extend-select = ["PTH"]  # os.path → pathlib を促すルール群
```

と書く

![alt text](doc/vscode01.png)
![alt text](doc/toml01.png)
