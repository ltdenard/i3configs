First, install the required packages
```
sudo yum install -y cairo-devel libev libev-devel libjpeg-devel libjpeg-turbo libxcb libxkbcommon libxkbcommon-x11 libxkbcommon-x11-devel pam-devel pkg-config xcb-util-devel xcb-util-image xcb-util-image-devel xcb-util-xrm xorg-x11-util-macros
```
Second, pull down a dependancy for i3-color
```
git clone --recursive https://github.com/Airblader/xcb-util-xrm.git
cd xcb-util-xrm
./autogen.sh --prefix=/usr && make && sudo make install
```
Third, compile i3-color for custom i3lock screen
```
git clone https://github.com/PandorasFox/i3lock-color.git
cd i3lock-color
autoreconf -i
./configure XCB_UTIL_XRM_CFLAGS='-I/usr/include -L/usr/lib' XCB_UTIL_XRM_LIBS='/usr/lib/libxcb-xrm.so'
make
sudo make install
```
Finally, copy configs into place and reload with $mod+Shift+r
```
cp config ~/.config/i3/config
mkdir -p ~/.config/i3status
cp i3statusconfig ~/.config/i3status/config
```
