# WireGuard

Install Docker and Generate Password HASH

```bash
sudo docker run ghcr.io/wg-easy/wg-easy wgpw <password>
```

now paste that hash here

```bash
docker run -d \
  --name=wg-easy \
  -e LANG=EN \
  -e WG_HOST=<🚨YOUR_SERVER_IP> \
  -e PASSWORD_HASH=<🚨YOUR_ADMIN_PASSWORD_HASH_INCLUDING-SINGLE_QUOTES> \
  -e PORT=51821 \
  -e WG_PORT=51820 \
  -v ~/.wg-easy:/etc/wireguard \
  -p 51820:51820/udp \
  -p 51821:51821/tcp \
  --cap-add=NET_ADMIN \
  --cap-add=SYS_MODULE \
  --sysctl="net.ipv4.conf.all.src_valid_mark=1" \
  --sysctl="net.ipv4.ip_forward=1" \
  --restart unless-stopped \
  ghcr.io/wg-easy/wg-easy

```

- Now Acees the web intereface in this in this port serverip:51821
- Create a new tunnel and download that conf file and add it and activate
