# Git 入门教程

## 1. 学习目标

*   **掌握 Git 的基本操作**：保存代码、查看历史、回退版本。
*   **学会使用分支**：开发新功能时不影响主代码。
*   **了解团队协作和解决常见问题**：从 GitHub 下载代码、处理冲突。

## 2. 什么是版本控制？

*   **定义**：一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统。（引自《Pro Git》）
*   **作用**：它就像是代码的"时光机"。

## 3. 为什么需要版本控制？

*   **没有版本控制的噩梦**：
    *   文件版本混乱（`final.docx` → `final(1).docx` 等）。
    *   不小心删除代码。
    *   多人互相覆盖代码。
    *   找不回历史版本。
*   **有了 Git 之后**：
    *   **完整的历史记录**：每一次修改都可追溯。
    *   **随时回退**：时光机般的体验。
    *   **多人协作井然有序**：自动合并代码。
    *   **分支并行开发**：互不干扰。

## 4. Git 上手要点

1.  **理解三个工作区域**：工作区 → 暂存区 → 本地仓库。
2.  **掌握基础命令**：`add`, `commit`, `status`, `log`。
3.  **建立正确的工作流程**：从实践中学习。

## 5. Git 的三个工作区域

*   **工作区**：你正在编辑的文件。
*   **暂存区**：准备提交的文件 (`git add` 将文件从工作区添加到暂存区)。
*   **本地仓库**：已保存的历史版本 (`git commit` 将暂存区的文件提交到仓库)。

## 6. 第一部分：基础入门

### 6.1. 安装与配置 Git

*   **安装 Git**：
    *   **Windows**：访问 `git-scm.com/download/win`，一路“下一步”安装。
    *   **Mac**：`brew install git`。
    *   **Linux (Ubuntu)**：`sudo apt-get install git`。
*   **首次配置**：
    ```bash
    git config --global user.name "你的名字"
    git config --global user.email "你的邮箱"
    ```
    *   **💡 提示**：这些信息会显示在你的每次提交中。

### 6.2. `git init` - 创建仓库

1.  **从零开始**：
    ```bash
    mkdir my-project
    cd my-project
    git init
    ```
    *   **结果**：创建 `.git` 目录，这是 Git 仓库的核心。
2.  **克隆现有项目**：
    ```bash
    git clone https://github.com/username/repository.git
    ```
    *   **结果**：自动下载完整的项目和历史记录。

### 6.3. `.gitignore` - 告诉 Git 忽略哪些文件

*   **不该提交的文件**：编译产物、日志文件、系统文件、编辑器配置等。
*   **创建 `.gitignore` 文件示例**：
    ```
    # 编译产物
    /target/
    # 日志
    *.log
    # 系统文件
    .DS_Store
    ```
*   **💡 小提示**：GitHub 为各种语言准备了 `.gitignore` 模板，可以搜索 "github gitignore rust" 等。

### 6.4. 基础工作流演示

1.  **创建文件**：
    ```bash
    echo "# My Rust Project" > README.md
    ```
2.  **查看状态**：`git status` (显示未追踪的文件，红色)。
3.  **添加到暂存区**：`git add .`。
4.  **提交**：`git commit -m "feat: 初始化项目"`。

### 6.5. `git status` - 查看当前状态

*   **三种文件状态**：
    *   **绿色**：已 `add`，准备提交。
    *   **红色**：修改了但还没 `add`。
    *   **未追踪**：Git 还不认识的新文件。
*   **💡 最佳实践**：养成习惯，每次操作前后都 `git status` 看一眼。

### 6.6. `git diff` - 看看改了什么

*   **查看改动**：
    *   **工作区的改动**：`git diff`
    *   **暂存区的改动**：`git diff --staged`
*   **输出示例**：`- let x = 10;` (红色:删掉的代码), `+ let x = 20;` (绿色:新加的代码)。
*   **💡 提示**：VSCode 等 IDE 可以在源代码管理面板点击文件查看可视化对比。

### 6.7. `git log` - 查看提交历史

