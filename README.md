# postCloudflared
post cloudflared lewat raspi
1. panggil dari github raspi x64
   - wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-arm64.deb
2. install cloudflared
   - sudo dpkg -i cloudflared-linux-*.deb
3. cek installan
   - sudo dpkg -i cloudflared-linux-*.deb
4. login cloudflared
   - cloudflared tunnel login
5. pilih domain
   - menenyooo.my.id
6. buat tunnel
   - cloudflared tunnel create [namaTunnel]
7. buat dns subdomain
   - cloudflared tunnel route dns [namaTunnel] [subDomain].menenyooo.my.id
8. buat config
   - nano ~/.cloudflared/config.yml
9. isi config
    tunnel: UUID_TUNNEL
    credentials-file: /home/pi/.cloudflared/UUID_TUNNEL.json

    ingress:
      - hostname: [subDomain].menenyooo.my.id
        service: http://localhost:1880 

      - service: http_status:404
  10. isi UUID dengan UUID saat buat tunnel
  11. jalankan tunnel
      - cloudflared tunnel run noderedrumah
