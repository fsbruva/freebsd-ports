# Created by: Francis Bacque <idroxid01@yahoo.fr>
# $FreeBSD$

PORTNAME=	bbdock
PORTVERSION=	0.2.9
PORTREVISION=	1
CATEGORIES=	x11
MASTER_SITES=	http://bbdock.nethence.com/download/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Application launcher for Blackbox-like window manager

LICENSE=	BSD

LIB_DEPENDS=	libpng15.so:${PORTSDIR}/graphics/png

GNU_CONFIGURE=	yes
USE_XORG=	x11
CPPFLAGS+=	-I${LOCALBASE}/include/libpng15
PORTDOCS=	README

PLIST_FILES=	bin/bbdock

OPTIONS_DEFINE=	DOCS

post-install:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/${PORTDOCS} ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
