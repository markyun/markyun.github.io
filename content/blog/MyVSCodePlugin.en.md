---
title: My VS Code Configuration
date: 2023-11-27 19:31:30
tags: ["Extensions", "vscode", "alias and tsconfig"]
series: [""]
category: ["blog"]
featured: true

---




## 我安装的 VS Code 插件 (**Extensions**)

### 常规类
> vscode-fileheader、
> Auto Close Tag,
> Auto Rename Tag ,
> CSSComb、
> Prettier 、
> CSSRem (px to rem & rpx & vw ),
> Remove Comments,
> Live Server,
> Color Highlight ,
> GitLens 代码编辑历史、
> Git History  历史记录并搜索提交、消息、分支、
> Import Cost（查看导入包的大小）、
> CSS PEEK（类名与样式关联）、
> Colorize  可视化 CSS 颜色
> TODO Highlight,
> Svg Preview,
> Excel Viewer,
> filesize、
> Open in Browser,
> toggle-upper-case、
> indent-rainbow（代码缩进高亮）、
> Better Comments  (Comment Highlighting)


### 纠正类
> AutoCorrect   用于「自动纠正」或「检查并建议」文案、给 CJK（中文、日语、韩语）与英文混写的场景，补充正确的空格，同时尝试以安全的方式自动纠正标点符号
> Code Spell Checker（检测单词错误）、
> Bracket Pair Colorizer  括号高亮配对
> Error Lens


### 工具类
> Turbo Console Log  无需手动添加日志。通过单击一个按钮添加控制台日志、
> Remove Comments  删除代码中的所有注释。
> Regex Previewer,
> CodeSnap（生成代码选中图片 Take beautiful screenshots of your code in VS Code!）、
> Markdown Preview Enhanced,
> Material  icons ,
> File Nesting Updater,
>


### 主动提示

> Path Intellisense,
> cssModules、
> Parameter Hints（入参格式提示）、
> Quokka.js


### AI 类工具

> Tabnine  、
> GitHub Copilot ,
> Codeium 、
> Time Master 分析编程时间


### 主题 (Theme)
> Monokai Pro（注册 key 输入 email 地址为 id@chinapyg.com，enter 后，再输入 key:  d055c-36b72-151ce-350f4-a8f69）、
> Peacock 打开多个 VS Code 实例显示不同颜色