*   **查看历史**：`git log --oneline` (推荐: 简洁明了)。
*   **输出示例**：
    ```
    a3f5b2c feat: 添加错误处理
    7d8e9f0 fix: 修复编译警告
    b2c4d5e feat: 初始化项目
    ```
*   **💡 小提示**：每个提交都有唯一编号 (如 `a3f5b2c`)。VSCode 可以看图形化历史。

## 7. 第二部分：分支管理

### 7.1. 为什么需要分支？

*   **没有分支的困境**：想尝试新想法却怕改坏，多人只能轮流修改。
*   **有了分支**：
    *   `main` 分支 ———————————————→ (稳定的主版本)
    *   `实验分支` ——→ (随便试新想法,不怕搞坏)
    *   **步骤**：在 `main` 分支写作业 → 创建新分支来创新和尝试 → 好用就合并，不好就删。

### 7.2. 理解分支

*   **什么是分支?**：分支就像给代码"贴书签"，告诉 Git 这是哪个版本。
*   **关键特点**：
    *   **创建分支很快**：只是创建一个指针。
    *   **互不影响**：新分支修改不影响 `main`。
    *   **随时切换**：在不同分支间自由切换。

### 7.3. `git branch` - 分支操作

*   **查看分支**：
    *   **查看本地分支**：`git branch`
    *   **查看所有分支 (含远程)**：`git branch -a`
*   **创建分支**：`git branch feat/add-user-auth`
*   **删除分支**：
    *   **安全删除 (已合并)**：`git branch -d feat/add-user-auth`
    *   **强制删除 (未合并)**：`git branch -D feat/add-user-auth`

### 7.4. `git switch` / `git checkout` - 切换分支

*   **现代用法 (推荐 `git switch`)**：
    *   **切换分支**：`git switch feat/async`
    *   **创建并切换**：`git switch -c feat/macro`
    *   **切回上一个**：`git switch -`
*   **传统用法 (`git checkout`)**：
    *   `git checkout feat/async` (切换分支)
    *   `git checkout -b feat/macro` (创建并切换)
*   **💡 推荐**：使用 `git switch`，语义更清晰。

### 7.5. `git merge` - 合并分支

*   **合并步骤**：
    1.  切换到目标分支：`git switch main`
    2.  合并分支：`git merge feat/async`
*   **合并类型**：
    *   **简单合并 (Fast-forward)**：`main` 没新提交，直接加上 `feature` 的提交。
    *   **复杂合并 (Merge commit)**：两边都有新提交，Git 创建一个"合并提交"。
*   **💡 提示**：大多数情况 Git 会自动处理，你只需执行 `git merge`。

### 7.6. 合并冲突 - 新手最怕的问题

*   **什么时候会冲突?**：两个分支修改了同一个文件的同一行，Git 不知道保留哪个。
    ```
    <<<<<<< HEAD
    let count = 10; // 你的修改
    =======
    let count = 20; // 他人的修改
    >>>>>>> feat/update
    ```
*   **解决步骤**：
    1.  打开冲突文件，找到 `<<<<<<< HEAD` 标记。
    2.  手动编辑代码，删除标记，保留需要的内容。
    3.  标记为已解决：`git add src/main.rs` → `git commit`。
*   **💡 VSCode 提示**：冲突文件会高亮显示，并提供“接受当前更改”/“接受传入更改”按钮，点击即可快速解决。

### 7.7. `git stash` - 临时保存工作

*   **💡 使用场景**：代码写到一半，突然需要切换分支修复紧急 Bug，但当前改动还不想提交。
*   **基本用法**：
    1.  储藏当前工作：`git stash`
    2.  切换分支修 Bug：`git switch main`
    3.  切回原分支：`git switch feat/feature`
    4.  恢复工作：`git stash pop`
*   **常用命令**：
    *   查看所有 stash：`git stash list`
    *   恢复但不删除：`git stash apply stash@{0}`
    *   删除 stash：`git stash drop stash@{0}`

## 8. 代码"后悔药" - 撤销操作

### 8.1. `git revert`：安全地撤销

