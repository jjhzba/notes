regenerate SSL Cert for Splunk Web:
/opt/splunk/bin/splunk createssl web-cert -l 2048

/opt/splunk/bin/splunk restart


Install Splunk Enterprise 8.1 or higher with the WiredTiger storage engine
vi /opt/splunk/etc/system/local/server.conf
[kvstore]
storageEngine = wiredTiger

/opt/splunk/bin/splunk show kvstore-status


Migrate the KV store after an upgrade to Splunk Enterprise 8.1 or higher in a single-instance
deployment
/opt/splunk/bin/splunk stop
vi /opt/splunk/etc/system/local/server.conf
[kvstore]
storageEngineMigration = true

/opt/splunk/bin/splunk migrate kvstore-storage-engine --target-engine wiredTiger
/opt/splunk/bin/splunk start
delete /opt/splunk/var/lib/splunk/kvstore/old_db