## JSON Settings
```json
/*
* @Author: ASCII-ART
* @Date: 2017-10-26 14:04:17
* @Last Modified by: ASCII-ART
* @Last Modified time: 2023-07-18 09:53:04
*/
{

  "editor.multiCursorModifier": "ctrlCmd",
  "editor.snippetSuggestions": "top",
  "git.ignoreMissingGitWarning": true,
  "editor.fontSize": 16,
  "editor.tabSize": 2,
  "editor.rulers": [120],
  "git.ignoreLegacyWarning": true,
  "editor.minimap.enabled": true,
  "editor.quickSuggestions": {
    "other": true,
    "comments": true,
    "strings": true
  },
  // "editor.snippetSuggestions": "top",
  // "editor.quickSuggestions": false,
  "workbench.startupEditor": "newUntitledFile",
  "files.associations": {
    "*.js": "javascriptreact",
    "*.ts": "typescript",
    "*.tsx": "typescriptreact",
    "*.vue": "vue",
    "*.jsx": "javascriptreact"
  },
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }, // By default, create file  username
  "beautify.language": {
    "js": {
      "type": ["javascript", "json"],
      "filename": [".jshintrc", ".jsbeautify"]
    },
    "css": ["css", "scss", "less"],
    "html": ["htm", "html"]
  },
  "editor.renderWhitespace": "none",
  "workbench.statusBar.feedback.visible": false,
  "fileheader.Author": "markyun",
  // By default, update file  username.
  "fileheader.LastModifiedBy": "markyun",
  // Controls the line height. Use 0 to compute the lineHeight from the fontSize.
  "editor.lineHeight": 22,
  // 以像素为单位控制字符间距。
  "editor.letterSpacing": 0.25,
  // Enables font ligatures
  "editor.fontLigatures": true,
  "extensions.autoUpdate": false,
  // 控制编辑器是否在滚动时使用动画
  "editor.smoothScrolling": true,
  // 控制选取范围是否有圆角
  "editor.roundedSelection": false,
  "workbench.colorCustomizations": {
    "titleBar.activeBackground": "#272727",
    "activityBar.background": "#272727",
    "tab.activeForeground": "#20fd84",
    "editorLineNumber.activeForeground": "#fdfdfd",
    "editorLineNumber.foreground": "#5c5c5c",
    "editor.selectionBackground": "#cbec0e65",
    "sideBar.border": "#464545",
    "settings.modifiedItemForeground": "#48ff00",
    "scrollbarSlider.hoverBackground": "#9e9898",
    "statusBar.background": "#242222",
    "statusBar.noFolderBackground": "#18181b",
    "statusBar.debuggingBackground": "#511f1f"
  },
  "workbench.commandPalette.history": 30,
  "workbench.commandPalette.preserveInput": true,
  "[javascriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "window.restoreWindows": "all",
  // 配置内置 HTML 语言支持是否建议 Angular V1 标记和属性。
  "html.suggest.angular1": false,
  "emmet.showExpandedAbbreviation": "inMarkupAndStylesheetFilesOnly",
  "sync.gist": "xxxx", // GitHub Token xxx
    "sync.host": "",
    "sync.pathPrefix": "",
    "sync.quietSync": false,
    "sync.askGistName": false,
    "sync.removeExtensions": true,
    "sync.syncExtensions": true,
    "sync.autoDownload": false,
    "sync.autoUpload": false,
    "sync.lastUpload": "2019-10-16T10:59:52.376Z",
    "sync.lastDownload": "",
    "sync.forceDownload": false,
    "materialTheme.fixIconsRunning": false,
    "editor.wordWrap": "on",
    "editor.minimap.renderCharacters": true,
    "editor.minimap.showSlider": "always",
    "editor.renderLineHighlight": "line",
    "editor.tabCompletion": "on",
    "workbench.editor.labelFormat": "default",
    "workbench.editor.swipeToNavigate": false,
    "workbench.fontAliasing": "auto",
    "files.trimTrailingWhitespace": true,
    "update.mode": "none",
    "update.enableWindowsBackgroundUpdates": false,
    "css.lint.zeroUnits": "warning",
    "less.lint.importStatement": "warning",
    "less.lint.zeroUnits": "warning",
    "npm.enableScriptExplorer": true,
    "emmet.showSuggestionsAsSnippets": true,
    "emmet.triggerExpansionOnTab": true,
    "[graphql]": {},
    "scss.lint.zeroUnits": "warning",
    "terminal.integrated.rendererType": "dom",
    "javascript.updateImportsOnFileMove.enabled": "always",
    "explorer.confirmDelete": false,
    "search.followSymlinks": false,
    "search.exclude": {
        "**/node_modules": true,
        "**/bower_components": true
    },
    "files.exclude": {
        "**/.git": true,
        "**/.svn": true,
        "**/.hg": true,
        "**/CVS": true,
        "**/.DS_Store": true,
        "**/tmp": true,
        // "**/node_modules": true,
        "**/bower_components": true,
        "**/build": false,
        "**/dist": false
    },
    "files.watcherExclude": {
        "**/.git/objects/**": true,
        "**/.git/subtree-cache/**": true,
        "**/node_modules/**": true,
        "**/tmp/**": true,
        "**/bower_components/**": true,
        "**/dist/**": true
    },
    "search.useIgnoreFiles": false,
    "gitlens.advanced.messages": {
        "suppressGitMissingWarning": true,
        "suppressShowKeyBindingsNotice": true
    },
    "colorize.ignore_search_variables_info": true,
    "javascript.implicitProjectConfig.experimentalDecorators": true,
    "explorer.confirmDragAndDrop": false,
    "vscode_vibrancy.opacity": 0.5,
    "vscode_vibrancy.theme": "Default Dark",
    "telemetry.enableCrashReporter": false,
    "telemetry.enableTelemetry": false,
    "[html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[css]": {
        "editor.defaultFormatter": "vscode.css-language-features"
    },
    "[json]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "extensions.ignoreRecommendations": true,
    "tabnine.experimentalAutoImports": true,
    "security.workspace.trust.untrustedFiles": "open",
    "php.validate.enable": false,
    "javascript.validate.enable": true,
    "typescript.validate.enable": false,
    "bracket-pair-colorizer-2.depreciation-notice": false,
    "docwriter.custom.author": "M.Jyun",
    "docwriter.language": "Chinese",
    "prettier.printWidth": 100,
    "prettier.tabWidth": 4,
    "sync.gist": "xxx",
    "sync.quietSync": true,
    "suppressLineUncommittedWarning": true,
    "files.autoGuessEncoding": true,
    "csscomb.preset": "zen",
    "csscomb.ignoreFilesOnSave": [],
    "csscomb.lines-between-rulesets": 0,
    "codetime.statusBarInfo": "total",
    "terminal.integrated.sendKeybindingsToShell": true,
    "workbench.enableExperiments": false,
    "update.showReleaseNotes": false,
    "[typescriptreact]": {
        "editor.defaultFormatter": "vscode.typescript-language-features"
    },
    "[typescript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[scss]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[jsonc]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "editor.foldingMaximumRegions": 2500,
    "git.autorefresh": false,
    "git.autoRepositoryDetection": false,
    "git.enabled": true,
    "editor.fontFamily": "Monaco, 'Courier New', monospace,Menlo",
    "gitlens.terminalLinks.enabled": false,
    "gitlens.advanced.repositorySearchDepth": 2,
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "html.format.enable": false,
    "javascript.format.enable": false,
    "prettier.embeddedLanguageFormatting": "off",
    "json.format.enable": false,
    "workbench.iconTheme": "Monokai Pro (Filter Spectrum) Icons",
    "editor.comments.ignoreEmptyLines": false,
    "deepl.apiKey": null,
    "terminal.integrated.enableMultiLinePasteWarning": false,
    "EnglishChineseDictionary.enableHover": true,
    "translateSpeaker.mode": "autoEnglish",
    "vscodeGoogleTranslate.preferredLanguage": "Chinese (Simplified)",
    "workbench.productIconTheme": "material-product-icons",
    "window.zoomLevel": 1,
    "explorer.fileNesting.enabled": true,
    "explorer.fileNesting.expand": false,
    "explorer.fileNesting.patterns": {
        "//": "Last update at 2023/7/4 17:20:03",
        "*.asax": "$(capture).*.cs, $(capture).*.vb",
        "*.ascx": "$(capture).*.cs, $(capture).*.vb",
        "*.ashx": "$(capture).*.cs, $(capture).*.vb",
        "*.aspx": "$(capture).*.cs, $(capture).*.vb",
        "*.bloc.dart": "$(capture).event.dart, $(capture).state.dart",
        "*.c": "$(capture).h",
        "*.cc": "$(capture).hpp, $(capture).h, $(capture).hxx",
        "*.cjs": "$(capture).cjs.map, $(capture).*.cjs, $(capture)_*.cjs",
        "*.component.ts": "$(capture).component.html, $(capture).component.spec.ts, $(capture).component.css, $(capture).component.scss, $(capture).component.sass, $(capture).component.less",
        "*.cpp": "$(capture).hpp, $(capture).h, $(capture).hxx",
        "*.cs": "$(capture).*.cs",
        "*.cshtml": "$(capture).cshtml.cs",
        "*.csproj": "*.config, *proj.user, appsettings.*, bundleconfig.json",
        "*.css": "$(capture).css.map, $(capture).*.css",
        "*.cxx": "$(capture).hpp, $(capture).h, $(capture).hxx",
        "*.dart": "$(capture).freezed.dart, $(capture).g.dart",
        "*.ex": "$(capture).html.eex, $(capture).html.heex, $(capture).html.leex",
        "*.go": "$(capture)_test.go",
        "*.java": "$(capture).class",
        "*.js": "$(capture).js.map, $(capture).*.js, $(capture)_*.js",
        "*.jsx": "$(capture).js, $(capture).*.jsx, $(capture)_*.js, $(capture)_*.jsx",
        "*.master": "$(capture).*.cs, $(capture).*.vb",
        "*.mjs": "$(capture).mjs.map, $(capture).*.mjs, $(capture)_*.mjs",
        "*.module.ts": "$(capture).resolver.ts, $(capture).controller.ts, $(capture).service.ts",
        "*.mts": "$(capture).mts.map, $(capture).*.mts, $(capture)_*.mts",
        "*.pubxml": "$(capture).pubxml.user",
        "*.resx": "$(capture).*.resx, $(capture).designer.cs, $(capture).designer.vb",
        "*.tex": "$(capture).acn, $(capture).acr, $(capture).alg, $(capture).aux, $(capture).bbl, $(capture).blg, $(capture).fdb_latexmk, $(capture).fls, $(capture).glg, $(capture).glo, $(capture).gls, $(capture).idx, $(capture).ind, $(capture).ist, $(capture).lof, $(capture).log, $(capture).lot, $(capture).out, $(capture).pdf, $(capture).synctex.gz, $(capture).toc, $(capture).xdv",
        "*.ts": "$(capture).js, $(capture).d.ts.map, $(capture).*.ts, $(capture)_*.js, $(capture)_*.ts",
        "*.tsx": "$(capture).ts, $(capture).*.tsx, $(capture)_*.ts, $(capture)_*.tsx",
        "*.vbproj": "*.config, *proj.user, appsettings.*, bundleconfig.json",
        "*.vue": "$(capture).*.ts, $(capture).*.js, $(capture).story.vue",
        "*.xaml": "$(capture).xaml.cs",
        "+layout.svelte": "+layout.ts,+layout.ts,+layout.js,+layout.server.ts,+layout.server.js,+layout.gql",
        "+page.svelte": "+page.server.ts,+page.server.js,+page.ts,+page.js,+page.gql",
        ".clang-tidy": ".clang-format, .clangd, compile_commands.json",
        ".env": "*.env, .env.*, .envrc, env.d.ts",
        ".gitignore": ".gitattributes, .gitmodules, .gitmessage, .mailmap, .git-blame*",
        ".project": ".classpath",
        "BUILD.bazel": "*.bzl, *.bazel, *.bazelrc, bazel.rc, .bazelignore, .bazelproject, WORKSPACE",
        "CMakeLists.txt": "*.cmake, *.cmake.in, .cmake-format.yaml, CMakePresets.json",
        "I*.cs": "$(capture).cs",
        "Pipfile": ".editorconfig, .flake8, .isort.cfg, .python-version, Pipfile, Pipfile.lock, requirements*.in, requirements*.pip, requirements*.txt, tox.ini",
        "artisan": "*.env, .babelrc*, .codecov, .cssnanorc*, .env.*, .envrc, .htmlnanorc*, .lighthouserc.*, .mocha*, .postcssrc*, .terserrc*, api-extractor.json, ava.config.*, babel.config.*, contentlayer.config.*, cssnano.config.*, cypress.*, env.d.ts, formkit.config.*, formulate.config.*, histoire.config.*, htmlnanorc.*, jasmine.*, jest.config.*, jsconfig.*, karma*, lighthouserc.*, playwright.config.*, postcss.config.*, puppeteer.config.*, rspack.config.*, server.php, svgo.config.*, tailwind.config.*, tsconfig.*, tsdoc.*, uno.config.*, unocss.config.*, vitest.config.*, webpack.config.*, webpack.mix.js, windi.config.*",
        "astro.config.*": "*.env, .babelrc*, .codecov, .cssnanorc*, .env.*, .envrc, .htmlnanorc*, .lighthouserc.*, .mocha*, .postcssrc*, .terserrc*, api-extractor.json, ava.config.*, babel.config.*, contentlayer.config.*, cssnano.config.*, cypress.*, env.d.ts, formkit.config.*, formulate.config.*, histoire.config.*, htmlnanorc.*, jasmine.*, jest.config.*, jsconfig.*, karma*, lighthouserc.*, playwright.config.*, postcss.config.*, puppeteer.config.*, rspack.config.*, svgo.config.*, tailwind.config.*, tsconfig.*, tsdoc.*, uno.config.*, unocss.config.*, vitest.config.*, webpack.config.*, windi.config.*",
        "cargo.toml": ".clippy.toml, .rustfmt.toml, cargo.lock, clippy.toml, cross.toml, rust-toolchain.toml, rustfmt.toml",
        "composer.json": ".php*.cache, composer.lock, phpunit.xml*, psalm*.xml",
        "default.nix": "shell.nix",
        "deno.json*": "*.env, .env.*, .envrc, api-extractor.json, deno.lock, env.d.ts, import-map.json, import_map.json, jsconfig.*, tsconfig.*, tsdoc.*",
        "dockerfile": ".dockerignore, docker-compose.*, dockerfile*",
        "flake.nix": "flake.lock",
        "gatsby-config.*": "*.env, .babelrc*, .codecov, .cssnanorc*, .env.*, .envrc, .htmlnanorc*, .lighthouserc.*, .mocha*, .postcssrc*, .terserrc*, api-extractor.json, ava.config.*, babel.config.*, contentlayer.config.*, cssnano.config.*, cypress.*, env.d.ts, formkit.config.*, formulate.config.*, gatsby-browser.*, gatsby-node.*, gatsby-ssr.*, gatsby-transformer.*, histoire.config.*, htmlnanorc.*, jasmine.*, jest.config.*, jsconfig.*, karma*, lighthouserc.*, playwright.config.*, postcss.config.*, puppeteer.config.*, rspack.config.*, svgo.config.*, tailwind.config.*, tsconfig.*, tsdoc.*, uno.config.*, unocss.config.*, vitest.config.*, webpack.config.*, windi.config.*",
        "gemfile": ".ruby-version, gemfile.lock",
        "go.mod": ".air*, go.sum",
        "go.work": "go.work.sum",
        "hatch.toml": ".editorconfig, .flake8, .isort.cfg, .python-version, hatch.toml, requirements*.in, requirements*.pip, requirements*.txt, tox.ini",
        "mix.exs": ".credo.exs, .dialyzer_ignore.exs, .formatter.exs, .iex.exs, .tool-versions, mix.lock",
        "next.config.*": "*.env, .babelrc*, .codecov, .cssnanorc*, .env.*, .envrc, .htmlnanorc*, .lighthouserc.*, .mocha*, .postcssrc*, .terserrc*, api-extractor.json, ava.config.*, babel.config.*, contentlayer.config.*, cssnano.config.*, cypress.*, env.d.ts, formkit.config.*, formulate.config.*, histoire.config.*, htmlnanorc.*, jasmine.*, jest.config.*, jsconfig.*, karma*, lighthouserc.*, next-env.d.ts, playwright.config.*, postcss.config.*, puppeteer.config.*, rspack.config.*, svgo.config.*, tailwind.config.*, tsconfig.*, tsdoc.*, uno.config.*, unocss.config.*, vitest.config.*, webpack.config.*, windi.config.*",
        "nuxt.config.*": "*.env, .babelrc*, .codecov, .cssnanorc*, .env.*, .envrc, .htmlnanorc*, .lighthouserc.*, .mocha*, .nuxtignore, .postcssrc*, .terserrc*, api-extractor.json, ava.config.*, babel.config.*, contentlayer.config.*, cssnano.config.*, cypress.*, env.d.ts, formkit.config.*, formulate.config.*, histoire.config.*, htmlnanorc.*, jasmine.*, jest.config.*, jsconfig.*, karma*, lighthouserc.*, playwright.config.*, postcss.config.*, puppeteer.config.*, rspack.config.*, svgo.config.*, tailwind.config.*, tsconfig.*, tsdoc.*, uno.config.*, unocss.config.*, vitest.config.*, webpack.config.*, windi.config.*",
        "package.json": ".browserslist*, .circleci*, .commitlint*, .cz-config.js, .czrc, .dlint.json, .dprint.json, .editorconfig, .eslint*, .firebase*, .flowconfig, .github*, .gitlab*, .gitpod*, .huskyrc*, .jslint*, .lintstagedrc*, .markdownlint*, .node-version, .nodemon*, .npm*, .nvmrc, .pm2*, .pnp.*, .pnpm*, .prettier*, .releaserc*, .sentry*, .simple-git-hooks*, .stackblitz*, .styleci*, .stylelint*, .tazerc*, .textlint*, .tool-versions, .travis*, .versionrc*, .vscode*, .watchman*, .xo-config*, .yamllint*, .yarnrc*, Procfile, apollo.config.*, appveyor*, azure-pipelines*, bower.json, build.config.*, commitlint*, crowdin*, dangerfile*, dlint.json, dprint.json, electron-builder.*, eslint*, firebase.json, grunt*, gulp*, jenkins*, lerna*, lint-staged*, nest-cli.*, netlify*, nodemon*, npm-shrinkwrap.json, nx.*, package-lock.json, package.nls*.json, phpcs.xml, pm2.*, pnpm*, prettier*, pullapprove*, pyrightconfig.json, release-tasks.sh, release.config.*, renovate*, rollup.config.*, rspack*, simple-git-hooks*, stylelint*, tslint*, tsup.config.*, turbo*, typedoc*, unlighthouse*, vercel*, vetur.config.*, webpack*, workspace.json, xo.config.*, yarn*",
        "pubspec.yaml": ".metadata, .packages, all_lint_rules.yaml, analysis_options.yaml, build.yaml, pubspec.lock, pubspec_overrides.yaml",
        "pyproject.toml": ".editorconfig, .flake8, .isort.cfg, .pdm-python, .pdm.toml, .python-version, MANIFEST.in, Pipfile, Pipfile.lock, hatch.toml, pdm.lock, poetry.lock, pyproject.toml, requirements*.in, requirements*.pip, requirements*.txt, setup.cfg, setup.py, tox.ini",
        "quasar.conf.js": "*.env, .babelrc*, .codecov, .cssnanorc*, .env.*, .envrc, .htmlnanorc*, .lighthouserc.*, .mocha*, .postcssrc*, .terserrc*, api-extractor.json, ava.config.*, babel.config.*, contentlayer.config.*, cssnano.config.*, cypress.*, env.d.ts, formkit.config.*, formulate.config.*, histoire.config.*, htmlnanorc.*, jasmine.*, jest.config.*, jsconfig.*, karma*, lighthouserc.*, playwright.config.*, postcss.config.*, puppeteer.config.*, quasar.extensions.json, rspack.config.*, svgo.config.*, tailwind.config.*, tsconfig.*, tsdoc.*, uno.config.*, unocss.config.*, vitest.config.*, webpack.config.*, windi.config.*",
        "readme*": "authors, backers*, changelog*, citation*, code_of_conduct*, codeowners, contributing*, contributors, copying, credits, governance.md, history.md, license*, maintainers, readme*, security.md, sponsors*",
        "remix.config.*": "*.env, .babelrc*, .codecov, .cssnanorc*, .env.*, .envrc, .htmlnanorc*, .lighthouserc.*, .mocha*, .postcssrc*, .terserrc*, api-extractor.json, ava.config.*, babel.config.*, contentlayer.config.*, cssnano.config.*, cypress.*, env.d.ts, formkit.config.*, formulate.config.*, histoire.config.*, htmlnanorc.*, jasmine.*, jest.config.*, jsconfig.*, karma*, lighthouserc.*, playwright.config.*, postcss.config.*, puppeteer.config.*, remix.*, rspack.config.*, svgo.config.*, tailwind.config.*, tsconfig.*, tsdoc.*, uno.config.*, unocss.config.*, vitest.config.*, webpack.config.*, windi.config.*",
        "requirements.txt": ".editorconfig, .flake8, .isort.cfg, .python-version, requirements*.in, requirements*.pip, requirements*.txt, tox.ini",
        "rush.json": ".browserslist*, .circleci*, .commitlint*, .cz-config.js, .czrc, .dlint.json, .dprint.json, .editorconfig, .eslint*, .firebase*, .flowconfig, .github*, .gitlab*, .gitpod*, .huskyrc*, .jslint*, .lintstagedrc*, .markdownlint*, .node-version, .nodemon*, .npm*, .nvmrc, .pm2*, .pnp.*, .pnpm*, .prettier*, .releaserc*, .sentry*, .simple-git-hooks*, .stackblitz*, .styleci*, .stylelint*, .tazerc*, .textlint*, .tool-versions, .travis*, .versionrc*, .vscode*, .watchman*, .xo-config*, .yamllint*, .yarnrc*, Procfile, apollo.config.*, appveyor*, azure-pipelines*, bower.json, build.config.*, commitlint*, crowdin*, dangerfile*, dlint.json, dprint.json, electron-builder.*, eslint*, firebase.json, grunt*, gulp*, jenkins*, lerna*, lint-staged*, nest-cli.*, netlify*, nodemon*, npm-shrinkwrap.json, nx.*, package-lock.json, package.nls*.json, phpcs.xml, pm2.*, pnpm*, prettier*, pullapprove*, pyrightconfig.json, release-tasks.sh, release.config.*, renovate*, rollup.config.*, rspack*, simple-git-hooks*, stylelint*, tslint*, tsup.config.*, turbo*, typedoc*, unlighthouse*, vercel*, vetur.config.*, webpack*, workspace.json, xo.config.*, yarn*",
        "setup.cfg": ".editorconfig, .flake8, .isort.cfg, .python-version, MANIFEST.in, requirements*.in, requirements*.pip, requirements*.txt, setup.cfg, tox.ini",
        "setup.py": ".editorconfig, .flake8, .isort.cfg, .python-version, MANIFEST.in, requirements*.in, requirements*.pip, requirements*.txt, setup.cfg, setup.py, tox.ini",
        "shims.d.ts": "*.d.ts",
        "svelte.config.*": "*.env, .babelrc*, .codecov, .cssnanorc*, .env.*, .envrc, .htmlnanorc*, .lighthouserc.*, .mocha*, .postcssrc*, .terserrc*, api-extractor.json, ava.config.*, babel.config.*, contentlayer.config.*, cssnano.config.*, cypress.*, env.d.ts, formkit.config.*, formulate.config.*, histoire.config.*, houdini.config.*, htmlnanorc.*, jasmine.*, jest.config.*, jsconfig.*, karma*, lighthouserc.*, mdsvex.config.js, playwright.config.*, postcss.config.*, puppeteer.config.*, rspack.config.*, svgo.config.*, tailwind.config.*, tsconfig.*, tsdoc.*, uno.config.*, unocss.config.*, vite.config.*, vitest.config.*, webpack.config.*, windi.config.*",
        "vite.config.*": "*.env, .babelrc*, .codecov, .cssnanorc*, .env.*, .envrc, .htmlnanorc*, .lighthouserc.*, .mocha*, .postcssrc*, .terserrc*, api-extractor.json, ava.config.*, babel.config.*, contentlayer.config.*, cssnano.config.*, cypress.*, env.d.ts, formkit.config.*, formulate.config.*, histoire.config.*, htmlnanorc.*, jasmine.*, jest.config.*, jsconfig.*, karma*, lighthouserc.*, playwright.config.*, postcss.config.*, puppeteer.config.*, rspack.config.*, svgo.config.*, tailwind.config.*, tsconfig.*, tsdoc.*, uno.config.*, unocss.config.*, vitest.config.*, webpack.config.*, windi.config.*",
        "vue.config.*": "*.env, .babelrc*, .codecov, .cssnanorc*, .env.*, .envrc, .htmlnanorc*, .lighthouserc.*, .mocha*, .postcssrc*, .terserrc*, api-extractor.json, ava.config.*, babel.config.*, contentlayer.config.*, cssnano.config.*, cypress.*, env.d.ts, formkit.config.*, formulate.config.*, histoire.config.*, htmlnanorc.*, jasmine.*, jest.config.*, jsconfig.*, karma*, lighthouserc.*, playwright.config.*, postcss.config.*, puppeteer.config.*, rspack.config.*, svgo.config.*, tailwind.config.*, tsconfig.*, tsdoc.*, uno.config.*, unocss.config.*, vitest.config.*, webpack.config.*, windi.config.*"
    },
    "workbench.colorTheme": "Monokai Pro (Filter Spectrum)",
    "cSpell.customDictionaries": {},
    "cSpell.dictionaryDefinitions": [],
    "cSpell.ignorePaths": [
        "package-lock.json",
        "node_modules",
        "vscode-extension",
        ".git/objects",
        ".vscode",
        ".vscode-insiders",
        ".umi"
    ],
    "totalTypeScript.hideAllTips": true,
    "totalTypeScript.hideBasicTips": true,
    "editor.experimental.stickyScroll.enabled": true,
    "editor.unicodeHighlight.ambiguousCharacters": false,
    "cssrem.vwDesign": 375,
    "[less]": {
        "editor.defaultFormatter": "vscode.css-language-features"
    },
    // 每组规则后加一个空行

    // 完全开启/关闭 AutoCorrect，默认：true
    "autocorrect.enable": true,
    // 开启/关闭 AutoCorrect Lint 检查，默认：true
    "autocorrect.enableLint": true,
    // 是否启用 formatOnSave，默认：true
    "autocorrect.formatOnSave": false
}

```

