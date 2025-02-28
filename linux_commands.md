**一、 文件和目录操作类**

- **`ls` (list directory contents)**：列出目录内容。
  
  - `ls`: 列出当前目录的文件和目录。
  - `ls -l`: 详细列表格式，显示权限、大小、修改时间等信息。
  - `ls -a`: 显示所有文件，包括隐藏文件（以 `.` 开头的文件）。
  - `ls -h`: 以人类可读的格式显示文件大小 (例如 KB, MB, GB)。
  - `ls -t`: 按修改时间排序（最新的在前面）。
  - `ls -r`: 反向排序。
  - `ls -R`: 递归列出目录及其子目录的内容。
  - `ls /path/to/directory`: 列出指定目录的内容。

- **`cd` (change directory)**：切换目录。
  
  - `cd directory_name`: 进入指定目录。
  - `cd ..`: 返回上一级目录。
  - `cd ~`: 回到用户家目录。
  - `cd /`: 切换到根目录。
  - `cd -`: 返回上一次所在的目录。

- **`pwd` (print working directory)**：显示当前工作目录的路径。
  
  - `pwd`: 直接运行即可显示当前所在目录的完整路径。

- **`mkdir` (make directory)**：创建目录。
  
  - `mkdir directory_name`: 创建一个名为 `directory_name` 的目录。
  - `mkdir -p directory1/directory2/directory3`: 递归创建多级目录，即使父目录不存在也会自动创建。

- **`rmdir` (remove directory)**：删除空目录。
  
  - `rmdir directory_name`: 删除一个名为 `directory_name` 的空目录。 **注意：只能删除空目录。**

- **`rm` (remove files or directories)**：删除文件或目录。
  
  - `rm file1 file2 ...`: 删除一个或多个文件。
  - `rm -r directory_name`: 递归删除目录及其所有内容（包括子目录和文件）。 **非常危险，请谨慎使用！**
  - `rm -f file_name`: 强制删除文件，即使文件是只读的或没有写权限也会尝试删除。
  - `rm -i file_name`: 删除前交互式提示确认。

- **`cp` (copy files and directories)**：复制文件和目录。
  
  - `cp source_file destination_file`: 复制文件。
  - `cp source_file directory`: 将文件复制到目录中。
  - `cp -r source_directory destination_directory`: 递归复制目录及其所有内容。
  - `cp -p source_file destination_file`: 保留源文件的属性（时间戳、权限等）进行复制。

- **`mv` (move files and directories)**：移动文件和目录，或重命名文件和目录。
  
  - `mv source_file destination_file`: 移动文件 (如果目标路径与源路径不同，则相当于移动；如果目标路径与源路径相同，但文件名不同，则相当于重命名文件)。
  - `mv source_file directory`: 将文件移动到目录中。
  - `mv source_directory destination_directory`: 移动目录。

- **`touch` (change file timestamps)**：创建空文件或更新文件的时间戳。
  
  - `touch file_name`: 如果文件不存在，则创建一个空文件；如果文件存在，则更新文件的访问时间和修改时间为当前时间。

- **`cat` (concatenate and display files)**：连接并显示文件内容。
  
  - `cat file_name`: 显示文件内容到标准输出 (通常是终端)。
  - `cat file1 file2 > combined_file`: 将 `file1` 和 `file2` 的内容合并并写入到 `combined_file` 中。

- **`more` 和 `less` (file pager)**：分页显示文件内容。
  
  - `more file_name`: 分页显示文件内容，按空格键翻页，按 `q` 键退出。
  - `less file_name`: 更强大的分页显示工具，支持向前和向后翻页、搜索等功能。

- **`head` (output the beginning of files)**：显示文件开头部分内容。
  
  - `head file_name`: 显示文件的前 10 行。
  - `head -n N file_name`: 显示文件的前 N 行。

- **`tail` (output the end of files)**：显示文件结尾部分内容。
  
  - `tail file_name`: 显示文件的后 10 行。
  - `tail -n N file_name`: 显示文件的后 N 行。
  - `tail -f file_name`: 实时监控文件末尾的追加内容 (常用于查看日志文件)。

