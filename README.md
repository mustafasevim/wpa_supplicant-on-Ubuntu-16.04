# wpa_supplicant on Ubuntu 16.04

1. Install required packages
```
apt-get install dbus libdbus-1-dev libdbus-glib-1-2 libdbus-glib-1-dev libreadline-dev libncurses5-dev libnl-genl-3-dev libnl-3-dev libssl-dev build-essential checkinstall pkg-config wget
```
2. Download wpa_supplicant source package
```
wget https://w1.fi/releases/wpa_supplicant-2.6.tar.gz
```
3. Extract wpa_supplicant2.6.tar.gz
```
tar xzvf wpa_supplicant-2.6.tar.gz
```
4. Go in to extracted wpa_supplicant2.6 folder
```
cd wpa_supplicant-2.6
```
4. Create a build configuration file that should work for standard WiFi setups by running the following command
```
cat > wpa_supplicant/.config << "EOF"
CONFIG_BACKEND=file
CONFIG_CTRL_IFACE=y
CONFIG_DEBUG_FILE=y
CONFIG_DEBUG_SYSLOG=y
CONFIG_DEBUG_SYSLOG_FACILITY=LOG_DAEMON
CONFIG_DRIVER_NL80211=y
CONFIG_DRIVER_WEXT=y
CONFIG_DRIVER_WIRED=y
CONFIG_EAP_GTC=y
CONFIG_EAP_LEAP=y
CONFIG_EAP_MD5=y
CONFIG_EAP_MSCHAPV2=y
CONFIG_EAP_OTP=y
CONFIG_EAP_PEAP=y
CONFIG_EAP_TLS=y
CONFIG_EAP_TTLS=y
CONFIG_IEEE8021X_EAPOL=y
CONFIG_IPV6=y
CONFIG_LIBNL32=y
CONFIG_PEERKEY=y
CONFIG_PKCS12=y
CONFIG_READLINE=y
CONFIG_WPS=y
CONFIG_WPS_ER=y
CONFIG_WNM=y
CFLAGS += -I/usr/include/libnl3
EOF
```
5. Go in to wpa_supplicant folder
```
cd wpa_supplicant
```
6. Compile
```
make && sudo make install