## 使用 alias 别名实现，代码编译和代码跳转（alias and tsconfig）


> 此问题可以当做面试题：【vscode 通过配置 alias 实现 代码编译和代码跳转，但是 webpack alias 和 tsconfig path 之间是什么关系】


在 VS Code 中开发 React + TypeScript 项目时，为了方便文件引入，常常是配置 alias 来简化路径，让组件的引入可以使用别名。
如下示例，通过 @ 符号，编辑器就应该知道是从  src/  这个路径去找 components 到这个文件。
```javascript
import IconFont from '@/components/IconFont';
import Menus from '@/components/Menus';
import { Sortable } from './Dndkit/Sortable';

export { IconFont, Menus, Sortable };
```

想要设置 alias 后，就能在编辑器中 正确编译和点击跳转，其实只有两处需要配置：webpack.resolve 和 tsconfig.json 路径映射的关系。

  其中 tsconfig.json 中的 paths 主要用于告诉 TypeScript 编译器如何解析模块导入的路径。

  而 webpack.resolve.alias 则用于告诉 webpack 构建过程中如何解析模块导入的路径。这两者的分别配合，确保在开发过程中和构建过程中都能正确地解析模块导入的路径，从而实现代码编译和代码跳转的成功使用。


1、项目根目录 需要有 tsconfig.json 配置文件，它是用于告诉 TypeScript 编译器如何 解析代码中的模块导入的路径。
```json
{
  "compilerOptions": {
    "baseUrl": "./src",
    "rootDir": ".",
    "module": "esnext",
    "target": "es5",
    "lib": ["dom", "dom.iterable", "esnext"],
    "sourceMap": true,
    "allowJs": true,
    "jsx": "preserve",
    "skipLibCheck": true,
    "experimentalDecorators": true,
    "moduleResolution": "node",
    "forceConsistentCasingInFileNames": true,
    "noImplicitReturns": true,
    "noImplicitThis": false,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "suppressImplicitAnyIndexErrors": true,
    "noUnusedLocals": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "paths": {
      "@/*": ["./*"],
      "@@/*": ["/src/.umi/*"],
      "fishx": [".fishx/moduleEntry"],
      "@utils/*": ["utils/*"],
      "@assets/*": ["assets/*"],
      "@services/*": ["services/*"],
      "@stores/*": ["stores/*"],
      "@components/*": ["components/*"],
      "@layouts/*": ["layouts/*"],
      "@config/*": ["config/*"],
      "@pages/*": ["pages/*"],
      "@models/*": ["models/*"],
      "@hooks/*": ["hooks/*"]
    }
  },
  "include": ["src"],

  "exclude": [
    "node_modules",
    "lib",
    "es",
    "dist",
    "typings",
    "**/__test__",
    "test",
    "docs",
    "tests"
  ]
}

```
2、webpack.resolve.alias 配置【给编译用的】

