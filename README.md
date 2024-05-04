# ZERO-NUXT3

## 開發環境

```
node -v
v20.12.2

npm -v
10.7.0

pnpm -v
9.0.6
```

### 啟動開發

```
pnpm dev
```

## [選用] 產生 CHANGELOG

1. 安裝 [Rust](https://www.rust-lang.org/zh-TW/tools/install)
2. 安裝 [git-cliff](https://git-cliff.org/docs/)
   ```
   cargo install git-cliff
   ```
3. 生成 CHANGELOG
   ```
   git cliff -o CHANGELOG.md
   ```

以下是目前 git commit msg 用到的規則

```
commit_parsers = [
  { message = "^feat", group = "<!-- 0 -->⛰️ Features" },
  { message = "^fix", group = "<!-- 1 -->🐛 Bug Fixes" },
  { message = "^doc", group = "<!-- 3 -->📚 Documentation" },
  { message = "^perf", group = "<!-- 4 -->⚡ Performance" },
  { message = "^refactor\\(clippy\\)", skip = true },
  { message = "^refactor", group = "<!-- 2 -->🚜 Refactor" },
  { message = "^style", group = "<!-- 5 -->🎨 Styling" },
  { message = "^test", group = "<!-- 6 -->🧪 Testing" },
  { message = "^chore\\(release\\): prepare for", skip = true },
  { message = "^chore\\(deps.*\\)", skip = true },
  { message = "^chore\\(pr\\)", skip = true },
  { message = "^chore\\(pull\\)", skip = true },
  { message = "^chore|^ci", group = "<!-- 7 -->⚙️ Miscellaneous Tasks" },
  { body = ".*security", group = "<!-- 8 -->🛡️ Security" },
  { message = "^revert", group = "<!-- 9 -->◀️ Revert" },
]
```

## 注意事項

- 因為使用 eslint flat config， VSCode的 Eslint 的 插件版本必須換到 3.0.5
