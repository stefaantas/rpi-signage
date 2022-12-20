# Digital Signage for Raspberry Pi
Basic solution for using feh within raspbian in order to start slideshows (digital signage).
This is meant to be a standalone solution, not requiring network capabilities.

The repository contains the required files in their directory structure /opt/signage, /etc/lightdm and /etc/systemd/system.
You can pull the repository locally and move the files to the appropriate folders.

lightdm.conf: you can either replace the file with the conf in this repository or add the following line below [Seat:*] in your existing config:
```xserver-command=X -s 0 -dpms``` 
Do not forget to reboot to apply.

Starting the service:
```systemctl start signage.service```

Enabling the service:
```systemctl enable signage.service```

Script to be located in /opt/signage -> do not forget to add execution permissions using ```chmod +x /opt/signage/start-slideshow.sh```

Slides to be uploaded in /opt/signage/slides
