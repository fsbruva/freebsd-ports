# Created by: Andy Pavlo <amp0928@rit.edu>
# $FreeBSD$

PORTNAME=	hotkeys
PORTVERSION=	0.5.7.1
PORTREVISION=	16
CATEGORIES=	misc
MASTER_SITES=	http://ypwong.org/hotkeys/${PORTVERSION}/
DISTNAME=	hotkeys_${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Allows usage of special keys on internet/multimedia keyboards

LICENSE=	GPLv2

LIB_DEPENDS=	libxml2.so:${PORTSDIR}/textproc/libxml2

WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}
CONFIGURE_ARGS=	--with-db3-inc=${BDB_INCLUDE_DIR} \
		--with-db3-lib=${BDB_LIB_DIR} \
		--with-db-name=${BDB_LIB_NAME}

USE_XORG=	x11 xkbfile xmu xft
GNU_CONFIGURE=	yes
USE_BDB=	yes
USES=		gmake

OPTIONS_DEFINE=	OSD
OPTIONS_DEFAULT=	OSD

OSD_LIB_DEPENDS=	libxosd.so:${PORTSDIR}/misc/xosd
OSD_CONFIGURE_WITH=	xosd

post-extract:
	@${CP} ${PATCHDIR}/error.h ${WRKSRC}/src
	@${CP} ${PATCHDIR}/eliteduo.def ${WRKSRC}/def
	@${CP} ${PATCHDIR}/logitech-ultrax.def ${WRKSRC}/def

post-patch:
	@${REINPLACE_CMD} -e '/^install-exec-am/s/install-sysconfDATA//' \
		${WRKSRC}/src/Makefile.in
post-configure:
	${REINPLACE_CMD} -e 's,-lXinerama,-lXinerama `pkgconf --libs pangoxft`,g' ${WRKSRC}/src/Makefile

post-install:
	@${INSTALL_DATA} ${WRKSRC}/src/hotkeys.conf ${STAGEDIR}${PREFIX}/etc/hotkeys.conf.sample

.include <bsd.port.mk>
