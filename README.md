/opt/splunk/etc/deployment-apps/upgrade_uf_win/local/inputs.conf
[script://.\\bin\\deploy.bat]
disabled = 0
interval = -1

/opt/splunk/etc/deployment-apps/upgrade_uf_win/local/app.conf
[ui]
is_visible = false
label = BLK UF for server upgrade Add-on

/opt/splunk/etc/deployment-apps/upgrade_uf_win/bin/deploy.bat
@ECHO OFF
FOR /F "delims=" %%i IN ('wmic service SplunkForwarder get Pathname ^| FINDSTR /m service') DO SET SPLUNKDPATH=%%i
SET SPLUNKPATH=%SPLUNKDPATH:~1,-28%
msiexec.exe /i "%SPLUNKPATH%\etc\apps\upgrade_uf_win\bin\splunkforwarder-8.2.3-cd0848707637-x64-release.msi" DEPLOYMENT_SERVER=192.168.2.41:8089 LAUNCHSPLUNK=1 SERVICESTARTTYPE=auto SPLUNKUSERNAME=admin SPLUNKPASSWORD=splunkedu AGREETOLICENSE=yes /quiet

/opt/splunk/etc/deployment-apps/upgrade_uf_win/metadata/default.meta
[]
access = read : [ * ], write : [ admin ]
export = system

