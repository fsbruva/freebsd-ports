# Created by: Ed Schouten <ed@fxq.nl>
# $FreeBSD$

PORTNAME=	kissd
PORTVERSION=	0.3
CATEGORIES=	net multimedia
MASTER_SITES=	http://rink.nu/downloads/projects/

MAINTAINER=	rink@FreeBSD.org
COMMENT=	Daemon for providing multimedia files to KiSS DP-50x players

GNU_CONFIGURE=	yes

PLIST_FILES=	bin/kissd

post-patch:
	@${REINPLACE_CMD} -e 's|-lpthread|${PTHREAD_LIBS}|' \
		${WRKSRC}/configure
	@${REINPLACE_CMD} -e '/^AM_CFLAGS/ s|-Werror|${PTHREAD_CFLAGS}|' \
		${WRKSRC}/src/Makefile.in

.include <bsd.port.mk>
