WireGuard
Uruchomienie WireGuard
Start

wg-quick up wg0
Stop

wg-quick down wg0
Status

wg
Tworzenie plików konfiguracyjnych
Plik konfiguracyjny znajdue się:

/etc/wireguard/wg0.conf
Generowanie kluczy
Server
wg genkey | tee server_privatekey | wg pubkey > server_publickey
Client
wg genkey | tee client1_privatekey | wg pubkey > client1_publickey
Przykład
Server
IP Address 10.0.0.1/24
Listen Port 51820
Private Key OL5T6seutQHvMePDJ0+LlvCLobp2E4Rp8KeGIdbqk0k=
Public Key i+453AlpXxLRSAJyiDuJtvIA02lSo/nZpbYdWCaFC0U=

[Interface]
Address = 10.0.0.1/24
ListenPort = 51820
PrivateKey = OL5T6seutQHvMePDJ0+LlvCLobp2E4Rp8KeGIdbqk0k=


[Peer]
PublicKey = ViKkvUP24MYeXYBSRzteSD/xHDVjWDjO3WIqaZxjLGA=
PresharedKey = u0lEokYQjL0N1LyIJ3b/8MnNUCs/YJmAhivA30F42n4=
AllowedIPs = 10.0.0.2/32
Client
IP Address 10.0.0.2/24
Listen Port 51820
Private Key 8PNQGRL1wEGmwc+B3zkmnQNo0gMIMT/Vigf8aU2o+W0=
Public Key ViKkvUP24MYeXYBSRzteSD/xHDVjWDjO3WIqaZxjLGA=

[Interface]
Address = 10.0.0.2/24
ListenPort = 51820
PrivateKey = 8PNQGRL1wEGmwc+B3zkmnQNo0gMIMT/Vigf8aU2o+W0=


[Peer]
PublicKey = i+453AlpXxLRSAJyiDuJtvIA02lSo/nZpbYdWCaFC0U=
PresharedKey = u0lEokYQjL0N1LyIJ3b/8MnNUCs/YJmAhivA30F42n4=
AllowedIPs = 0.0.0.0/0, ::/0
Endpoint = myserver.dyndns.org:51820
