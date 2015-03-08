 Ubuntu-vim-ssh-xampp
首先<br>
1.安装虚拟机  <br>
2.输入用户名密码  <br>
3.选择安装地址  <br>
4.配置虚拟机  <br>
5.安装中  <br>
6.输入用户名密码  <br>
7.按住Ctrl+Alt+T 唤出Terminal <br>
8.输入sudo apt-get install vim-gtk   回车 <br>
9.输入sudo apt-get install ack-grep ctags  回车 <br>
10.输入sudo apt-get install git  回车 <br>
11.输入git clone git://github.com/humiaozuzu/dot-vimrc.git ~/.vim  回车 <br>
12.输入ln -s ~/.vim/vimrc ~/.vimrc  回车 <br>
13.输入git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/vundle  回车 <br>
14.打开vim，执行:BundleInstall <br>
15.按住Ctrl+Alt+T，重开一个Terminal。输入vim回车 <br>
16.登陆https://www.apachefriends.org/index.html下载xampp <br>
17.输入cd ~/Downloads  回车 <br>
18.输入sudo ./xampp-linux-x64-5.6.3-0-installer.run  输入密码 <br>
19.输入astoneman@ubuntu:~$ ssh localhost  <br>
 <br>
ssh: connect to host localhost port 22: Connection refused <br>
 <br>
如上所示，表示没有还没有安装，可以通过apt安装，命令如下： <br>
 <br>
astoneman@ubuntu:~$ sudo apt-get install openssh-server   <br>
 <br>
 <br>
系统将自动进行安装，安装完成以后，先启动服务： <br>
 <br>
astoneman@ubuntu:~$ sudo /etc/init.d/ssh start   <br>
 <br>
 <br>
启动后，可以通过如下命令查看服务是否正确启动 <br>
 <br>
astoneman@ubuntu:~$ ps -e|grep ssh    <br>
 <br>
 9134 ?        00:00:00 ssh-agent <br>
22173 ?        00:00:00 sshd   <br>
 <br>
这样就正式启动ssh了 <br>
20.输入ifconfig  查看ip  记下ip <br>
21.在windows系统打开PuTTY  在Host Name(or IP address)   输入192.168.61.132   点击Open <br>
22.在你的浏览器输入192.168.61.132   会发现禁止访问，要求你改动"httpd-xampp.conf". <br>
23.输入sudo -s	输入nautilus打开文件管理器(root身份打开文件管理) <br>
24.在computer.opt.lampp.etc.extra目录下你会发现httpd-xampp.conf <br>
25.把最后改成 <br>
 <br>
# New XAMPP security concept <br>
<LocationMatch "^/(?i:(?:xampp|security|licenses|phpmyadmin|webalizer|server-status|server-info))"> <br>
	Order deny,allow <br>
	Allow from all| <br>
		fc00::/7 10.0.0.0/8 172.16.0.0/12 192.168.0.0/16\ <br>
		fe80::/10 169.254.0.0/16 <br>
	ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var <br>
        <br>
</LocationMatch> <br>
26.输入/opt/lampp/lampp restart   重启服务器 <br>
27.在电脑端输入IP（192.168.61.132）即可进入服务器 <br>
