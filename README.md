To enable firewall using ipfw on freebsd 14.2 with ssh traffic should have certain limit of bandwidth with allow some traffic only, we use ipfw setup on freebsd

# login as root user

#First step is in check that your kernel has below thing?
test@freebsd14-2:~ $ sudo sysctl kern.conftxt |grep -i -e altq -e dummynet
options ALTQ_PRIQ
options ALTQ_CDNR
options ALTQ_HFSC
options ALTQ_RIO
options ALTQ_RED
options ALTQ_CBQ
options ALTQ
options DUMMYNET

# check dummynet is loaded or not
test@freebsd14-2:~/project-ipfw-dummynet-altq $ kldstat -v |grep -i dummynet
415 dummynet


# If above both are missing then compile kernel to have support of module
dummynet and ALTQ (actually in this example dummynet only required), 
Now Check file 01-kernel-compile.txt and follow it

# If above both present then follow 03-step-to-enable-ipfw.txt

# Follow ipfw.rules and save as /etc/ipfw.rules

# use command ipfw list to check all rules are loaded or not (example file is ipfw_list.txt)

# ipfw show command will show which rule hit by network traffic

# congratulations you completed ipfw firewall setup on freebsd 14.2 with bandwidth control/traffic shaping on ssh traffic on perticular ip



