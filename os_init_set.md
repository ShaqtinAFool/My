<!-- MarkdownTOC -->

- MAC
- MAC\(VM\)
- Linux\(Host Ubuntu\)
- Linux\(VM CentOS\)
- Windows
- Windows\(TTFRI\)
- Chrome
- Sublime
- Notepad++
- Brackets
- Unix Interface

<!-- /MarkdownTOC -->

---

# MAC
- 格式：外接硬碟如果不是 Mac 格式，就無法寫入。
- 開發
	- Java
		- JDK 8: http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
		- 注意！！Netbeans 須和 JDK 版本一致
	- MySQL: https://dev.mysql.com/downloads/mysql/
		- 更改 root 密碼: http://emn178.pixnet.net/blog/post/87659567-mysql%E4%BF%AE%E6%94%B9%E5%AF%86%E7%A2%BC%E8%88%87%E5%BF%98%E8%A8%98%E5%AF%86%E7%A2%BC%E9%87%8D%E8%A8%AD
			- 記下 root temp password
			- 執行進入 MySQL
			- mysql -u 登入使用者 -p
			- SET PASSWORD FOR '登入使用者'@'localhost' = PASSWORD('密碼');
			- flush privileges;
			- done!
		- 如果透過 Java 匯入中文字是問號的話:
			- su 進去
			- 新建立一個檔案 vi /etc/my.cnf，內容如下  
				[client]  
				default-character-set=utf8  
				[mysqld]  
				character-set-server=utf8  
			- 到 GUI 重啟 MySQL
			- check 指令
				- mysql -uroot -p
				- show variables like 'character%';
	- Git: https://git-scm.com/download/mac
		- ssh-keygen -t rsa -b 4096 -C "xxx@xxx"，產生 ssh key
			- 可參考: http://blog.alantsai.net/2016/03/ssh-config-ssh-agent-passphrase-management.html
			- 建議命名 id_rsa_github.pub
		- 如果有兩組 ssh 以上，需建立 config [如果沒建立，會出現 Permission denied (publickey)]
			- 第一組  
				Host github.com  
				HostName github.com  
				User git  
				IdentityFile ~/.ssh/id_rsa_github
			- 第二組  
				Host gitlab.ttfri.org.tw  
				HostName gitlab.ttfri.org.tw  
				User git  
				IdentityFile ~/.ssh/id_rsa_gitlab
		- cat ~/.ssh/id_rsa.pub，複製全部文字
		- 到 GitLab 網站的 SSH Keys 把這段文字貼上去
		- 測試看看: ssh -T -p 13922 git@gitlab.ttfri.org.tw
			- 如果出現 Bad owner or permissions on /home/使用者名稱/.ssh/config
			- 執行 chmod 600 ~/.ssh/config 就可以了
		- 設定識別資料
			- git config --global user.email "xxx@xxx"
		- 設定 .gitignore
			- git rm . -r --cached
			- git add .
			- git commit -m "fixed untracked files"
		- **bug**
			- 如果無法使用: Permissions 0777 for '/Users/username/.ssh/id_rsa' are too open.
				- 到 .ssh 把檔案都 chmod 400 * 就 OK
			- ssh: Could not resolve hostname github.com: nodename nor servname provided, or not known
				- DNS 問題
	- Homebrew
		- /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
		- 安裝 telnet: https://github.com/theeternalsw0rd/homebrew-telnet
			- brew tap theeternalsw0rd/telnet
			- brew install telnet
			- 此時預設路徑是 /usr/local/bin/telnet，需要進入 Recovery Mode
				- 重啟後按 command + R，啟動終端機
				- csrutil diable
				- ln -s /usr/local/Cellar/telnet/54.50.1/bin/telnet /usr/bin/
				- 重啟後按 command + R，啟動終端機
				- csrutil enable
		- 安裝 mas-cli (Mac App Store command line interface): https://free.com.tw/mas-cli-macos-install-app/
			- brew install mas
			- mas install 1246284741
	- IDE
		- Netbeans: https://netbeans.org/downloads/index.html
		- Sequel Pro: https://sequelpro.com/download
		- DBeaver: https://dbeaver.jkiss.org/

