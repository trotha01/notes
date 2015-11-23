# Start boot2docker on load (osx)
```
$ brew info boot2docker
...
==> Caveats
To have launchd start boot2docker at login:
    ln -sfv /usr/local/opt/boot2docker/*.plist ~/Library/LaunchAgents
Then to load boot2docker now:
    launchctl load ~/Library/LaunchAgents/homebrew.mxcl.boot2docker.plist
```


# Old start boot2docker on load
Not needed if the steps above worked

pieces taken from 
http://blog.amussey.com/post/85117547548/docker-starting-docker-on-system-boot-on-osx-via

## Create a file for logging:
``` touch ~/.boot2docker-launch.log ```

## Create file /Applications/Docker/initialize_docker.sh with contents:
```
#!/bin/bash

echo "================"         >>  ~/.boot2docker-launch.log
date                            >> ~/.boot2docker-launch.log
/usr/local/bin/boot2docker up   >> ~/.boot2docker-launch.log
echo "boot2docker up completed" >> ~/.boot2docker-launch.log
echo "================"         >>  ~/.boot2docker-launch.log
```

## Make shell script executable:
```
chmod +x /Applications/Docker/initialize_docker.sh
```

## Create a .plist file at ~/Library/LaunchAgents/com.user.boot2docker.plist
```
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
   <key>Label</key>
   <string>com.user.boot2docker</string>
   <key>Program</key>
   <string>/Applications/Docker/initialize_docker.sh</string>
   <key>RunAtLoad</key>
   <true/>
</dict>
</plist>
```

## Load the .plist file
``` launchctl load ~/Library/LaunchAgents/com.user.boot2docker.plist
