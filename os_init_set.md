<!-- MarkdownTOC -->

- MAC
- Linux\(Ubuntu\)
- Windows

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
		- 產生 ssh key: ssh-keygen -t rsa -b 4096 -C "註冊電子郵件"
		- cat ~/.ssh/id_rsa.pub，複製全部文字
		- 到 GitLab 網站的 SSH Keys 把這段文字貼上去
	- IDE
		- Netbeans: https://netbeans.org/downloads/index.html
		- Sequel Pro: https://sequelpro.com/download
- 文書
	- LibreOffice: https://zh-tw.libreoffice.org/
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
		- 產生 ssh key: ssh-keygen -t rsa -b 4096 -C "註冊電子郵件"
		- xclip -sel clip < ~/.ssh/id_rsa.pub
		- cat ~/.ssh/id_rsa.pub，複製全部文字
		- 到 GitLab 網站的 SSH Keys 把這段文字貼上去
		- 設定識別資料:
			- git config --global user.email "註冊電子郵件"
			- git config --global user.name "John Doe"
	- IDE
		- DBeaver: https://dbeaver.jkiss.org/download/
		- Brackets: http://brackets.io/
- 跨平台
	- PlayOnLinux: https://www.playonlinux.com/en/download.html
		- Office 2010 32 bit
- 文書
	- Sublime
		- Package Control: https://packagecontrol.io/installation
		- 解決無法輸入中文: https://github.com/lyfeyaj/sublime-text-imfix
			- 此方法同步解決其他程式無法輸入中文的囧境！！
		- MarkdownTOC
		- Side Bar
		- ConvertToUTF8
		- Trailingspaces
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

# Windows
- 開發
	- cmder 
	- Git: https://dotblogs.com.tw/kirkchen/2013/04/23/use_ssh_to_interact_with_github_in_windows
			- 產生 ssh key: ssh-keygen -t rsa -C "註冊電子郵件"
			- cat C:\Users\Belle\.ssh\id_rsa.pub，複製全部文字到 GitLab 網站，到 SSH Keys 把這段文字貼上去
			- ssh -T git@github.com，顯示以下  
				The authenticity of host 'github.com (192.30.253.112)' can't be established.  
				RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.  
				Are you sure you want to continue connecting (yes/no)? yes  
				Warning: Permanently added 'github.com,192.30.253.112' (RSA) to the list of known hosts.  
				Hi ShaqtinAFool! You've successfully authenticated, but GitHub does not provide shell access.  
			- 設定識別資料:
				- git config --global user.email "註冊電子郵件"
				- git config --global user.name "John Doe"
			- done !