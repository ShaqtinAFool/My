<!-- MarkdownTOC -->

- [MAC](#mac)
- [Linux\(Host Ubuntu\)](#linuxhost-ubuntu)
- [Linux\(VM CentOS\)](#linuxvm-centos)
- [Windows](#windows)
- [Windows\(TTFRI\)](#windowsttfri)
- [Chrome](#chrome)
- [Sublime](#sublime)

<!-- /MarkdownTOC -->

---

# MAC
- 格式：外接硬碟如果不是 Mac 格式，就無法寫入。
- 開發
	- Java
		- JDK 8: http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
		- 注意！！Netbeans 須和 JDK 版本一致
	- MySQL: https://dev.mysql.com/downloads/mysql/
		- 更改 root 密碼
			- 記下 root temp password
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
				Host gitlab.ttfri.space  
				HostName gitlab.ttfri.space  
				User git  
				IdentityFile ~/.ssh/id_rsa_gitlab
		- cat ~/.ssh/id_rsa.pub，複製全部文字
		- 到 GitLab 網站的 SSH Keys 把這段文字貼上去
		- 測試看看: ssh -T -p 13922 git@gitlab.ttfri.space
			- 如果出現 Bad owner or permissions on /home/使用者名稱/.ssh/config
			- 執行 chmod 600 ~/.ssh/config 就可以了
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
	- IDE
		- Netbeans: https://netbeans.org/downloads/index.html
		- Sequel Pro: https://sequelpro.com/download
		- DBeaver: https://dbeaver.jkiss.org/
		- Brackets: http://brackets.io/
			- 設定中文語系: Debug >> Switch Language
			- 設定自動完成括號: Edit >> Auto close Braces
			- Brackets Icons
			- Brackets Beautify
			- Markdown Preview
- 同步
	- Google Drive: https://www.google.com/intl/zh-TW_ALL/drive/download/
- 文書
	- LibreOffice: https://zh-tw.libreoffice.org/
	- OpenOffice: https://www.openoffice.org
	- MicroSoft Office: https://myfcu.fcu.edu.tw/main/infomyfculogin.aspx
- ~~繪圖(還不會用)~~
	- ~~Kirta: https://krita.org/jp/~~
- 防護
	- Avast: https://www.avast.com/zh-tw/free-mac-security
- 其他
	- FreeMind: http://freemind.sourceforge.net/wiki/index.php/Main_Page
	- FreeFileSync: https://www.freefilesync.org/download.php
	- Mactracker: https://itunes.apple.com/tw/app/mactracker/id430255202?mt=12
	- AppCleaner: https://freemacsoft.net/appcleaner/
	- VLC: https://www.videolan.org/vlc/download-macosx.zh-TW.html
	- Transmission (續傳軟體): https://transmissionbt.com/download/
- 基本設定
	- 讓終端機有顏色: http://sodahau.logdown.com/posts/18879-mac-ls
		- vi ~/.bash_profile
		- 加入 export CLICOLOR='true'
	- 別名 alias
		- vi ~/.bash_profile
		- alias ll='ls -l'
		- source ~/.bash_profile
	- 調整滑鼠大小: http://appleuser.com/2016/02/23/accessibility/
	- 設定專屬的 Launchpad 排列方法 (initial: 7 columns * 5 rows)
		- 直向: defaults write com.apple.dock springboard-rows -int 8
		- 橫向: defaults write com.apple.dock springboard-columns -int 8
		- 完成: killall Dock
	- 啟用NTFS讀寫功能 (待寫...)

- 硬體層面
	- if 故障
		- 清 PRAM: 重開機後會聽到「噹」一聲後立刻按下**⌘＋option＋P＋R**
		- 重置 SMC: Shift＋Control＋Option 鍵以及電源按鈕
	- 立馬釋放記憶體
		- sudo purge

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
- 查詢 IP
	- ip a 找名稱為 enp0s8
- 將使用者設定成 root 權限
	- visudo
	- 找到  root    ALL=(ALL) ALL
	- 加上  tony    ALL=(ALL) ALL
- 先跑
	- sudo yum update
	- yum install gcc make kernel-devel kernel-headers
	- 執行 vboxadditions 裡面的 autorun.sh

- 安裝 Apache
	- sudo yum install httpd

- 安裝 Git
	- yum install git

- 啟動 Apache
	- 啟動 httpd
		- systemctl start httpd
		- systemctl enable httpd
		- 查詢執行狀態: service httpd status
	- 網頁伺服器設定檔: vi /etc/httpd/conf/httpd.conf
		- ServerName 192.168.56.101:80

---

# Windows
- 開發
	- Git: https://dotblogs.com.tw/kirkchen/2013/04/23/use_ssh_to_interact_with_github_in_windows
		- ssh-keygen -t rsa -C "xxx@xxx"，產生 ssh key
		- cat C:\Users\Belle\.ssh\id_rsa.pub，複製全部文字到 GitLab 網站，到 SSH Keys 把這段文字貼上去
		- ssh -T git@github.com(非預設 port: ssh -T -p 13922 git@gitlab.ttfri.space)，顯示以下  
			The authenticity of host 'github.com (192.30.253.112)' can't be established.  
			RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.  
			Are you sure you want to continue connecting (yes/no)? yes  
			Warning: Permanently added 'github.com,192.30.253.112' (RSA) to the list of known hosts.  
			Hi ShaqtinAFool! You've successfully authenticated, but GitHub does not provide shell access.  
		- 設定識別資料
			- git config --global user.email "xxx@xxx"
			- git config --global user.name "John Doe"
		- done !
	- MySQL
- 其他
	- cmder: http://cmder.net/
		- 中文不亂碼: set LANG=zh_TW.UTF-8
	- QTTabBar (免費開源): http://qttabbar.wikidot.com/
	- UNetbootin: https://unetbootin.github.io/
	- Pot player: https://potplayer.daum.net/
	- Avast
	- FreeFileSync: https://www.freefilesync.org/download.php
	- HeidiSQL: https://www.heidisql.com/

# Windows(TTFRI)
- 主機型號: https://www.asus.com/tw/Commercial-Desktop/BM6675/
	 - USB3.0: http://dlcdnet.asus.com/pub/ASUS/misc/usb30/Intel_USB3_Win7_VER104255.zip?_ga=2.252948105.1821313632.1512825030-1024450722.1512825030

---

# Chrome
- LastPass
- Google 翻譯
- AdBlock
- Office Online
- Imagus
- 遠端桌面: https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp?hl=zh-TW

---

# Sublime
- Package Control: https://packagecontrol.io/installation
- 解決無法輸入中文: https://github.com/lyfeyaj/sublime-text-imfix
	- 此方法同步解決其他程式無法輸入中文的囧境！！
- MarkdownTOC
	- "default_bracket": "round"
- Side Bar
- ConvertToUTF8
- Trailingspaces