<!-- MarkdownTOC -->

- [MAC](#mac)
- [Linux\(Ubuntu\)](#linuxubuntu)
- [Linux\(VM CentOS\)](#linuxvm-centos)
- [Windows](#windows)
- [Chrome](#chrome)
- [Sublime](#sublime)

<!-- /MarkdownTOC -->

---

# MAC
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
	- Git: https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/
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
- 文書
	- LibreOffice: https://zh-tw.libreoffice.org/
	- OpenOffice: https://www.openoffice.org
	- MicroSoft Office: https://myfcu.fcu.edu.tw/main/infomyfculogin.aspx
- 繪圖
	- Kirta: https://krita.org/jp/
- 防護
	- Avast: https://www.avast.com/zh-tw/free-mac-security
- 其他
	- FreeFileSync: https://www.freefilesync.org/download.php
	- Mactracker: https://itunes.apple.com/tw/app/mactracker/id430255202?mt=12
	- AppCleaner: https://freemacsoft.net/appcleaner/
	- VLC: https://www.videolan.org/vlc/download-macosx.zh-TW.html
	- Transmission (續傳軟體): https://transmissionbt.com/download/
	- 讓終端機有顏色: http://sodahau.logdown.com/posts/18879-mac-ls
		- vi ~/.bash_profile
		- 加入 export CLICOLOR='true'

---

# Linux(Ubuntu)
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
		- Office 2010 32 bit (不好用...)
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

# Linux(VM CentOS)
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
- 其他
	- cmder 
	- QTTabBar (免費開源): http://qttabbar.wikidot.com/
	- UNetbootin: https://unetbootin.github.io/
	- Pot player: https://potplayer.daum.net/
	- Avast
	- FreeFileSync: https://www.freefilesync.org/download.php
	- HeidiSQL: https://www.heidisql.com/

---

# Chrome
- LastPass
- Google 翻譯
- AdBlock
- Office Online
- Imagus

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