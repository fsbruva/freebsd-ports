# Created by: gahr
# $FreeBSD$

PORTNAME=	mysql-connector-c
PORTVERSION=	6.1.5
CATEGORIES=	databases
MASTER_SITES=	${MASTER_SITE_MYSQL}
MASTER_SITE_SUBDIR=	Connector-C
DISTNAME=	${PORTNAME}-${PORTVERSION}-src

MAINTAINER=	gahr@FreeBSD.org
COMMENT=	MySQL database connector for C

LICENSE=	GPLv2

USE_MYSQL=	51+
USE_OPENSSL=	yes
WITH_OPENSSL_PORT=yes
USES=		cmake:outsource compiler:features
CMAKE_ARGS+=	-DWITH_SSL=system \
		-DOPENSSL_INCLUDE_DIR=${LOCALBASE}/include \
		-DOPENSSL_LIBRARY=${LOCALBASE}/lib/libssl.so \
		-DCRYPTO_LIBRARY=${LOCALBASE}/lib/libcrypto.so
USE_LDCONFIG=	${PREFIX}/lib/${PORTNAME}

PLIST_SUB+=	PORTVERSION=${PORTVERSION}

.include <bsd.port.pre.mk>

.if ${ARCH} == "i386" && ${COMPILER_TYPE} == gcc && ${COMPILER_VERSION} <= 42
CFLAGS+=	-march=i586
.endif

.include <bsd.port.post.mk>
