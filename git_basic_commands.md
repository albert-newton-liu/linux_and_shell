**一、 基本配置和设置 (Setup & Configuration)**

- **`git config`**: 配置 Git 的设置，例如用户名、邮箱、编辑器等。
  - **`git config --global user.name "Your Name"`**: 设置全局用户名。
  - **`git config --global user.email "your_email@example.com"`**: 设置全局邮箱地址。
  - **`git config --global core.editor "vim"`**: 设置全局默认文本编辑器为 Vim (你可以替换为 `nano`, `code`, etc.)。
  - **`git config --list`**: 列出当前的 Git 配置信息。
  - **`git config --global -e`**: 编辑全局 Git 配置文件。

**二、 获取和创建项目 (Getting & Creating Projects)**

- **`git init`**: 在当前目录初始化一个新的 Git 仓库。
  
  - **`git init`**: 在当前目录创建一个新的 `.git` 子目录，开始跟踪版本控制。

- **`git clone <repository_url>`**: 克隆一个远程仓库到本地。
  
  - **`git clone https://github.com/username/repository.git`**: 克隆 GitHub 上的一个仓库到当前目录。
  - **`git clone <repository_url> <directory_name>`**: 克隆仓库到指定的目录名下。

**三、 基本工作流程 (Basic Workflow - Working with Changes)**

- **`git status`**: 查看工作区和暂存区的状态，显示哪些文件被修改、暂存或未跟踪。
  
  - **`git status`**: 查看当前分支的状态，哪些文件有改动。
  - **`git status -s`** 或 **`git status --short`**: 以简洁的格式显示状态。

- **`git add <file>`** 或 **`git add <directory>`** 或 **`git add .`**: 将文件或目录添加到暂存区 (Staging Area)。
  
  - **`git add file.txt`**: 暂存 `file.txt` 文件的修改。
  - **`git add src/`**: 暂存 `src/` 目录下的所有文件和目录的修改。
  - **`git add .`**: 暂存当前目录及其子目录中所有已修改和新增的文件。

- **`git commit -m "<commit message>"`**: 提交暂存区的文件到本地仓库，创建一个新的提交记录。
  
  - **`git commit -m "Fix: Resolve issue with user login"`**: 提交暂存区内容，并添加提交信息 "Fix: Resolve issue with user login"。
  - **`git commit -am "<commit message>"`**: 跳过暂存区，直接提交所有已跟踪的修改文件 (Add and Commit in one step)。 **谨慎使用，确保你清楚提交的内容。**
  - **`git commit --amend`**: 修改上一次提交 (可以修改提交信息或添加新的暂存文件到上一次提交中)。

- **`git rm <file>`**: 从工作区和暂存区删除文件 (并且会记录删除操作到下次提交)。
  
  - **`git rm unwanted_file.txt`**: 删除 `unwanted_file.txt` 文件，并暂存删除操作。
  - **`git rm --cached <file>`**: 只从暂存区删除文件，保留工作区文件 (取消跟踪文件)。

- **`git mv <old_file> <new_file>`**: 移动或重命名文件 (并且会记录移动/重命名操作到下次提交)。
  
  - **`git mv old_name.txt new_name.txt`**: 将 `old_name.txt` 重命名为 `new_name.txt`，并暂存重命名操作。
  - **`git mv file.txt src/`**: 将 `file.txt` 移动到 `src/` 目录下，并暂存移动操作。

**四、 分支与合并 (Branching & Merging)**

- **`git branch`**: 查看、创建、删除分支。
  
  - **`git branch`**: 列出所有本地分支，当前分支会用 `*` 标记。
  - **`git branch -r`**: 列出所有远程分支。
  - **`git branch -a`**: 列出所有本地和远程分支。
  - **`git branch <branch_name>`**: 创建一个新的本地分支 `branch_name`。
  - **`git branch -d <branch_name>`**: 删除本地分支 `branch_name` (如果分支已合并，否则需要使用 `-D` 强制删除)。
  - **`git branch -D <branch_name>`**: 强制删除本地分支 `branch_name` (即使分支未合并)。

