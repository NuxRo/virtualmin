# vmin-nginx

Fronting Virtualmin's Apache with Nginx automatically.

HOW TO (Assuming you start from scratch, tested on CentOS 7)
- Install Virtualmin as usual
- Set Apache to listen on ports 1080 for HTTP and 1443 for HTTPS and apply the configuration, do this from the Virtualmin/Webmin interface so the control panel is aware of the change, make sure to apply the configuration afterwards.
![Webmin Screenshot] (http://img.nux.ro/kJ9-Selection_188.png)


- Install Nginx and set it to include .conf files from /etc/nginx/vhosts/*.conf (and create that dir)
`mkdir /etc/nginx/vhosts
echo "include /etc/nginx/vhosts/*.conf;" > /etc/nginx/default.d/vmin-nginx.conf
service nginx start
systemctl enable nginx`

- Set Virtualmin to run this script as Pre/Post command: /usr/local/bin/vmin-nginx.sh
- Download the script:
`wget https://raw.githubusercontent.com/NuxRo/vmin-nginx/master/vmin-nginx.sh -O /usr/local/bin/vmin-nginx.sh`

`chmod +x /usr/local/bin/vmin-nginx.sh`
