1.

```sh
sudo nano /etc/systemd/system/mailpit.service
```

2.

```sh
[Unit]
Description=Description


[Service]
ExecStart=/usr/local/bin/mailpit
Restart=always
User=root
Group=root


[Install]
WantedBy=multi-user.target
```

3.

```sh
sudo systemctl enable mailpit.service
```

4.

```sh
sudo systemctl start mailpit.service
```
