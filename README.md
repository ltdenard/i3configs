yum install cairo-devel libev libev-devel libjpeg-devel libjpeg-turbo libxcb libxkbcommon libxkbcommon-x11 libxkbcommon-x11-devel pam-devel pkg-config xcb-util-devel xcb-util-image xcb-util-image-devel xcb-util-xrm xorg-x11-util-macros

git clone --recursive https://github.com/Airblader/xcb-util-xrm.git

cd xcb-util-xrm

./autogen.sh --prefix=/usr && make && sudo make install

git clone https://github.com/PandorasFox/i3lock-color.git

cd i3lock-color

autoreconf -i
./configure XCB_UTIL_XRM_CFLAGS='-I/usr/include -L/usr/lib' XCB_UTIL_XRM_LIBS='/usr/lib/libxcb-xrm.so'
make
sudo make install


i3lock --linecolor=ffffffff --ringcolor=ffffffff --insidecolor=00000000 --separatorcolor=00ffffff --keyhlcolor=00ffffff --verifcolor=00000000 --bshlcolor=00ffffff --layoutcolor=ffffffff --wrongcolor=ff000000 --timecolor=ffffffff --ringwrongcolor=ffffffff --ringvercolor=ffffffff --insidewrongcolor=ffffffff  --insidevercolor=00000000 -c 000000 --ring-width=4.0

mkdir -p ~/.config/i3status
nano ~/.config/i3status/config