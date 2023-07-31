pkgname="matlab-docker-wrapper"
pkgdesc="Wrapper to enable running MATLAB within a Docker container"
pkgver="0.1"
pkgrel="1"

arch=("any")
depends=("docker" "libnotify")
source=("matlab-docker-wrapper" "matlab-docker-wrapper.desktop")
b2sums=("SKIP" "SKIP")

MATLAB_VER_UPPER="R2023a"
MATLAB_VER_LOWER=`echo $MATLAB_VER_UPPER | tr 'R' 'r'`
CONTAINER_ICON_PATH="/opt/matlab/$MATLAB_VER_UPPER/bin/glnxa64/cef_resources/matlab_icon.png"

prepare() {
  # populate the version within the wrapper and desktop file
  sed -i \
    "s/\$MATLAB_VER_UPPER/$MATLAB_VER_UPPER/g; s/\$MATLAB_VER_LOWER/$MATLAB_VER_LOWER/g" \
    matlab-docker-wrapper matlab-docker-wrapper.desktop

  # grab the MATLAB icon from the container
  docker run --rm \
    --name matlab-docker-wrapper--prepare \
    --entrypoint /bin/bash mathworks/matlab:$MATLAB_VER_LOWER \
    -c "base64 $CONTAINER_ICON_PATH" | base64 -d > $srcdir/icon.png
}

package() {
  install -D -t "$pkgdir/usr/bin" "$srcdir/matlab-docker-wrapper"
  install -D -t "$pkgdir/usr/share/matlab-docker-wrapper" "$srcdir/icon.png"
  install -D -t "$pkgdir/usr/share/applications" "$srcdir/matlab-docker-wrapper.desktop"
}