- 同步
	- Google Drive: https://www.google.com/intl/zh-TW_ALL/drive/download/
- 文書
	- ~~LibreOffice: https://zh-tw.libreoffice.org/~~
	- OpenOffice: https://www.openoffice.org
	- MicroSoft Office: https://myfcu.fcu.edu.tw/main/infomyfculogin.aspx
	- iWork: https://www.kocpc.com.tw/archives/4201
		- 轉成英文版後更新
- ~~繪圖(還不會用)~~
	- ~~Kirta: https://krita.org/jp/~~
	- iMovie
- 防護
	- Avast: https://www.avast.com/zh-tw/free-mac-security
- 其他
	- FreeMind: http://freemind.sourceforge.net/wiki/index.php/Main_Page
	- FreeFileSync: https://www.freefilesync.org/download.php
	- Mactracker: https://itunes.apple.com/tw/app/mactracker/id430255202?mt=12
	- AppCleaner: https://freemacsoft.net/appcleaner/
	- VLC: https://www.videolan.org/vlc/download-macosx.zh-TW.html
		- 可在 preference 轉成 中文
	- Transmission (續傳軟體): https://transmissionbt.com/download/
	- coconutBattery: http://www.coconut-flavour.com/coconutbattery/
	- Mounty for NTFS: http://enjoygineering.com/mounty/#FAQs
	- KeKa: http://www.kekaosx.com/zh-tw/
- 基本設定
	- 調整滑鼠大小: http://appleuser.com/2016/02/23/accessibility/
	- 設定專屬的 Launchpad 排列方法 (initial: 7 columns \* 5 rows)
		- 直向: defaults write com.apple.dock springboard-rows -int 8
		- 橫向: defaults write com.apple.dock springboard-columns -int 8
		- 完成: killall Dock
	- 啟用NTFS讀寫功能 (待寫...)
	- 製作 USB 開機碟: https://www.newmobilelife.com/2016/09/21/how-to-create-usb-drive-macos-sierra-installer/
		- sudo /Users/fool/Downloads/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/Mac --applicationpath /Users/fool/Downloads/Install\ macOS\ Sierra.app --nointeraction
	- 關閉 spotlight: https://www.howtogeek.com/230424/how-to-disable-system-integrity-protection-on-a-mac-and-why-you-shouldnt/
		- disable System Integrity Protection
			- reboot into recovery mode: Command+R
			- csrutil disable (開啟: csrutil enable)
		- restrat system
		- sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.metadata.mds.plist
- 故障
	- 清 PRAM: 重開機後會聽到「噹」一聲後立刻按下**⌘＋option＋P＋R**
	- 重置 SMC: Shift＋Control＋Option 鍵以及電源按鈕
- 釋放記憶體
	- sudo purge

# MAC(VM)
- http://magicjackting.pixnet.net/blog/post/191234203-%E7%94%A8-vmware-%E5%AE%89%E8%A3%9D%E5%8F%8A%E6%B8%AC%E8%A9%A6-mac-os-x

---

# Linux(Host Ubuntu)
- 一般設定
	- 輸入法
		- gcin:
		- debug: http://hyperrate.com/thread.php?tid=29563
- 開發
	- MySQL: https://dev.mysql.com/downloads/mysql/
		- 遭遇中文是問號的話: http://blog.fens.me/linux-mysql-install/
			- sudo vi /etc/mysql/my.cnf
				- 直接在 my.cnf 最下面新增  
					[client]  
					default-character-set=utf8  
					[mysqld]  
					character-set-server=utf8  
					collation-server=utf8_general_ci  
			- 重啟 MySQL : sudo /etc/init.d/mysql restart
	- Git: https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/
		- ssh-keygen -t rsa -b 4096 -C "xxx@xxx"，產生 ssh key
		- xclip -sel clip < ~/.ssh/id_rsa.pub
		- cat ~/.ssh/id_rsa.pub，複製全部文字
		- 到 GitLab 網站的 SSH Keys 把這段文字貼上去
		- 設定識別資料:
			- git config --global user.email "xxx@xxx"
			- git config --global user.name "John Doe"
	- IDE
		- DBeaver: https://dbeaver.jkiss.org/download/
		- Brackets: http://brackets.io/
