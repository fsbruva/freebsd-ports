# Created by: Gasol Wu <gasol.wu@gmail.com>
# $FreeBSD$

PORTNAME=	mosquitto
PORTVERSION=	0.2.2
CATEGORIES=	net pear
MASTER_SITES=	http://pecl.php.net/get/
PKGNAMEPREFIX=	pecl-
DISTNAME=	Mosquitto-${PORTVERSION}
DIST_SUBDIR=	PECL

MAINTAINER=	gasol.wu@gmail.com
COMMENT=	Extension for libmosquitto

LICENSE=	BSD3CLAUSE

BUILD_DEPENDS=	mosquitto>=0:${PORTSDIR}/net/mosquitto

USE_PHP=	yes
USE_PHPEXT=	yes
USES=		tar:tgz

.include <bsd.port.mk>
