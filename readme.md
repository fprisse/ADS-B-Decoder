# Dependencies
sudo apt install build-essential fakeroot debhelper librtlsdr-dev pkg-config \
  libncurses-dev libbladerf-dev libhackrf-dev liblimesuite-dev libsoapysdr-dev \
  git lighttpd

# Clone and build
git clone https://github.com/flightaware/dump1090
cd dump1090
./prepare-build.sh bookworm
cd package-bookworm
dpkg-buildpackage -b --no-sign
cd ..

# Install (replace [version] with actual version number, e.g. dump1090-fa_10.2_amd64.deb)
sudo dpkg -i dump1090-fa_[version]_amd64.deb
