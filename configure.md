One part of the NAS I needed to create was a Jail which is a application holder like Docker. I wanted to create a jail to be able to use Transmission which is a torrent downloader and seeder for me to be able to quickly and precisely manage the torrents I download.
```
#Create a temporary file listing the applications to automaticlly be installed in the jail
echo '{"pkgs":["bash","ca_root_nss","jq","openvpn","transmission-cli","transmission-daemon","transmission-web","unzip","unrar","wget","-y p5-Digest-SHA"]}' > /tmp/pkg.json

# Create the jail and automaticlly install the applications inside it
iocage create -n "Transmission" -p /tmp/pkg.json -r 11.2-RELEASE ip4_addr="vnet0|192.168.0.181/24" defaultrouter="192.168.0.1" vnet="on" allow_raw_sockets="1" boot="on"
```