*   **作用**：创建一个新的提交，其内容与你想要撤销的提交完全相反。
*   **优点**：不修改项目历史，对于已经推送到远程的共享分支，这是唯一安全的撤销方式。
*   **用法**：`git revert 5d7a5b` (假设 `5d7a5b` 是一个错误的提交)。
    
*   Git Revert 示意图: 
    
    `Commit A` <- `Commit B` <- `Commit C` (错误提交) <- `Commit D` (Revert C 的提交)

### 8.2. `git reset`：强大的历史改写工具

*   **作用**：移动当前分支的 HEAD 指针到指定提交，并根据模式更新暂存区和工作区。**它会修改历史！**
*   **模式**：
    *   `--soft`：只移动 HEAD 指针。暂存区不变，工作区不变。
    *   `--mixed` (默认)：移动 HEAD，重置暂存区，工作区不变。
    *   `--hard`：移动 HEAD，重置暂存区，丢弃工作区。
*   **⚠️ 警告**：绝对不要 `reset` 已经被推送到远程共享分支的提交！

## 9. Commit Message 规范

### 9.1. 约定式提交（Conventional Commits）

*   **格式**：`<type>(<scope>): <subject>`
    *   空行
    *   `<body>`
    *   空行
    *   `<footer>`
*   **组成**：
    *   `type`：必填，提交类型。
    *   `scope`：可选，影响范围。
    *   `subject`：必填，简短描述。

### 9.2. 常用 Type 类型详解

*   `feat`：新功能 (如：`feat: 添加用户登录功能`)
*   `fix`：Bug 修复 (如：`fix: 修复登录验证失败问题`)
*   `docs`：文档 (如：`docs: 更新 API 使用文档`)
*   `style`：代码格式 (不影响代码功能，如：`style: 格式化代码缩进`)
*   `refactor`：重构 (既不是新功能也不是修复，如：`refactor: 重构用户认证模块`)
*   `perf`：性能优化 (如：`perf: 优化数据库查询速度`)
*   `test`：测试 (添加或修改测试代码，如：`test: 添加用户注册单元测试`)
*   `chore`：杂项 (构建过程、辅助工具的变动，如：`chore: 更新依赖包版本`)

### 9.3. 好的 vs 坏的 Commit Message

*   **❌ 反面教材**：
    *   `update` (太模糊)
    *   `fix bug` (修了什么 Bug?)
    *   `修改了一些代码` (完全没有信息量)
*   **✅ 正面示例**：
    *   `feat: 添加邮箱验证功能` (清楚说明了新增的功能)
    *   `fix: 修复用户头像上传失败` (具体说明修复了什么)
    *   `perf(api): 优化列表查询性能` (带 scope，更精确)

### 9.4. Commit Message 最佳实践

*   **编写规则**：
    1.  使用动词开头 (添加、修复...)。
    2.  使用现在时态 ("添加" 不是 "添加了")。
    3.  首字母小写 (`feat:` 而非 `Feat:`)。
    4.  不用句号结尾，保持简洁。
*   **💡 进阶技巧**：
    *   带 scope 更精确 (`feat(auth): 添加 JWT 认证`)。
    *   关联 Issue (`fix: 修复登录问题 #123`)。
    *   破坏性变更 (`feat!: 重构 API 接口 BREAKING CHANGE: 移除旧版`)。
*   **🎯 核心原则**：一个月后的你，或者你的队友，应该能通过 commit message 立刻明白这次改动做了什么。

## 10. 常见错误与解决方案

*   **不小心提交了密码**：
    *   **解决**：⚠️ 立即改密码! `git revert <commit>` (创建新提交来撤销)。
*   **提交信息写错了**：
    *   **解决**：`git commit --amend -m "正确信息"` (修改最后一次提交，还没 `push`)。
*   **`add` 错文件了**：
    *   **解决**：`git restore --staged 文件名` (从暂存区移除，但保留修改)。
*   **工作区文件改坏了**：
    *   **解决**：`git restore 文件名` (⚠️ 会丢失未提交的修改！)。
*   **💡 记住**：Git 很难把代码彻底删除，大胆尝试！遇到问题先 `git status`。