- **`find` (search for files in a directory hierarchy)**：在目录结构中查找文件。
  
  - `find . -name "filename"`: 在当前目录及其子目录中查找名为 "filename" 的文件。
  - `find /path/to/search -type d -name "directory_name"`: 在指定路径下查找类型为目录且名为 "directory_name" 的目录。
  - `find . -size +10M`: 查找当前目录下大小超过 10MB 的文件。
  - `find . -mtime -7`: 查找最近 7 天内修改过的文件。
  - `find . -exec command {} \;`: 对找到的文件执行指定命令，`{}` 会被替换为找到的文件名，`\;` 表示命令结束。

- **`chmod` (change file mode bits)**：修改文件或目录的权限。
  
  - `chmod +x script.sh`: 给 `script.sh` 文件添加执行权限。
  - `chmod 755 file_name`: 设置文件权限为 755 (所有者读写执行，用户组和其他用户读和执行)。
  - `chmod -R 777 directory_name`: 递归设置目录及其所有内容的权限为 777 (所有用户读写执行)。 **非常宽松的权限，通常不推荐。**

- **`chown` (change file owner and group)**：修改文件或目录的所有者和所属组。
  
  - `chown user file_name`: 将 `file_name` 的所有者更改为 `user`。
  - `chown user:group file_name`: 将 `file_name` 的所有者更改为 `user`，所属组更改为 `group`。
  - `chown -R user:group directory_name`: 递归更改目录及其所有内容的所有者和所属组。

**二、 文本处理类**

- **`grep` (global regular expression print)**：在文件中搜索匹配模式的行，并打印出来。
  
  - `grep "pattern" file_name`: 在 `file_name` 中搜索包含 "pattern" 的行并打印。
  - `grep -i "pattern" file_name`: 忽略大小写进行搜索。
  - `grep -v "pattern" file_name`: 打印不包含 "pattern" 的行 (反向匹配)。
  - `grep -r "pattern" directory`: 递归在目录及其子目录下的所有文件中搜索。
  - `grep -n "pattern" file_name`: 显示匹配行的行号。
  - `grep -w "word" file_name`: 只匹配完整的单词 "word"。
  - `grep -E "pattern1|pattern2" file_name`: 使用扩展正则表达式，匹配 "pattern1" 或 "pattern2"。

- **`sed` (stream editor)**：流编辑器，用于对文本进行编辑和转换。 (前面已经详细解释过)
  
  - `sed 's/old_text/new_text/g' file_name`: 将文件中所有 "old_text" 替换为 "new_text"。
  - `sed '/pattern/d' file_name`: 删除包含 "pattern" 的行。
  - `sed -n '/pattern/p' file_name`: 只打印包含 "pattern" 的行 (类似于 `grep`，但 `sed` 更强大)。

- **`awk` (pattern scanning and processing language)**：强大的文本处理工具，可以进行复杂的文本分析和数据提取。
  
  - `awk '{print $1}' file_name`: 打印每行的第一个字段 (默认字段分隔符是空格或制表符)。
  - `awk -F',' '{print $2}' file_name`: 使用逗号 `,` 作为字段分隔符，打印每行的第二个字段。
  - `awk '/pattern/{print $0}' file_name`: 打印包含 "pattern" 的整行。
  - `awk 'BEGIN{sum=0} {sum+=$1} END{print sum}' file_name`: 计算文件中第一列数字的总和。

- **`sort` (sort lines of text files)**：对文本文件行进行排序。
  
  - `sort file_name`: 按字母顺序排序文件内容并输出。
  - `sort -n file_name`: 按数值大小排序 (适用于数字列)。
  - `sort -r file_name`: 反向排序。
  - `sort -k 2 file_name`: 按第二个字段排序。
  - `sort -u file_name`: 去除重复行 (unique)。

- **`uniq` (report or omit repeated lines)**：去除或报告文件中的重复行。
  
  - `uniq file_name`: 去除相邻的重复行并输出。 **注意： `uniq` 只能去除相邻的重复行，所以通常需要先 `sort` 再 `uniq`。**
  - `uniq -c file_name`: 在每行前面显示重复行的计数。
  - `uniq -d file_name`: 只显示重复的行 (每个重复组只显示一行)。