- **`git checkout <branch_name>`**: 切换到指定分支。
  
  - **`git checkout main`**: 切换到 `main` 分支。
  - **`git checkout -b <new_branch_name>`**: 创建并切换到一个新的分支 `new_branch_name` (相当于 `git branch <new_branch_name>` followed by `git checkout <new_branch_name>`).

- **`git merge <branch_name>`**: 将指定分支 `branch_name` 合并到当前分支。
  
  - **`git merge feature-branch`**: 将 `feature-branch` 分支合并到当前分支。
  - **合并冲突 (Merge Conflicts):** 合并时如果遇到冲突，Git 会提示，你需要手动解决冲突文件，然后 `git add` 解决冲突后的文件，最后 `git commit` 完成合并。

- **`git branch --merged`**: 列出已经合并到当前分支的分支。

- **`git branch --no-merged`**: 列出尚未合并到当前分支的分支。

**五、 远程仓库操作 (Remote Repositories)**

- **`git remote`**: 管理远程仓库连接。
  
  - **`git remote -v`**: 列出当前配置的远程仓库连接，并显示 URL。
  - **`git remote add <remote_name> <repository_url>`**: 添加一个新的远程仓库连接，命名为 `remote_name` (例如 `origin`)，URL 为 `repository_url`。
  - **`git remote rename <old_name> <new_name>`**: 重命名远程仓库连接名称。
  - **`git remote remove <remote_name>`**: 删除远程仓库连接。

- **`git fetch <remote_name>`**: 从远程仓库 `remote_name` 下载最新的分支和提交记录，但不合并到本地分支。
  
  - **`git fetch origin`**: 从名为 `origin` 的远程仓库获取最新数据。

- **`git pull <remote_name> <branch_name>`**: 从远程仓库 `remote_name` 的 `branch_name` 分支拉取最新代码并合并到当前本地分支 (相当于 `git fetch` + `git merge FETCH_HEAD`)。
  
  - **`git pull origin main`**: 从 `origin` 远程仓库的 `main` 分支拉取代码并合并到当前本地分支。
  - **通常在开始工作前先 `git pull` 同步远程仓库的最新更改。**

- **`git push <remote_name> <branch_name>`**: 将本地分支 `branch_name` 的提交推送到远程仓库 `remote_name`。
  
  - **`git push origin main`**: 将本地 `main` 分支推送到 `origin` 远程仓库的 `main` 分支。
  - **`git push origin <branch_name>`**: 如果远程仓库没有同名分支，会自动创建远程分支。
  - **`git push origin --delete <branch_name>`**: 删除远程仓库的 `branch_name` 分支。

**六、 查看提交历史和比较 (Inspecting & Comparing)**

- **`git log`**: 查看提交历史记录。
  
  - **`git log`**: 显示详细的提交历史，包括提交 ID、作者、日期、提交信息等。
  - **`git log --oneline`**: 以简洁的单行格式显示提交历史。
  - **`git log --graph`**: 以图形化方式显示分支合并历史。
  - **`git log --decorate`**: 显示分支和标签信息。
  - **`git log -p`**: 显示每次提交的详细 diff (文件变更内容)。
  - **`git log --author="Author Name"`**: 只显示指定作者的提交记录。
  - **`git log --grep="keyword"`**: 只显示提交信息中包含关键词 "keyword" 的提交记录。

- **`git diff`**: 比较工作区、暂存区和仓库之间的差异。
  
  - **`git diff`**: 比较工作区和暂存区的差异 (未暂存的修改)。
  - **`git diff --staged`** 或 **`git diff --cached`**: 比较暂存区和最后一次提交 (已暂存的修改)。
  - **`git diff <commit1> <commit2>`**: 比较两个提交之间的差异。
  - **`git diff <branch1> <branch2>`**: 比较两个分支之间的差异。
  - **`git diff HEAD`**: 比较工作区和最后一次提交的差异。

