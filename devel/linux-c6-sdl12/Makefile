# Created by: Johannes Meixner <xmj@chaot.net
# $FreeBSD$

PORTNAME=	sdl
PORTVERSION=	1.2.14
CATEGORIES=	devel linux
DISTNAME=	SDL-${PORTVERSION}-${RPMVERSION}

MAINTAINER=	emulation@FreeBSD.org
COMMENT=	Cross-platform multi-media development API (Linux CentOS ${LINUX_DIST_VER})

CONFLICTS=	linux-sdl12-[0-9]* linux-f8-sdl12-[0-9]*

ONLY_FOR_ARCHS=	i386 amd64
USE_LINUX=	c6
USE_LINUX_RPM=	yes
USE_LINUX_APPS=	xorglibs
INSTALL_SHLIB=	yes
LINUX_NAME=	SDL

RPMVERSION=	3.el6
USE_LDCONFIG=	yes

PLIST_FILES=	usr/lib/libSDL-1.2.so.0 usr/lib/libSDL-1.2.so.0.11.3
DOCSDIR=	${PREFIX}/usr/share/doc/${LINUX_NAME}-${PORTVERSION}
PORTDOCS=	BUGS COPYING CREDITS README-SDL.txt
DESCR=		${.CURDIR}/../${PORTNAME}12/pkg-descr

SRC_DISTFILES=	SDL-1.2.14-3.el6.src.rpm

.include <bsd.port.mk>