```javascript
resolve: {
    extensions: ['.tsx', 'ts', '.js', '.json'],
    alias: {
      '@src': resolve('./src'),
    },
  },
```
最后，如果插件编辑器的语言状态，都成功加载了对应的配置，就能正常工作了。
![image.png](https://cdn.nlark.com/yuque/0/2023/png/203859/1702005780118-d3891327-5acc-4e43-97f4-f83b73b53132.png#averageHue=%23383739&clientId=u666fbd0b-50c6-4&from=paste&height=306&id=u3ed33181&originHeight=459&originWidth=859&originalType=binary&ratio=1.5&rotation=0&showTitle=false&size=47186&status=done&style=none&taskId=u10ecb9ee-1d23-4f48-b6a0-2330d68dad8&title=&width=572.6666666666666)


## 使用 .gitignore_global 忽略 .vscode 文件夹
用于 Git 的全局忽略配置文件名为 .gitignore_global，它存放在用户主目录下（例如：C:\Users\name 名 或 /Users/name）。要启用全局忽略功能，我们需要进行一些配置。

首先，打开命令行工具或终端，使用以下命令告诉 Git 要使用全局忽略文件：

```jsx
git config --global core.excludesfile ~/.gitignore_global
```

这条命令告诉 Git 在用户主目录下使用.gitignore_global 文件作为全局忽略文件。
全局忽略文件只针对未被纳入版本控制的文件起作用。在已经提交到版本控制的文件中，Git 会遵循.gitignore 文件的规则。所以，在使用全局忽略文件时，我们需要注意已经添加到版本控制的文件。

```jsx
# 忽略所有的日志文件
*.log

# dependencies
/node_modules
.yarn
/npm-debug.log*
/yarn-error.log
/yarn.lock
/package-lock.json

# production
/dist

# misc
.DS_Store

# 忽略所有的临时文件
*.tmp

# 忽略所有的编译产生的文件
*.o
*.exe

# 忽略IDE和编辑器产生的文件
.vscode/
.idea/
*.sublime-project
*.sublime-workspace

# 忽略项目根目录下的build目录
/build

# 忽略src目录下的所有pdf文件
/src/**/*.pdf

```

##

## 内置终端


可以快速了解当前环境变量，在终端中运行 printenv。

```jsx
printenv
```
![image.png](https://cdn.nlark.com/yuque/0/2023/png/203859/1698304214991-b1464bac-7230-4940-bf27-d3075af7e95c.png#averageHue=%23161514&clientId=u1af1eb05-a548-4&from=paste&height=879&id=u471e72e9&originHeight=1318&originWidth=1870&originalType=binary&ratio=1.5&rotation=0&showTitle=false&size=182436&status=done&style=none&taskId=u309e460b-bec0-47e9-9ee9-1e7a13fe74a&title=&width=1246.6666666666667)
可以轻松地将终端分成两边。我经常用一边运行开发服务器，用另一边执行随机的终端命令（git 命令、linting 命令、随机任务等）。超级方便。


