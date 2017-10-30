### Config:

1. PermitRootLogin yes
2. UsePAM no
3. exposed port 22
4. default command: /usr/sbin/sshd -D
5. root password: root

### Run example:

1. $ sudo docker run -d -P --name test_sshd lorock/sshd
2. $ sudo docker port test_sshd 22
3.  0.0.0.0:32168

### Default Password:

1. $ ssh root@localhost -p 32168
2. #The password is `root`
3. root@test_sshd $
