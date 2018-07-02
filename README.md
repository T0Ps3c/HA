## Raspberry Pi 3 / Raspbian Stretch

### Dependencies
    sudo apt install bash jq curl
    curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
    sudo apt-get install -y nodejs

### Docker CE
    sudo curl -SsL https://get.docker.com | bash

### Portainer
    sudo docker volume create portainer_data
    sudo docker run -d --restart=always --name portainer -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer

### Home Assistant
    curl -sL https://raw.githubusercontent.com/home-assistant/hassio-build/master/install/hassio_install | bash -s -- -m raspberrypi3

### Netdata
    sudo docker run -d --restart=always --name netdata -p 19999:19999 mhiro2/rpi-netdata

### Kerberos
    sudo docker run -d --restart=always --name camera1 -p 80:80 -p 8889:8889 kerberos/kerberos

### MotionEye
    sudo docker run -d --restart=always --name=motioneye -p 8765:8765 -p 8081:8081 -v /etc/localtime:/etc/localtime:ro -v /etc/motioneye:/etc/motioneye -v /var/lib/motioneye:/var/lib/motioneye ccrisan/motioneye:dev-armhf

### Zoneminder
    sudo docker run -d --restart=always --name zoneminder -p 8080:80 -e TZ="Europe/Amsterdam" --privileged="true" -v "/opt/zoneminder/config":"/config":rw -v "/opt/zoneminder/data":"/var/cache/zoneminder":rw koenkk/rpi-zoneminder