- **`cut` (remove sections from each line of files)**：从每行中提取指定字段。
  
  - `cut -d',' -f1,3 file_name`: 使用逗号 `,` 作为分隔符，提取每行的第 1 和第 3 个字段。
  - `cut -c 1-5 file_name`: 提取每行的第 1 到第 5 个字符。

- **`paste` (merge lines of files)**：合并多个文件的行。
  
  - `paste file1 file2`: 将 `file1` 和 `file2` 的对应行合并，默认用制表符分隔。
  - `paste -d',' file1 file2`: 使用逗号 `,` 作为分隔符合并行。

- **`wc` (word, line, character, and byte count)**：统计文件中的字数、行数、字符数和字节数。
  
  - `wc file_name`: 显示文件的行数、字数和字节数。
  - `wc -l file_name`: 只显示行数 (lines)。
  - `wc -w file_name`: 只显示字数 (words)。
  - `wc -c file_name`: 只显示字节数 (bytes)。
  - `wc -m file_name`: 只显示字符数 (characters)。

**三、 进程管理类**

- **`ps` (process status)**：显示当前进程的状态。
  
  - `ps`: 显示当前用户正在运行的进程。
  - `ps aux`: 显示所有用户的详细进程信息 (包括 CPU 和内存占用等)。
  - `ps -ef`: 另一种显示所有进程的格式。
  - `ps aux | grep "process_name"`: 查找包含 "process_name" 的进程。

- **`top` (display Linux processes)**：实时动态地显示系统进程信息，包括 CPU、内存使用情况等。
  
  - `top`: 运行 `top` 命令，进入交互式界面，实时查看进程信息。 按 `q` 键退出。

- **`htop` (interactive process viewer)**：更友好的交互式进程查看器，功能更强大，界面更美观 (通常需要单独安装)。
  
  - `htop`: 运行 `htop` 命令，进入交互式界面。

- **`kill` (terminate a process)**：发送信号给进程，通常用于终止进程。
  
  - `kill PID`: 向进程 ID 为 `PID` 的进程发送 `SIGTERM` 信号 (正常终止信号)。
  - `kill -9 PID`: 向进程 ID 为 `PID` 的进程发送 `SIGKILL` 信号 (强制终止信号，立即杀死进程，不给进程清理资源的机会)。 **尽量避免使用 `-9`，除非进程无法正常终止。**
  - `killall process_name`: 杀死所有名为 `process_name` 的进程。

- **`bg` (background jobs)**：将当前挂起的作业 (job) 放到后台运行。
  
  - `bg`: 在终端中使用 `Ctrl+Z` 挂起一个前台运行的进程后，可以使用 `bg` 命令将其放到后台继续运行。

- **`fg` (foreground jobs)**：将后台作业放到前台运行。
  
  - `fg %job_number`: 将作业编号为 `job_number` 的后台作业放到前台运行。 可以使用 `jobs` 命令查看后台作业及其编号。

- **`jobs` (display status of jobs in the current session)**：显示当前会话的作业列表 (包括前台和后台运行的进程)。
  
  - `jobs`: 显示当前会话的作业列表。

- **`nohup` (run a command immune to hangups, with output to a non-tty)**：在后台运行命令，使其不受终端关闭或断线的影响，并将输出重定向到 `nohup.out` 文件 (默认)。
  
  - `nohup command &`: 在后台运行 `command`，并将标准输出和标准错误输出重定向到 `nohup.out` 文件。 `&` 符号表示将命令放到后台运行。

- **`screen` 和 `tmux` (terminal multiplexer)**：终端复用器，允许在一个终端窗口中创建和管理多个会话，即使终端关闭或断线，会话仍然保持运行。 非常适合长时间运行的任务。
  
  - `screen`: 运行 `screen` 命令，创建一个新的 screen 会话。 在 screen 会话中可以使用 `Ctrl+a c` 创建新窗口，`Ctrl+a n` 切换到下一个窗口， `Ctrl+a p` 切换到上一个窗口， `Ctrl+a d` 分离 (detach) 会话 (会话在后台继续运行)， `screen -r` 或 `screen -r session_name` 重新连接 (reattach) 到已分离的会话。
  - `tmux`: 类似 `screen` 的终端复用器，功能更强大，配置更灵活。 用法类似，例如 `tmux new-session -s session_name` 创建新会话， `tmux attach-session -t session_name` 连接到会话， `Ctrl+b d` 分离会话， `Ctrl+b c` 创建新窗口， `Ctrl+b n` 下一个窗口， `Ctrl+b p` 上一个窗口。