- 跨平台
	- PlayOnLinux: https://www.playonlinux.com/en/download.html
		- ~~Office 2010 32 bit (不好用...)~~
- 繪圖
	- krita: https://krita.org/jp/
- 防護
	- Wireshark (免費開源): http://self.jxtsai.info/2016/10/wireshark-for-ubuntu.html
		- sudo add-apt-repository ppa:wireshark-dev/stable
		- sudo apt-get update
		- sudo apt-get install wireshark
		- 出現"Can't run /usr/bin/dumpcap in child process Permission denied"時，sudo adduser $USER wireshark
		- 再把"sudo tcpdump -q -nn -w log"用 Wireshark 開啟
- 其他
	- Shutter: https://magiclen.org/shutter/
	- FreeFileSync: https://www.freefilesync.org/download.php
	- FileZilla: https://filezilla-project.org/download.php?type=client
	- FB Messenger (非官方支援): https://messengerfordesktop.com/
	- PCMAN: https://wiki.ubuntu-tw.org/index.php?title=PCMAN

---

# Linux(VM CentOS)
- 查詢
	- IP
		- ip a 找名稱為 enp0s8
	- Kernel
		- cat /etc/\*-release
	- hostname
		- hostname: 取得目前本機設定好的 Hostname
		- hostname –i: 取得目前本機 Hostname 對應的 IP
		- hostname –I: 取得目前本機設定好的所有 IP 位址
- 將使用者設定成 root 權限
	- visudo
	- 找到  root    ALL=(ALL) ALL
	- 加上  tony    ALL=(ALL) ALL
- 先跑
	- sudo yum update
	- yum install gcc make kernel-devel kernel-headers
	- 執行 vboxadditions 裡面的 autorun.sh
- 安裝 Git
	- yum install git
- 安裝 Apache 並啟動
	- 教學: https://devops.profitbricks.com/tutorials/how-to-set-up-apache-web-server-on-centos-7/#set-up-the-apache-http-server
	- sudo yum install httpd
	- sudo vi /etc/selinux/config
		- SELINUX=disabled
	- firewalld
		- sudo firewall-cmd --permanent --add-port=80/tcp
		- sudo firewall-cmd --reload
		- 可 cat /etc/firewalld/zones/public.xml 確認是否加成功
	- 輸入 IP 會出現 Apache 資訊
- 啟動 Apache
	- 啟動 httpd
		- CentOS 7
			- **systemctl start httpd**
			- systemctl enable httpd
			- 查詢執行狀態: service httpd status
		- Cent)S 6.9
			- service httpd start
			- chkconfig httpd on (開機啟動)
			- 查詢執行狀態: service httpd status
	- 網頁伺服器設定檔: vi /etc/httpd/conf/httpd.conf
		- ServerName 192.168.56.101:80
- 查詢 80 port 是否開啟
	- netstat -ntlp，顯示以下  
		tcp        0      0 0.0.0.0:111             0.0.0.0:\*               LISTEN      -  
		tcp        0      0 192.168.122.1:53        0.0.0.0:\*               LISTEN      -  
		tcp        0      0 0.0.0.0:22              0.0.0.0:\*               LISTEN      -  
		tcp        0      0 127.0.0.1:631           0.0.0.0:\*               LISTEN      -  
		tcp        0      0 127.0.0.1:25            0.0.0.0:\*               LISTEN      -  
		tcp6       0      0 :::111                  :::\*                    LISTEN      -  
		**tcp6       0      0 :::80                   :::\*                    LISTEN      -**  
		tcp6       0      0 :::22                   :::\*                    LISTEN      -  
		tcp6       0      0 ::1:631                 :::\*                    LISTEN      -  
		tcp6       0      0 ::1:25                  :::\*                    LISTEN      -
	- 出現以上代表已經是 IPv4/IPv6 兩種環境同時支援的服務了
	- 如果關掉 (systemctl stop httpd)，輸入 netstat -ntlp 則顯示  
		tcp        0      0 0.0.0.0:111             0.0.0.0:\*               LISTEN      -  
		tcp        0      0 192.168.122.1:53        0.0.0.0:\*               LISTEN      -  
		tcp        0      0 0.0.0.0:22              0.0.0.0:\*               LISTEN      -  
		tcp        0      0 127.0.0.1:631           0.0.0.0:\*               LISTEN      -  
		tcp        0      0 127.0.0.1:25            0.0.0.0:\*               LISTEN      -  
		tcp6       0      0 :::111                  :::\*                    LISTEN      -  
		tcp6       0      0 :::22                   :::\*                    LISTEN      -  
		tcp6       0      0 ::1:631                 :::\*                    LISTEN      -  
		tcp6       0      0 ::1:25                  :::\*                    LISTEN      -
	- lsof -i -P -n | grep :80
		- httpd  8326 apache  4u  IPv6 2394078  0t0  TCP \*:80 (LISTEN)
	- netstat -tun
		- 列出已連線的網路連線狀態  
			Proto Recv-Q Send-Q Local Address           Foreign Address         State  
			tcp        0      0 192.168.56.101:22       192.168.56.1:53692      ESTABLISHED  
			tcp        0     64 192.168.56.101:22       192.168.56.1:54168      ESTABLISHED  
			**tcp6       0      0 192.168.56.101:80       192.168.56.1:54206      TIME_WAIT**
