
Feh signage

Installation

Update /etc/lightdm/lightm.conf
add line below [Seat:*]

xserver-command=X -s 0 -dpms

Create service /etc/systemd/system/signage.service with the following content

[Unit]
Description=Signage Service
StartLimitIntervalSec=0

[Service]
Type=simple
Restart=on-failure
RestartSec=1
User=pi
ExecStart=/opt/signage/start-slideshow.sh

[Install]
WantedBy=multi-user.target

Create start script in /opt/signage

#!/bin/bash
DISPLAY=:0.0 XAUTHORITY=/home/pi/.Xauthority /usr/bin/feh -q -p -Z -F -R 60 -Y -D 10.0 /opt/signage/slides

Create directory /opt/signage/slides and place images

Start Service

systemctl start signage.service

Enable Service

systemctl enable signage.service
