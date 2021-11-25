 # README

 > **NAME**

EASY STEPS ON HOW TO ACCESS REMOTE MySQL DATABASE IN LOCAL PHPADMIN

 > **DESCRIPTION**


In most cases, the MySQL server and phpMyAdmin both are installed on the same server so that the management of the database becomes easy. However, do you know? We can even access the remote server in the phpMyAdmin with just a little tweak. If not, then here is the tutorial on that.

phpMyAdmin is a PHP-based application to easily create, manage, edit, delete, import, and export MySQL databases. That’s is the reason why most of the hosting companies are providing it as a default application either via cPanel or as manually installed on a cloud server. But what about the cloud hosting services especially such as Google, Amazon AWS Ec2 or LightSail, Digital Ocean, etc. where you manually create a server and separate database instances. Well, yes if we are using some pre-built stack such as Bitnami on them it will install the phpMyAdmin by default, or in case you are installing a database within the server instance then you can install phpMyAdmin as well. Both the setup will allow us to access the database application that resides on the same server.

However, a separate database instance on the cloud is something different. It doesn’t provide root access to the database server in most of the cases to make sure the security of it 

In such scenarios, if you still want to manage the cloud or any other web hosting MySQL database then simply install phpMyAdmin locally on your system. Yes, make sure the system you are going to use is secure without any malware. I recommend you should use Linux OS and those are on Windows 10 they can go for WSL (Windows system for Linux) because phpMyAdmin is natively a Linux tool.



[Reference](https://www.how2shout.com/linux/how-to-access-remote-mysql-database-in-local-phpmyadmin/)


  > **VISUAL**

![DATABASE](https://www.how2shout.com/linux/wp-content/uploads/2020/07/ubuntu2004_bgg5hsFxN5-min.jpg)

![PHP](https://www.how2shout.com/linux/wp-content/uploads/2020/07/chrome_p4e0jtJA0e-min.jpg)

  > **INSTALLATION**

{

    Step 1: Enable WSL on Window 10 ( Linux user skip this)

    Those are using Windows 10 system can install phpMyAdmin on its built-in Linux system safely with just a single command. In case you already have installed WSL 1 or WSL 2 on your system then move to the next step otherwise see this tutorial first on installing WSL.

}

{

    Step 2:  Install MySQL

    As phpMyAdmin itself needs a database to work, thus we a one for it on the local machine or server where you are planning to use phpMyAdmin. Hence, use the below command:

}

{

    For Debian, Ubuntu or similar Linux uses an APT package manager

    sudo apt install mysql-server

}

{

    For CentOS or RedHat systems

    yum install mysql
    or
    dnf install mysql

}

{

    Step 3: Install phpMyAdmin locally or on a remote server

    Next, step is to set up this PHP based open-source MySQL database management application. Again its installation is not a cumbersome job.

}

{

    For Ubuntu servers:
    sudo apt install phpMyAdmin

    For CentOS
    First and EPEL repository and then run yum install phpmyadmin.

}

{

    Step 4: Edit configuration file

    Now, before logging in to phpMyAdmin, we need to perform some changes. So, simply on your server command line terminal type the below command to edit the configuration file of this DB management system.

}

{

    sudo vim /etc/phpmyadmin/config.inc.php

    ⇒User arrow key and scroll down to the end of the file.

    ⇒Press the INSERT key on the keyboard and add the following lines:

}

{

    $i++;
    $cfg['Servers'][$i]['host']          = '';
    $cfg['Servers'][$i]['port']          = '';
    $cfg['Servers'][$i]['socket']        = '';
    $cfg['Servers'][$i]['connect_type']  = 'tcp';
    $cfg['Servers'][$i]['extension']     = 'mysql';
    $cfg['Servers'][$i]['compress']      = FALSE;
    $cfg['Servers'][$i]['auth_type']     = 'config';
    $cfg['Servers'][$i]['user']          = '';
    $cfg['Servers'][$i]['password']      = '';

}

{

    After that:

    Host: Inside the two single columns given in front of the host value enter the address of the remote database. For example, in the below-given image, we used the address of a MySQL database created on Amazon Cloud. In the same way, you just need to provide the address, it could be IP address as well.

    Port: The default ports is 3306. If you have changed it then use that instead.

    Next, for security reasons leave the username and password of the Mysql database blank and enter the same while logging phpMyadmin. However, if you know that nobody else is going to access your computer and it is secure. Then simply, add the credential of the MySQL database, user= you-mysql-username, and password= your-myslqdatabase-password.

    Now, save and exit the file. For that press Esc button, type :wq  and then hit the Enter key.

}

{

    Step 5: Run phpMyAdmin to access a remote database

    Whether you have installed it on the local or some remote cloud/hosting server, after installing the phpMyAdmin; open the browser and type the server’s ip-address/phpmyadmin. 

    Note: replace the IP-address text with real IP of yours.

    Once the interface of this open-source database management tool appears you will see the login screen. Enter the username and password of the remote server, in case you haven’t added in the phpMyAdmin configuration file above. And then click on the Server Choice drop-down box to select the remote server IP address or endpoint link.

    Finally, click on the Go button and this will enable you to access the MySQL database on your locally installed phpMyAdmin.

}

> **AUTHOR**

Author Name: Renzther G. Alili

![DATABASE](https://scontent.fceb2-2.fna.fbcdn.net/v/t1.6435-9/94786533_672667246880811_6280057414494453760_n.jpg?_nc_cat=102&ccb=1-5&_nc_sid=174925&_nc_eui2=AeGWbKnW1Keqh7XHewfsIh63r3WGVY09qq6vdYZVjT2qruk8NXStv3m_mhKU-mrHpK2xrL0TzgMhsJ1BYvGDsX6X&_nc_ohc=hLZt7UotOA8AX8v1Lsr&_nc_ht=scontent.fceb2-2.fna&oh=6275c7dd94d4aa5a2bb7b1183a780fd1&oe=61C68043)


