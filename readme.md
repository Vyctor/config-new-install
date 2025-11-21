<p align="center">
 <a href="https://www.linkedin.com/in/vyctorguimaraes/" target="_blank" rel="noopener noreferrer">
    <img alt="Made by" src="https://img.shields.io/badge/made%20by-vyctor%20guimarães-%23FF9000">
  </a>
 <img alt="GitHub" src="https://img.shields.io/github/license/EliasGcf/gobarber?color=%23FF9000">
</p>

# My configuration files

Configuration of path variables and git for a fresh install of OS.

# .zshrc

```
export ZSH="$HOME/.oh-my-zsh"

ZSH_THEME="spaceship"
plugins=(git)
source $ZSH/oh-my-zsh.sh


export CARGO_HOME=$HOME/.cargo
export PATH="$PATH:$CARGO_HOME/bin"

export SDKMAN_DIR="$HOME/.sdkman"
[[ -s "$HOME/.sdkman/bin/sdkman-init.sh" ]] && source "$HOME/.sdkman/bin/sdkman-init.sh"

eval "$(fnm env --use-on-cd --shell zsh)"



alias cat="bat --style=numbers,changes,grid --paging=always"
alias ls="exa --icons --group-directories-first --git --color=always"
alias top="btm"
alias python="python3"
alias pip="pip3"
alias code="cursor"


if [[ ! -f $HOME/.local/share/zinit/zinit.git/zinit.zsh ]]; then
    print -P "%F{33} %F{220}Installing %F{33}ZDHARMA-CONTINUUM%F{220} Initiative Plugin Manager (%F{33}zdharma-continuum/zinit%F{220})…%f"
    command mkdir -p "$HOME/.local/share/zinit" && command chmod g-rwX "$HOME/.local/share/zinit"
    command git clone https://github.com/zdharma-continuum/zinit "$HOME/.local/share/zinit/zinit.git" && \
        print -P "%F{33} %F{34}Installation successful.%f%b" || \
        print -P "%F{160} The clone has failed.%f%b"
fi

source "$HOME/.local/share/zinit/zinit.git/zinit.zsh"
autoload -Uz _zinit
(( ${+_comps} )) && _comps[zinit]=_zinit


zinit light-mode for \
    zdharma-continuum/zinit-annex-as-monitor \
    zdharma-continuum/zinit-annex-bin-gem-node \
    zdharma-continuum/zinit-annex-patch-dl \
    zdharma-continuum/zinit-annex-rust
zinit light zdharma-continuum/fast-syntax-highlighting
zinit light zsh-users/zsh-autosuggestions
zinit light zsh-users/zsh-history-substring-search
zinit light zsh-users/zsh-completions

pasteinit() {
  OLD_SELF_INSERT=${${(s.:.)widgets[self-insert]}[2,3]}
  zle -N self-insert url-quote-magic
}

pastefinish() {
  zle -N self-insert $OLD_SELF_INSERT
}

zstyle :bracketed-paste-magic paste-init pasteinit
zstyle :bracketed-paste-magic paste-finish pastefinish


SPACESHIP_PROMPT_ORDER=(
  time           # Time stamps section
  user           # Username section
  dir            # Current directory section
  host           # Hostname section
  git            # Git section (git_branch + git_status)
  hg             # Mercurial section (hg_branch  + hg_status)
  package        # Package version
  node           # Node.js section
  bun            # Bun section
  deno           # Deno section
  ruby           # Ruby section
  python         # Python section
  elm            # Elm section
  elixir         # Elixir section
  xcode          # Xcode section
  swift          # Swift section
  golang         # Go section
  perl           # Perl section
  php            # PHP section
  rust           # Rust section
  haskell        # Haskell Stack section
  scala          # Scala section
  kotlin         # Kotlin section
  java           # Java section
  lua            # Lua section
  dart           # Dart section
  julia          # Julia section
  crystal        # Crystal section
  docker         # Docker section
  docker_compose # Docker section
  aws            # Amazon Web Services section
  gcloud         # Google Cloud Platform section
  azure          # Azure section
  venv           # virtualenv section
  conda          # conda virtualenv section
  uv             # uv section
  dotnet         # .NET section
  ocaml          # OCaml section
  vlang          # V section
  zig            # Zig section
  purescript     # PureScript section
  erlang         # Erlang section
  gleam          # Gleam section
  kubectl        # Kubectl context section
  ansible        # Ansible section
  terraform      # Terraform workspace section
  pulumi         # Pulumi stack section
  ibmcloud       # IBM Cloud section
  nix_shell      # Nix shell
  gnu_screen     # GNU Screen section
  exec_time      # Execution time
  async          # Async jobs indicator
  line_sep       # Line break
  battery        # Battery level and status
  jobs           # Background jobs indicator
  exit_code      # Exit code section
  sudo           # Sudo indicator
  char           # Prompt character
)
SPACESHIP_USER_SHOW=always
SPACESHIP_PROMPT_ADD_NEWLINE=false
SPACESHIP_PROMPT_SEPARATE_LINE=false
SPACESHIP_PROMPT_ASYNC=false
SPACESHIP_CHAR_SYMBOL="❯"
SPACESHIP_CHAR_SUFFIX=" "
# fnm
FNM_PATH="/Users/vvguimaraes/Library/Application Support/fnm"
if [ -d "$FNM_PATH" ]; then
  export PATH="/Users/vvguimaraes/Library/Application Support/fnm:$PATH"
  eval "`fnm env`"
fi

```

