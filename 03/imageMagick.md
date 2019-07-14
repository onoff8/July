# imageMagick

의존성 모듈 설치


>yum install -y tcl-devel libpng-devel libjpeg-devel 

>yum install -y ghostscript-devel bzip2-devel freetype-devel libtiff-devel zlib-devel

>yum install -y ImageMagick-c++ ImageMagick-c++-devel

wget http://www.imagemagick.org/download/ImageMagick.tar.gz

>tar xvzf ImageMagick.tar.gz

>cd ImageMagick-7.0.4-0

>./configure CXX=CC CXXFLAGS=-O2 --prefix=/usr/local

>make clean

>make

>make install

>/sbin/ldconfig /usr/local/lib

>/usr/local/bin/convert logo: logo.gif

>make check

<pre>`# identify -version

Version: ImageMagick 7.0.4-0 Q16 x86_64 2015-09-14 http://www.imagemagick.org

Copyright: Copyright (C) 1999-2015 ImageMagick Studio LLC

License: http://www.imagemagick.org/script/license.php

Features: Cipher DPC OpenMP

Delegates (built-in): bzlib fontconfig freetype jng jpeg pangocairo png x xml zlib`

<u>png나 jpeg가 delegate에 보이지 않는다면 이모듈이 설치된 곳을 확인</u>

# locate libpng

/usr/bin/libpng-config

/usr/bin/libpng12-config

/usr/include/libpng12

/usr/include/libpng12/png.h

/usr/include/libpng12/pngconf.h

/usr/lib64/libpng.so

/usr/lib64/libpng.so.3

/usr/lib64/libpng.so.3.49.0

/usr/lib64/libpng12.so

/usr/lib64/libpng12.so.0

/usr/lib64/libpng12.so.0.49.0

/usr/lib64/compiz/libpng.so

/usr/lib64/gthumb/modules/libpngexporter.so

/usr/lib64/pkgconfig/libpng.pc

/usr/lib64/pkgconfig/libpng12.pc


<u>/usr/lib64 에 들어가 있다면 make 에 옵션을 주고 다시 해보자.</u>


# make clean

# make libdir=/usr/lib64

# make libdir=/usr/lib64 install


# identify -version

Version: ImageMagick 7.0.4-0 Q16 x86_64 2015-09-14 http://www.imagemagick.org

Copyright: Copyright (C) 1999-2015 ImageMagick Studio LLC

License: http://www.imagemagick.org/script/license.php

Features: Cipher DPC OpenMP

Delegates (built-in): bzlib fontconfig freetype jng jpeg pangocairo png x xml zlib
</pre>
