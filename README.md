
# Install on Ubuntu

```bash
# Get
git clone https://github.com/tomlobato/http-statuscode-exporter
cd http-statuscode-exporter

# Copy bin
cp nc_nginx_status_codes /usr/local/sbin/nc_nginx_status_codes
chmod 755 /usr/local/sbin/nc_nginx_status_codes

# Setup service
cp nc_nginx_status_codes.service /etc/systemd/system/nc_nginx_status_codes.service
systemctl daemon-reload
systemctl enable nc_nginx_status_codes.service
systemctl start nc_nginx_status_codes.service
systemctl status nc_nginx_status_codes.service

# Test
root@tsrv:~# curl http://localhost:9144/metrics
nc_nginx_status_codes{file="access",code="200"} 1
nc_nginx_status_codes{file="access",code="301"} 5
nc_nginx_status_codes{file="access_monit",code="200"} 135
nc_nginx_status_codes{file="access_monit",code="404"} 2

```