- 測試連線
	- telnet xxx.xxx.xxx.xxx 80
- 資料夾權限設定
	- 777，手動複製到 /var/www/html/ 裡面

- MySQL: https://dev.mysql.com/downloads/mysql/
	- 查詢狀態: systemctl status mysqld.service
	- 關閉 MySQL 服務: systemctl stop mysqld.service
	- 建立空的密碼: 
		- systemctl set-environment MYSQLD_OPTS="--skip-grant-tables"
		- systemctl start mysql
	- mysql -u 登入使用者 -p
		- USE mysql;
		- UPDATE user SET authentication_string=PASSWORD('密碼') WHERE User='登入使用者';
		- flush privileges;
		- done!

---

# Windows
- 開發
	- Git: https://dotblogs.com.tw/kirkchen/2013/04/23/use_ssh_to_interact_with_github_in_windows
		- ssh-keygen -t rsa -C "xxx@xxx"，產生 ssh key
		- cat C:\Users\帳號名稱\.ssh\id_rsa.pub，複製全部文字到 GitLab 網站，到 SSH Keys 把這段文字貼上去
		- ssh -T git@github.com(非預設 port: ssh -T -p 13922 git@gitlab.ttfri.space)，顯示以下  
			The authenticity of host 'github.com (192.30.253.112)' can't be established.  
			RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.  
			Are you sure you want to continue connecting (yes/no)? yes  
			Warning: Permanently added 'github.com,192.30.253.112' (RSA) to the list of known hosts.  
			Hi ShaqtinAFool! You've successfully authenticated, but GitHub does not provide shell access.  
		- 設定識別資料
			- git config --global user.email "xxx@xxx"
			- ~~git config --global user.name "John Doe"~~
		- done !
	- MySQL
		- 將下載檔案解壓縮後放在 C 槽
		- 在 C:\Windows 製作(用 echo %WINDIR% 查路徑)
			- my.ini
			- my.cnf
		- 產生 CSV 檔案所遇到的問題: https://blog.csdn.net/qq_35246620/article/details/78148505
			- 問題: The MySQL server is running with the --secure-file-priv option so it cannot execute this statement
			- 到 C:\ProgramData\MySQL\MySQL Server 5.7 改 my.ini
				- # Secure File Priv.
				- secure-file-priv="C:\Users\tony\Desktop"
			- 安裝服務(如果沒裝的話)
				- 用 admin 開啟 cmd: C:\Program Files\MySQL\MySQL Server 5.7\bin\mysqld --install
				- 顯示 Service successfully installed.
			- 重啟 mysql server
				- 到 C:\Program Files\MySQL\MySQL Server 5.7\bin 底下輸入 mysqladmin.exe -uroot -p shutdown
			- 到 cmd 輸入 services.msc，啟動 MySQL57

	- telnet: https://support.microsoft.com/zh-tw/help/982538

