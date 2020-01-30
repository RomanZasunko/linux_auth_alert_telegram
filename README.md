Sends a message in telegrams when someone enters your Linux.
You can receive such messages:

        open_session  on   'vps Linux_Ubuntu 185.***.***.75 ' 
        Service: sshd. Login {roman} from 176.**.***.2 - Sat Jan 18 21:13:11 MSK 2020
        
        close_session  on   'vps Linux_Ubuntu 185.***.****.75 ' 
        Service: sshd. Login {root} from 176.**.***.2 - Sat Jan 18 21:54:01 MSK 2020
        
Put this script in   /bin/login-notify

Edit config  /etc/pam.d/sshd , Add this line here:

        session    optional     pam_exec.so  /bin/login-notify

Do not forget to give the right to execute the script file. 
        sudo chmod +x /bin/login-notify

Restart ssh service
        sudo systemctl restart ssh
        
If you do not have an ssh connection, then you need to register this line in /etc/pam.d/login
