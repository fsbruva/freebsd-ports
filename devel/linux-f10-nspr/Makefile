# Created by: bsam
# $FreeBSD$

PORTNAME=	nspr
PORTVERSION=	4.7.6
PORTREVISION=	1
CATEGORIES=	devel linux
MASTER_SITES=	CRITICAL/rpm/${LINUX_RPM_ARCH}/fedora/${LINUX_DIST_VER}

MAINTAINER=	emulation@FreeBSD.org
COMMENT=	Netscape Portable Runtime (Linux Fedora 10)

CONFLICTS=	linux-f8-nspr-[0-9]*

USE_LINUX=	f10
USE_LINUX_RPM=	yes

RPMVERSION=	1.fc10.1

PLIST_FILES=	lib/libnspr4.so lib/libplc4.so lib/libplds4.so
DESCR=		${.CURDIR}/../${PORTNAME}/pkg-descr

.include <bsd.port.mk>