- 其他
	- cmder: http://cmder.net/
		- 初始目錄: 修改 .\cmder_mini\vendor\init.bat
			Set home path  
			:: if not defined HOME set "HOME=%USERPROFILE%"  
			@cd /d "D:\Ubuntu\Documents"
		- 中文不亂碼: set LANG=zh_TW.UTF-8
		- 將 lambda 改成 $: \cmder\vendor\clink.lua，找 lambda
		- 環境變數
		set PATH=%ConEmuBaseDir%\Scripts;%PATH%  
		set LANG=zh_TW.UTF8  
		alias ll=ls -list  
		alias git cm=git commit -m
	- QTTabBar (免費開源): http://qttabbar.wikidot.com/
	- UNetbootin: https://unetbootin.github.io/
	- Pot player: https://potplayer.daum.net/
	- Avast
	- FreeFileSync: https://www.freefilesync.org/download.php
	- HeidiSQL: https://www.heidisql.com/
		- 註解快捷建: 工具 > 設定 > 快捷建 > SQL > 取消/加入註釋 > Ctrl + /

# Windows(TTFRI)
- 主機型號: https://www.asus.com/tw/Commercial-Desktop/BM6675/
	 - USB3.0: http://dlcdnet.asus.com/pub/ASUS/misc/usb30/Intel_USB3_Win7_VER104255.zip?_ga=2.252948105.1821313632.1512825030-1024450722.1512825030
	 - ASUS WiFi n10:
- Xming X Server for Windows: https://sourceforge.net/projects/xming/
- SQL Server
	- SSMS: https://docs.microsoft.com/zh-tw/sql/ssms/download-sql-server-management-studio-ssms
- MySQL
	- 安裝檔: https://dev.mysql.com/downloads/file/?id=473605
	- 參考步驟: https://downloads.mysql.com/docs/mysql-installer-en.pdf
- VirtualBox: https://www.virtualbox.org/wiki/Downloads
	- 建立一個目錄放 VM
	- VirtualBox 5.2.2 Oracle VM VirtualBox Extension Pack: 放在 VM 目錄內
		- 新增在: 檔案 > 喜好設定 > 擴充功能
- 啟用 WCF 元件
	- 終端機輸入: %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:\*']

---

# Chrome
- LastPass
- Google 翻譯
- AdBlock
- ~~Office Online~~
- Imagus
- 遠端桌面: https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp?hl=zh-TW

---

# Sublime
- Package Control: https://packagecontrol.io/installation
- 解決無法輸入中文: https://github.com/lyfeyaj/sublime-text-imfix
	- 此方法同步解決其他程式無法輸入中文的囧境！！
- MarkdownTOC
	- "default_autolink": true
	- "default_bracket": "round"
- Side Bar
- ConvertToUTF8
- ChineseLocalizations
- Trailingspaces
- Markdown Preview: https://github.com/revolunet/sublimetext-markdown-preview
- SublimeTableEditor (到 github 下載專案): https://github.com/vkocubinsky/SublimeTableEditor
- Clickable URLs: https://github.com/leonid-shevtsov/ClickableUrls_SublimeText

---

# Notepad++
- MarkdownViewerPlusPlus: https://github.com/nea/MarkdownViewerPlusPlus
	- 將 dll 放在 Plugins 內

---

# Brackets
- 設定中文語系: Debug >> Switch Language
- 設定自動完成括號: Edit >> Auto close Braces
- Brackets Tree Icons
- Brackets Beautify
- ~~Markdown Preview~~
- HTML Starter Template

---

# Unix Interface
- root
	- 改 vi 顏色
		- vi .bashrc
		- alias vi='vim'
		- source .bashrc
	- 改 vim 設定
		- vi ~/.vimrc
		- set cindent (自動縮排)
		- set cursorline (底線 目前游標位置)
		- syntax on (語法上色)
- User
	- 讓終端機有顏色: http://sodahau.logdown.com/posts/18879-mac-ls
		- vi ~/.bash_profile
		- 加入 export CLICOLOR='true'
		- source ~/.bash_profile
	- 別名 alias
		- vi ~/.bash_profile
		- alias ll='ls -al'
		- source ~/.bash_profile
