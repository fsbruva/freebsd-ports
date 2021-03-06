# $FreeBSD$

PORTNAME=	pike78
PORTVERSION=	${PIKEVERSION}
PORTREVISION=	1
CATEGORIES=	lang
MASTER_SITES=	http://pike.ida.liu.se/pub/pike/all/${PORTVERSION}/ \
		ftp://pike.ida.liu.se/pub/pike/beta/${PORTVERSION}/ \
		http://pike.ida.liu.se/pub/pike/beta/${PORTVERSION}/ \
		ftp://ftp.caudium.net/pike/official_releases/${PORTVERSION}/
DISTNAME=	Pike-v${PORTVERSION}

MAINTAINER=	johans@FreeBSD.org
COMMENT=	Dynamic programming language with a syntax similar to C++

LIB_DEPENDS=	libjpeg.so:${PORTSDIR}/graphics/jpeg \
		libtiff.so:${PORTSDIR}/graphics/tiff \
		libgdbm.so:${PORTSDIR}/databases/gdbm \
		libpcre.so:${PORTSDIR}/devel/pcre \
		libgmp.so:${PORTSDIR}/math/gmp \
		libnettle.so:${PORTSDIR}/security/nettle

CONFLICTS=	pike7[26]-[0-9]*

OPTIONS_DEFINE=	TTF FREETYPE MYSQL PGSQL
OPTIONS_DEFAULT=TTF FREETYPE MYSQL
NO_OPTIONS_SORT=yes
TTF_DESC?=		Enable FreeType 1 (libttf) font rendering engine
TTF_LIB_DEPENDS=	libttf.so:${PORTSDIR}/print/freetype
TTF_CONFIGURE_WITH=	ttflib
FREETYPE_LIB_DEPENDS=	libfreetype.so:${PORTSDIR}/print/freetype2
FREETYPE_CONFIGURE_WITH=freetype
MYSQL_USE=		mysql=yes
MYSQL_CONFIGURE_WITH=	mysql
PGSQL_USE=		pgsql=yes
PGSQL_CONFIGURE_WITH=	pgsql

CFLAGS+=	-ffast-math -fomit-frame-pointer

GNU_CONFIGURE=	yes
CONFIGURE_ENV=	CPPFLAGS+=${PTHREAD_CFLAGS} M4="/usr/bin/m4 -g"
CONFIGURE_ARGS+=	--without-debug \
		 --with-thread-library=${PTHREAD_LIBS} \
		 --with-double-precision \
		 --with-long-double-precision \
		 --disable-rpath \
		 --without-rtldebug \
		 --without-cdebug \
		 --without-copt \
		 --without-security \
		 --with-oob \
		 --without-poll \
		 --without-devpoll \
		 --with-max-fd=60000 \
		 --with-gmp \
		 --with-zlib \
		 --with-threads \
		 --with-readline \
		 --with-jpeg \
		 --with-tiff \
		 --with-gdbm \
		 --with-perl \
		 --with-relocatable-dumped-modules \
		 --without-GL --without-GLUT \
		 --without-GTK \
		 --without-ffmpeg \
		 --without-fftw \
		 --without-glade \
		 --without-gnome \
		 --without-gssapi \
		 --without-java \
		 --without-libglade-config \
		 --without-libpdf --without-libpanda \
		 --without-machine-code \
		 --without-msql \
		 --without-odbc \
		 --without-sane \
		 --without-svg \
		 --without-sybase \
		 --prefix=${PREFIX}

USES=		bison gettext gmake perl5

PLIST_FILES=	bin/pike bin/pike78 bin/hilfe \
		man/man1/pike.1.gz

ONLY_FOR_ARCHS=	i386 amd64

do-configure:
	@${MAKE} -C ${WRKSRC} configure CONFIGUREARGS="${CONFIGURE_ARGS}"

post-patch:
	@${REINPLACE_CMD} -e 's| -lgmp| -L${LOCALBASE}/lib -lgmp|' \
		${WRKSRC}/src/modules/Gmp/configure ${WRKSRC}/src/modules/_Image_XFace/configure
	@${REINPLACE_CMD} -e '/memchr_memcmp.*needle/s/^/static /' \
		${WRKSRC}/src/pike_search_engine2.c
	@${REINPLACE_CMD} -e 's|%%PTHREAD_CFLAGS%%|${PTHREAD_CFLAGS}|' \
		-e 's|%%PTHREAD_LIBS%%|${PTHREAD_LIBS}|' \
		-e 's|,-Bshareable|& -shared|' \
		${WRKSRC}/src/configure
	@${REINPLACE_CMD} -e '/install.*MANDIR/s|^|//|' \
		${WRKSRC}/bin/install.pike

do-install:
	@cd ${WRKSRC} && ${MAKE_CMD} ${INSTALL_TARGET} buildroot=${STAGEDIR}

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/pike/${PORTVERSION}/bin/pike
	${INSTALL_SCRIPT} ${WRKSRC}/bin/hilfe ${STAGEDIR}${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/man/pike.1 ${STAGEDIR}${MAN1PREFIX}/man/man1
	@cd ${STAGEDIR}${PREFIX} && \
		(${FIND} pike/${PORTVERSION} ! -type d && \
		${FIND} pike/${PORTVERSION} -type d -empty -delete && \
		${FIND} -d pike/${PORTVERSION} -type d | \
		${SED} 's,^,@dirrm ,' && \
		${ECHO_CMD} '@unexec rmdir %D/pike 2>/dev/null || true' \
		) >> ${TMPPLIST}

verify:
	cd ${WRKSRC}; ${MAKE_CMD} verify

.include "Makefile.common"
.include <bsd.port.mk>