## 11. `git tag`：标记你的版本

*   **🏷️ 什么是 tag?**：为特定 commit 创建永久标记，通常用于版本发布。
    *   标记重要里程碑
    *   方便版本回溯
    *   清晰的版本历史
*   **💻 常用命令**：
    *   **轻量标签**：`git tag v1.0.0`
    *   **附注标签 (推荐)**：`git tag -a v1.0.0 -m "Release"`
    *   **推送标签**：`git push origin --tags`

## 12. 远程协作 · GitHub

### 12.1. 理解远程仓库 (Remote)

*   **☁️ 什么是远程仓库?**：托管在网络服务器上的你的项目版本。
    *   `origin` 是 Git 在你 `clone` 项目时创建的远程仓库默认名称。
    *   **常见的托管平台**：GitHub、GitLab、Gitee。
*   **⚙️ 常用命令**：
    *   `git remote -v`：查看所有远程仓库。
    *   `git remote add <name> <url>`：添加新的远程仓库。
    *   `git remote remove <name>`：移除远程仓库。

### 12.2. `git clone` - 克隆远程仓库

*   **📦 克隆仓库**：`git clone` 会完整复制远程仓库到本地。
    ```bash
    git clone https://github.com/username/repo.git
    ```
*   **✅ 自动完成**：
    *   下载所有文件和历史记录。
    *   设置 `origin` 远程仓库。
    *   切换到默认分支。
*   **🔐 HTTPS vs SSH**：
    *   **HTTPS (推荐新手)**：`https://github.com/user/repo.git` (简单易用，需要输入密码)。
    *   **SSH (更安全)**：`git@github.com:user/repo.git` (需要配置密钥，免密推送)。
*   **💡 提示**：两种方式功能完全相同。

### 12.3. `git fetch` vs `git pull`

*   **📥 `git fetch`**：只下载远程的更新，不合并到当前分支。
    ```bash
    git fetch origin
    ```
    *   **✅ 安全操作**：先看看远程有什么变化，再决定是否合并。
*   **⬇️ `git pull`**：下载并自动合并远程更新到当前分支。
    ```bash
    git pull origin main
    ```
    *   **⚠️ 注意**：可能会产生合并冲突。
*   **💡 推荐**：开始工作前先 `git pull`，避免冲突。

### 12.4. `git push` - 推送到远程

*   **⬆️ 基本用法**：将本地提交推送到远程仓库。
    ```bash
    git push origin main
    # 首次推送,设置上游
    git push -u origin main
    ```
*   **✅ 最佳实践**：完成功能后及时 `push`，与团队共享。
*   **⚠️ 常见问题**：
    *   **`push` 被拒绝**：原因可能是远程有新提交，先 `git pull` 再 `push`。
    *   **强制推送**：`git push -f` (❌ 危险! 会覆盖远程历史)。
*   **💡 工作流程**：`pull` → 修改代码 → `commit` → `push`。

## 13. 实用技巧与资源

### 13.1. 实战：完整的分支工作流

*   **阶段 1: 创建并开发**：
    ```bash
    git switch main && git pull
    git switch -c feat/error-handling
    git add .
    git commit -m "feat: 添加错误处理"
    ```
*   **阶段 2: 合并回主分支**：
    ```bash
    git switch main && git pull
    git merge feat/error-handling
    git push origin main
    git branch -d feat/error-handling
    ```

### 13.2. Git 工作流：GitHub Flow

*   **🔄 简单实用的团队协作模式**：`main` (生产环境) → 创建 `feature` 分支 → 开发 → Pull Request → Code Review → 合并。
*   **🔒 原则**：
    1.  `main` 永远可部署 (稳定版本)。
    2.  描述性分支名 (`feature/user-auth`)。
    3.  PR + Code Review 保证质量。

### 13.3. 什么是 Pull Request (PR)?

*   **🔄 Pull Request 是什么?**：一种让别人审查你的代码并合并到主分支的机制。
    *   你在自己的分支上完成了功能开发，想要把代码合并到主分支。但不是直接合并，而是先"请求"项目维护者审查你的代码，觉得 OK 了再合并。
