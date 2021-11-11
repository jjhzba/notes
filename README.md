Indexer:
systemctl start firewalld; systemctl enable firewalld
firewall-cmd --zone=public --add-port=8000/tcp --permanent
firewall-cmd --zone=public --add-port=8089/tcp --permanent
firewall-cmd --zone=public --add-port=8191/tcp --permanent
firewall-cmd --zone=public --add-port=9997/tcp --permanent
firewall-cmd --zone=public --add-port=1514/udp --permanent
firewall-cmd --zone=public --add-port=1515/udp --permanent
firewall-cmd --zone=public --add-port=51433/udp --permanent
firewall-cmd --zone=public --add-forward-port=port=514:proto=udp:toport=1514:toaddr=192.168.2.40 --permanent
firewall-cmd --zone=public --add-forward-port=port=515:proto=udp:toport=1515:toaddr=192.168.2.40 --permanent
firewall-cmd --reload


Deployment Server:
systemctl start firewalld; systemctl enable firewalld
firewall-cmd --zone=public --add-port=8000/tcp --permanent
firewall-cmd --zone=public --add-port=8089/tcp --permanent
firewall-cmd --zone=public --add-port=8191/tcp --permanent
firewall-cmd --zone=public --add-port=514/udp --permanent
firewall-cmd --zone=public --add-port=6514/tcp --permanent
firewall-cmd --reload

Search Head:
systemctl start firewalld; systemctl enable firewalld
firewall-cmd --zone=public --add-port=8000/tcp --permanent
firewall-cmd --zone=public --add-port=8089/tcp --permanent
firewall-cmd --zone=public --add-port=8191/tcp --permanent
firewall-cmd --reload

firewall-cmd --list-ports
firewall-cmd --list-forward-ports


[udp://51433]
_rcvbuf = 16777216
queueSize = 16MB
persistentQueueSize = 128MB