**四、 系统信息和网络类**

- **`uname` (print system information)**：显示系统信息。
  
  - `uname -a`: 显示所有系统信息 (内核名称、主机名、内核版本、硬件架构、操作系统等)。
  - `uname -s`: 显示内核名称。
  - `uname -r`: 显示内核版本。
  - `uname -m`: 显示硬件架构。
  - `uname -o`: 显示操作系统名称。

- **`hostname` (show or set the system's host name)**：显示或设置系统的主机名。
  
  - `hostname`: 显示当前主机名。
  - `hostname new_hostname`: 临时设置主机名为 `new_hostname` (重启后失效)。

- **`date` (print or set the system date and time)**：显示或设置系统日期和时间。
  
  - `date`: 显示当前日期和时间。
  - `date "+%Y-%m-%d %H:%M:%S"`: 按指定格式显示日期和时间 (例如 `YYYY-MM-DD HH:MM:SS`)。
  - `date -s "YYYY-MM-DD HH:MM:SS"`: 设置系统日期和时间 (需要 root 权限)。

- **`df` (report file system disk space usage)**：显示磁盘空间使用情况。
  
  - `df -h`: 以人类可读的格式显示磁盘空间使用情况。
  - `df -T`: 显示文件系统类型。

- **`du` (estimate file space usage)**：估计文件和目录的磁盘空间使用情况。
  
  - `du -h directory_name`: 以人类可读的格式显示目录 `directory_name` 的磁盘空间使用情况。
  - `du -sh directory_name`: 显示目录 `directory_name` 的总大小。

- **`free` (display amount of free and used memory in the system)**：显示系统内存使用情况。
  
  - `free -h`: 以人类可读的格式显示内存使用情况 (包括物理内存和交换空间)。

- **`ifconfig` 或 `ip addr` (configure a network interface)**：显示和配置网络接口信息。
  
  - `ifconfig`: 显示网络接口信息 (过时命令，部分系统可能不再默认安装，建议使用 `ip addr`)。
  - `ip addr`: 显示网络接口信息 (更现代的命令)。
  - `ip addr show interface_name`: 显示指定网络接口的信息。

- **`ping` (send ICMP ECHO_REQUEST packets to network hosts)**：测试网络连接是否畅通。
  
  - `ping hostname_or_IP`: 向指定主机名或 IP 地址发送 ping 包。
  - `ping -c 5 hostname_or_IP`: 只发送 5 个 ping 包。

- **`wget` (the non-interactive network downloader)**：非交互式的网络下载工具。
  
  - `wget URL`: 下载指定 URL 的文件到当前目录。
  - `wget -O filename URL`: 下载文件并保存为指定文件名。
  - `wget -c URL`: 断点续传下载。

- **`curl` (transfer a URL)**：功能强大的网络请求工具，可以发送各种 HTTP 请求，获取网页内容、下载文件等。
  
  - `curl URL`: 获取指定 URL 的内容并输出到标准输出 (常用于查看网页源代码)。
  - `curl -O URL`: 下载指定 URL 的文件到当前目录，并使用 URL 中的文件名保存。
  - `curl -o filename URL`: 下载文件并保存为指定文件名。

- **`ssh` (OpenSSH SSH client (remote login program))**：远程登录到其他 Linux/Unix 系统。
  
  - `ssh user@hostname_or_IP`: 使用用户名 `user` 远程登录到指定主机。

- **`scp` (secure copy)**：安全地在本地系统和远程系统之间复制文件。
  
  - `scp local_file user@hostname_or_IP:remote_directory`: 将本地文件复制到远程系统的指定目录。
  - `scp user@hostname_or_IP:remote_file local_directory`: 从远程系统复制文件到本地系统的指定目录。

**五、 脚本控制流命令**

- **`echo` (display a line of text)**：输出文本到终端。(前面已经多次提到)
  
  - `echo "Hello, world!"`: 输出 "Hello, world!"。
  - `echo $variable`: 输出变量 `variable` 的值。
  - `echo -n "Text without newline"`: 输出文本但不换行。

- **`printf` (formatted output)**：格式化输出文本，功能更强大，可以像 C 语言的 `printf` 一样进行格式化输出。
  
  - `printf "Name: %s, Age: %d\n" "John" 30`: 格式化输出姓名和年龄。

- **`exit` (cause the shell to exit)**：退出脚本或 shell 会话。
  
  - `exit 0`: 正常退出，返回状态码 0 (通常表示成功)。
  - `exit 1`: 非正常退出，返回状态码 1 (或其他非零值，通常表示失败或错误)。

- **`if`, `then`, `elif`, `else`, `fi` (conditional execution)**：条件判断语句。
  
  BASH
  
  `if [ condition ]; then   # 条件为真时执行的代码 elif [ another_condition ]; then   # 另一个条件为真时执行的代码 else   # 所有条件都不为真时执行的代码 fi`
  
  - `condition` 通常是使用 `test` 命令或 `[]` 进行的条件表达式，例如 `[ -f file.txt ]` (判断文件是否存在), `[ "$VAR" -eq 10 ]` (判断变量 `VAR` 是否等于 10), `[ -d directory ]` (判断是否是目录) 等。

- **`case`, `esac` (conditional execution)**：多分支条件判断语句，类似于其他语言的 `switch` 语句。
  
  BASH
  
  `case "$variable" in   pattern1)     # 匹配 pattern1 时执行的代码     ;;   pattern2)     # 匹配 pattern2 时执行的代码     ;;   *)     # 默认情况，如果都不匹配时执行的代码     ;; esac`
  
  Show all (12)

- **`for`, `in`, `do`, `done` (looping)**： `for` 循环，用于遍历列表或范围。 (前面在 `sed` 命令解释中已提到)
  
  BASH
  
  `for variable in item1 item2 ... itemN do   # 循环体，对每个 item 执行的代码 done`
  
  - `for i in {1..10}`; `do echo $i; done`: 循环 10 次，输出 1 到 10 的数字。
  - `for file in *.txt`; `do echo "Processing $file"; done`: 循环处理当前目录下的所有 `.txt` 文件。

- **`while`, `do`, `done` (looping)**： `while` 循环，当条件为真时重复执行循环体。
  
  BASH
  
  `while [ condition ] do   # 循环体，条件为真时执行的代码 done`

- **`until`, `do`, `done` (looping)**： `until` 循环，当条件为假时重复执行循环体，直到条件为真才停止。
  
  BASH
  
  `until [ condition ] do   # 循环体，条件为假时执行的代码 done`

- **`break` (exit from loop)**：在循环体内部使用 `break` 命令可以立即跳出当前循环。

- **`continue` (continue to next iteration of loop)**：在循环体内部使用 `continue` 命令可以跳过当前迭代的剩余代码，直接进入下一次迭代。

- **`function`, `()` (define a function)**：定义函数，用于封装可重用的代码块。
  
  BASH
  
  `function function_name() {   # 函数体，要执行的代码   return value  # 可选的返回值 } # 或者更简洁的写法 (推荐) function_name() {   # 函数体   return value } # 调用函数 function_name result=$?  # 获取函数的返回值 (exit status)`
  
  Show all (15)

- **`return` (exit from a function)**：在函数内部使用 `return` 命令可以从函数中返回，并可以指定返回值 (exit status)。

**六、 变量和运算符**

- **变量赋值:** `variable_name=value` (注意等号两边不能有空格)。

- **变量引用:** `$variable_name` 或 `${variable_name}` (花括号在某些情况下是必要的，例如变量名与其他字符紧邻时)。

- **环境变量:** 系统级别的变量，例如 `PATH`, `HOME`, `USER` 等。 可以使用 `export variable_name=value` 将自定义变量设置为环境变量。

- **算术运算符:** `+`, `-`, `*`, `/`, `%` (加、减、乘、除、取模)。 通常需要使用 `expr` 命令或 `$(())` 或 `$[]` 进行算术运算。
  
  - `result=$(( 10 + 5 ))`
  - `result=$[ 20 - 3 ]`
  - `result=$(expr 15 \* 2)` (注意 `*` 需要转义为 `\*`，因为 `*` 在 shell 中是通配符)。

- **比较运算符:**
  
  - **数值比较:** `-eq` (等于), `-ne` (不等于), `-gt` (大于), `-ge` (大于等于), `-lt` (小于), `-le` (小于等于)。 例如 `[ "$COUNT" -gt 10 ]`
  - **字符串比较:** `==` 或 `=` (等于), `!=` (不等于), `<` (小于), `>` (大于)。 例如 `[ "$STR1" == "hello" ]` 或 `[[ "$STR1" == "hello" ]]` (推荐使用 `[[ ... ]]`，更强大且不容易出错)。
  - **文件测试:** `-f` (文件存在且是普通文件), `-d` (目录存在), `-e` (文件或目录存在), `-r` (可读), `-w` (可写), `-x` (可执行) 等。 例如 `[ -f file.txt ]`

- **逻辑运算符:** `&&` (逻辑与 AND), `||` (逻辑或 OR), `!` (逻辑非 NOT)。
  
  - `[ condition1 ] && [ condition2 ]` (条件 1 和条件 2 都为真时才为真)
  - `[ condition1 ] || [ condition2 ]` (条件 1 或条件 2 至少有一个为真时就为真)
  - `! [ condition ]` (条件为假时才为真)

**七、 其他常用命令**

- **`echo` (display a line of text)**： (再次强调，因为太常用了)

- **`sleep` (delay for a specified amount of time)**：暂停脚本执行一段时间。
  
  - `sleep 5`: 暂停 5 秒。
  - `sleep 2m`: 暂停 2 分钟。
  - `sleep 1h`: 暂停 1 小时。

- **`date` (print or set the system date and time)**： (也常用，特别是脚本需要记录时间戳时)

- **`history` (display or manipulate the history list)**：显示命令历史记录。
  
  - `history`: 显示最近执行的命令历史。
  - `history | grep "command"`: 搜索命令历史记录中包含 "command" 的命令。
  - `!N`: 执行历史记录中第 N 条命令 (例如 `!100` 执行第 100 条命令)。
  - `!!`: 执行上一条命令。
  - `!string`: 执行最近一条以 "string" 开头的命令。

- **`alias` (define or display aliases)**：定义或显示命令别名，可以为常用命令设置简短的别名。
  
  - `alias la='ls -la'`: 定义别名 `la` 为 `ls -la` 命令。
  - `alias`: 显示当前已定义的别名。
  - `unalias alias_name`: 取消别名。

- **`unalias` (remove alias definitions)**：取消命令别名。

- **`source` 或 `.` (run commands from a file in the current shell environment)**：执行脚本文件中的命令，并在当前 shell 环境中生效。 常用于加载配置文件或函数库。
  
  - `source script.sh` 或 `. script.sh`: 执行 `script.sh` 文件中的命令。

- **`type` (describe a command)**：显示命令的类型 (例如是 shell 内置命令、外部命令、别名、函数等)。
  
  - `type ls`: 显示 `ls` 命令的类型。

- **`man` (an interface to the system reference manuals)**：查看命令的帮助手册 (manual pages)。
  
  - `man command_name`: 查看 `command_name` 命令的 man page。 按 `q` 键退出。
  - `man -k keyword`: 搜索 man page 中包含 `keyword` 的命令。

- **`info` (read Info documents)**：查看 GNU Info 格式的文档 (比 man page 更详细，但不是所有命令都有 info 文档)。
  
  - `info command_name`: 查看 `command_name` 命令的 info 文档。

- **`help` (display helpful information about builtin commands)**：查看 shell 内置命令的帮助信息。
  
  - `help cd`: 查看 `cd` 命令的帮助信息。