*   **✅ 平台叫法**：GitHub 叫 Pull Request，GitLab 叫 Merge Request (意思一样)。

### 13.4. 为什么要使用 Pull Request?

*   **🛡️ 代码质量保障**：
    *   **代码审查 (Code Review)**：多双眼睛看代码，找出 Bug 和问题。
    *   **自动化测试**：CI/CD 自动运行测试，确保代码可用。
    *   **代码规范检查**：自动检查代码风格、格式是否统一。
*   **🤝 团队协作**：
    *   **讨论和交流**：在 PR 里讨论实现方案，分享想法。
    *   **知识传播**：新人通过 Review 学习，老手传授经验。
    *   **留下记录**：为什么这么改？讨论过程都有记录。
*   **💡 核心理念**：PR 不是找茬，而是互相帮助，共同提高代码质量！

### 13.5. 如何使用 Pull Request?

*   **🚀 完整流程**：创建分支 → 开发提交 → 推送远程 → 创建 PR → 代码审查 → 合并代码。
*   **📌 创建 PR 的步骤**：
    1.  在 GitHub 点击 "New pull request"。
    2.  选择源分支 → 目标分支。
    3.  填写标题和描述。
    4.  指定审查者 (Reviewers)。
    5.  点击 "Create pull request"。
*   **✅ 好的 PR 应该**：
    *   标题清晰：`feat: 添加登录功能`
    *   描述完整：改了什么、为什么
    *   一次一件事：不混杂多个功能
    *   保持小巧：改动不超过 300 行
    *   CI 通过：确保测试都过了

### 13.6. Git 配置优化

*   **命令别名**：让常用命令更简短。
    ```bash
    git config --global alias.st status
    git config --global alias.cm commit
    git config --global alias.lg "log --oneline"
    ```
    *   之后就可以用 `git st` 代替 `git status`。
*   **默认分支名**：新建仓库时使用 `main` 而不是 `master`。
    ```bash
    git config --global init.defaultBranch main
    ```
    *   **💡 提示**：GitHub 等平台现在都默认使用 `main`。

### 13.7. 学习资源推荐

*   **🎮 互动学习**：
    *   **Learn Git Branching**：可视化的交互式学习 (`learngitbranching.js.org`)。
    *   **Pro Git 书籍**：免费在线阅读，最权威 (`git-scm.com/book/zh`)。
*   **🛠️ 推荐工具**：
    *   **VSCode 内置 Git**：侧边栏完成所有操作。
    *   **GitHub Desktop**：图形界面，不用记命令。
    *   **SourceTree**：功能强大的图形工具。
*   你总会找到一个让你舒适的 Git 使用方法：命令行、图形界面、IDE 插件...选择最适合你的!

## 14. Git 是怎么工作的？

### Git 的三种核心对象

*   **Blob**：
    *   存储文件内容。
    *   用 SHA-1 标识。
*   **Tree**：
    *   存储目录结构。
    *   包含 `blob` 和子 `tree`。
*   **Commit**：
    *   指向根 `tree`。
    *   包含作者、时间、消息。
*   **关键**：相同内容只存储一次，非常高效！

## 15. 总结

*   **记住这些就够了**：
    1.  **基本流程**：`git add` → `git commit` → `git push`。
    2.  **查看状态**：随时 `git status`。
    3.  **用好分支**：开发新功能时创建新分支。
    4.  **团队协作**：先 `pull`，后 `push`。
*   **Suggestions**：
    *   **多练习**：创建测试项目，试试所有命令。
    *   **用 VSCode**：图形界面更直观。
    *   **看文档**：遇到问题先搜索。

---

恭喜你迈出了第一步！Git 的学习是持续的过程。今天学的这些，足够你完成大部分日常工作了。

*   **📝 掌握基础**：`add`/`commit`/`push`
*   **🌿 理解分支**：创建/合并/切换
*   **👥 团队协作**：`pull`/`push`/冲突

🙋‍♂️ Q & A: 有任何问题都可以提问！关于 Git 的任何问题都欢迎交流。