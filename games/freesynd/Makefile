# Created by: Lars Engels <lars.engels@0x20.net>
# $FreeBSD$

PORTNAME=	freesynd
PORTVERSION=	0.7.1
PORTREVISION=	1
CATEGORIES=	games
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}/${PORTNAME}-${PORTVERSION}

MAINTAINER=	madpilot@FreeBSD.org
COMMENT=	Reimplementation of the classic Bullfrog game Syndicate

LIB_DEPENDS=	libpng15.so:${PORTSDIR}/graphics/png

USES=		cmake
USE_SDL=	sdl image mixer

SUB_FILES=	pkg-message

do-install:
	${MKDIR} ${STAGEDIR}${DATADIR}
	${INSTALL_PROGRAM} ${WRKSRC}/src/freesynd ${STAGEDIR}${PREFIX}/bin
	(cd ${WRKSRC} && ${COPYTREE_SHARE} data ${STAGEDIR}${DATADIR})

.include <bsd.port.mk>
