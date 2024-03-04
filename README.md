# Gantt chart Project management tools

[https://gantt-online.com/](https://gantt-online.com/)
![A Project ](https://gantt-online.com/api/svg/f14661caf04661f6fe/)


#  Private Deployment Documentation

## Dependent Components
Database `mysql`

## Deployment Steps
1. Go to download the corresponding installation file from https://gantt-online.com/deploy and unzip it
2. Enter the unzipped folder in the command line window and modify the configuration content of `conf.yaml`
3. Execute the command `./gantt-online -c` to get the client token (root permission is required on Linux)
4. Copy the token from Step 3 to create a license authorization code
5. Copy the license created in Step 4 and fill it into the configuration file `conf.yaml`
6. Initialize the service `./gantt-online -i -f conf.yaml` (root permission required on Linux)
7. Start the service `./gantt-online -f conf.yaml` (root permission required on Linux)

> If on Windows, the command `./gantt-online` needs to be changed to `gantt-online.exe`

## Daemon Process Running Method
### Linux 

Recommends Using systemd   
Shortcut `( ./gantt-online -f conf.yaml &)`

Recommend using the following method

```shell


Copy code
#/usr/lib/systemd/system/gantt-online.service 
#sudo systemctl daemon-reload  

[Unit]  
Description=zz plan   


[Service]
Type=simple
# Fill in the absolute path of your running file and configuration below  
ExecStart=/home/gantt/start -f /home/gantt/conf.yaml  
Restart=always
RestartSec=9  
User=root  
Group= root

[Install]  
WantedBy=multi-user.target
```

- Enable the service `systemctl enable gantt-online.service`
- Start the service `systemctl start gantt-online.service`
- Stop the service `systemctl stop gantt-online.service`
- Restart the service `systemctl restart gantt-online.service`

### mac
`( ./gantt-online -f conf.yaml &)` or use `launchctl` to manage

### windows
Can use `nssm` for service management

