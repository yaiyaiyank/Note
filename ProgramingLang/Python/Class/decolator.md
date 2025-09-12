### staticmethod

selfがないときに使うやつ

```python
    @staticmethod
    def _get_log_folder_path(log_folder_path: Path | str | None) -> Path:
        """ログのフォルダーを決定"""
        # 引数で指定されていたらそれ
        if not log_folder_path is None:
            return Path(log_folder_path)
        # tomlから引用
        with (project_folder_path / "config.toml").open("rb") as f:
            toml = tomllib.load(f)
        log_folder_path_str = toml["path"]["default_log_folder"]
        # tomlにも設定されていなかったら
        if log_folder_path_str == "":
            return project_folder_path / "log"
        # tomlに設定されていたらそれを使う
        return Path(log_folder_path_str)
```