# Git config

```
1. Setar o VSCode como editor global
   1. git config --global core.editor code --edit
2. Editar as configurações
   1. git config --global --edit
# Configurações
[user]
 name = Vyctor
 email = dev.vyctor@gmail.com
[core]
 editor = code --wait
[push]
 followTags = true
[alias]
c = !git add --all && git commit -m
s = !git status -s
l = !git log  --pretty=format:'%C(blue)%h%C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
amend = !git add --all && git commit --amend --no-edit
count = !git shortlog -s --grep
```

# Clone all repos

```bash
CNTX={users}; NAME={vyctor}; PAGE=1
curl "https://api.github.com/$CNTX/$NAME/repos?page=$PAGE&per_page=100" |
  grep -e 'ssh_url*' |
  cut -d \" -f 4 |
  xargs -L1 git clone
```

# VSCODE SETTINGS

```json
{
  // Workbench & Window (Aparência geral e comportamento da interface)
  "workbench.editor.labelFormat": "short",
  "workbench.activityBar.location": "hidden",
  "workbench.statusBar.visible": true,
  "workbench.iconTheme": "symbols",
  "workbench.startupEditor": "newUntitledFile",
  "workbench.tree.enableStickyScroll": false,
  "workbench.productIconTheme": "fluent-icons",
  "workbench.editor.empty.hint": "hidden",
  "workbench.layoutControl.enabled": false,
  "workbench.preferredDarkColorTheme": "Bearded Themanopia (Experimental)",
  "window.commandCenter": false,
  "window.autoDetectColorScheme": true,
  "breadcrumbs.enabled": false,
  // Editor (Configurações de fonte, cursor e comportamento de edição)
  "editor.fontFamily": "JetBrains Mono",
  "editor.fontLigatures": true,
  "editor.fontSize": 16,
  "editor.lineHeight": 1.5,
  "editor.formatOnSave": true,
  "editor.tabSize": 2,
  "editor.rulers": [80, 120],
  "editor.renderLineHighlight": "gutter",
  "editor.minimap.enabled": false,
  "editor.scrollbar.vertical": "hidden",
  "editor.hideCursorInOverviewRuler": true,
  "editor.bracketPairColorization.enabled": false,
  "editor.stickyScroll.enabled": false,
  "editor.parameterHints.enabled": false,
  "editor.suggestSelection": "first",
  "editor.acceptSuggestionOnCommitCharacter": false,
  "editor.accessibilitySupport": "off",
  "editor.semanticHighlighting.enabled": false,
  "editor.multiCursorLimit": 50000,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  },
  "editor.tokenColorCustomizations": {
    "textMateRules": []
  },
  // Explorer & Files (Gerenciador de arquivos e associações)
  "explorer.compactFolders": false,
  "explorer.confirmDelete": false,
  "explorer.confirmDragAndDrop": false,
  "explorer.sortOrder": "foldersNestsFiles",
  "explorer.fileNesting.enabled": true,
  "explorer.fileNesting.patterns": {
    "package.json": ".eslint*, eslint.config.*, prettier*, tsconfig*, vite*, pnpm-*, bun.lockb, nest*, package-lock*",
    "tailwind.config.*": "tailwind.config*, postcss.config*",
    ".env.local": ".env*",
    ".env": ".env*"
  },
  "files.associations": {
    ".env.*": "dotenv",
    ".prettierrc": "json",
    "*.css": "postcss",
    ".dev.vars": "dotenv",
    "*.ndjson": "jsonl"
  },
  "files.exclude": {
    "**/CVS": true,
    "**/.DS_Store": true,
    "**/.hg": true,
    "**/.svn": true,
    "**/.git": true,
    ".vscode": true
    // "node_modules": true
  },
  // Terminal (Configurações do terminal integrado)
  "terminal.integrated.showExitAlert": false,
  "terminal.integrated.fontSize": 14,
  "terminal.integrated.fontFamily": "MesloLGS NF",
  "terminal.integrated.gpuAcceleration": "on",
  "terminal.integrated.defaultProfile.osx": "zsh",
  "terminal.integrated.env.osx": {
    "FIG_NEW_SESSION": "1"
  },
  // Git & GitLens
  "git.enableSmartCommit": true,
  "git.openRepositoryInParentFolders": "always",
  "gitlens.codeLens.recentChange.enabled": false,
  "gitlens.codeLens.authors.enabled": false,
  "gitlens.advanced.messages": {
    "suppressIntegrationDisconnectedTooManyFailedRequestsWarning": true,
    "suppressIntegrationRequestTimedOutWarning": true
  },
  // Language Specific (JavaScript, TypeScript, Emmet)
  "javascript.suggest.autoImports": true,
  "javascript.updateImportsOnFileMove.enabled": "always",
  "typescript.tsserver.log": "off",
  "typescript.updateImportsOnFileMove.enabled": "always",
  "typescript.suggest.autoImports": true,
  "typescript.preferences.preferTypeOnlyAutoImports": true,
  "emmet.includeLanguages": {
    "javascript": "javascriptreact",
    "mdx": "javascriptreact"
  },
  "emmet.syntaxProfiles": {
    "javascript": "jsx",
    "mdx": "jsx"
  },
  // Extensions (ESLint, Symbols)
  "extensions.ignoreRecommendations": true,
  "eslint.validate": ["javascript", "javascriptreact", "graphql"],
  "symbols.hidesExplorerArrows": false,
  "symbols.files.associations": {
    "*.module.ts": "nest",
    "*.controller.ts": "nest-controller",
    "*.service.ts": "nest-service",
    "*.guard.ts": "typescript",
    "*.spec.ts": "ts-test",
    "*.e2e-spec.ts": "ts-test",
    "*.mock.ts": "ts-test",
    "vitest.config.e2e.ts": "vite",
    ".env.development.local": "gear",
    ".env.test.local": "gear",
    ".env.local": "gear",
    ".env.sst": "gear",
    ".env.example": "gear",
    "*.ndjson": "brackets-orange"
  },
  // Security & Update
  "security.workspace.trust.untrustedFiles": "newWindow",
  "security.promptForLocalFileProtocolHandling": false,
  "update.mode": "start",
  "update.showReleaseNotes": false,
  // Language-Specific Overrides (Formatadores)
  "[prisma]": {
    "editor.formatOnSave": true
  },
  "[jsonc]": {
    "editor.defaultFormatter": "vscode.json-language-features"
  },
  "[json]": {
    "editor.defaultFormatter": "vscode.json-language-features"
  },
  "[javascript]": {
    "editor.defaultFormatter": "vscode.typescript-language-features"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "json.schemaDownload.enable": true
}
```

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Made by Vyctor Guimarães 👋 [See my linkedin](https://www.linkedin.com/in/vyctorguimaraes/)

```

```