- **`git show <commit>`**: 显示指定提交的详细信息，包括提交信息和文件变更内容 (diff)。
  
  - **`git show HEAD`**: 显示最后一次提交的详细信息。
  - **`git show <commit_id>`**: 显示指定提交 ID 的提交信息。

**七、 撤销和回滚 (Undoing Changes)**

- **`git restore <file>`**: 撤销工作区的修改，恢复文件到暂存区或最后一次提交的版本。
  
  - **`git restore file.txt`**: 撤销工作区对 `file.txt` 的修改，恢复到暂存区版本 (如果暂存区有该文件，否则恢复到最后一次提交的版本)。
  - **`git restore --staged <file>`**: 从暂存区移除文件，但保留工作区的文件 (Unstage file)。

- **`git reset`**: 重置暂存区和分支指针到指定的提交或状态。 **非常强大且 potentially dangerous，使用需谨慎。**
  
  - **`git reset --soft <commit>`**: 软重置。将分支指针回退到 `<commit>`，但保留工作区和暂存区的修改 (修改会变成未暂存状态)。 提交历史回退，但代码修改还在。
  - **`git reset --mixed <commit>`** (默认，可以省略 `--mixed`): 混合重置。将分支指针和暂存区都回退到 `<commit>`，但保留工作区的修改 (修改会变成未暂存状态)。 暂存区和提交历史回退，代码修改还在，但未暂存。
  - **`git reset --hard <commit>`**: 硬重置。将分支指针、暂存区和工作区都回退到 `<commit>`。 **会彻底丢失 `<commit>` 之后的所有提交和工作区修改，非常危险！谨慎使用！**

- **`git revert <commit>`**: 创建一个新的提交，来撤销指定提交 `<commit>` 的更改。 **安全撤销方式，不会修改历史，推荐使用。**
  
  - **`git revert HEAD`**: 撤销最近一次提交的更改，并创建一个新的提交记录来记录撤销操作。

**八、 标签 (Tags)**

- **`git tag`**: 管理标签，用于标记版本发布点 (例如 v1.0, v2.5)。
  - **`git tag`**: 列出所有标签。
  - **`git tag -l "v1.*"`**: 列出所有以 "v1." 开头的标签。
  - **`git tag -a <tag_name> -m "<tag message>"`**: 创建一个带注释的标签 `tag_name`，并添加标签信息 "tag message"。
  - **`git tag <tag_name>`**: 创建一个轻量级标签 `tag_name` (没有注释)。
  - **`git tag -d <tag_name>`**: 删除本地标签 `tag_name`。
  - **`git push origin --tags`**: 将本地标签推送到远程仓库。
  - **`git push origin --delete tag <tag_name>`**: 删除远程仓库的标签 `tag_name`。

**九、 储藏 (Stashing)**

- **`git stash`**: 储藏当前工作区的未提交更改，以便稍后恢复。 用于临时保存工作进度，切换分支或处理紧急任务。
  - **`git stash`** 或 **`git stash save "<stash message>"`**: 储藏当前更改，并可选地添加储藏信息。
  - **`git stash list`**: 列出所有储藏的记录。
  - **`git stash apply`**: 恢复最近一次储藏的更改到工作区 (但不删除储藏记录)。
  - **`git stash apply stash@{n}`**: 恢复指定的储藏记录 (例如 `stash@{0}` 表示最近一次储藏)。
  - **`git stash pop`**: 恢复最近一次储藏的更改到工作区，并删除该储藏记录 (相当于 `git stash apply` followed by `git stash drop`)。
  - **`git stash drop stash@{n}`**: 删除指定的储藏记录。
  - **`git stash clear`**: 删除所有储藏记录。
