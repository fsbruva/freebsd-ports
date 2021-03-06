# Created by: Satoshi Taoka <taoka@FreeBSD.org>
# $FreeBSD$

PORTNAME=	eijiro-fpw
PORTVERSION=	1.0b
PORTREVISION=	5
CATEGORIES=	japanese
MASTER_SITES=	http://openlab.ring.gr.jp/edict/fpw/dist/eijiro/
DISTNAME=	${PORTNAME}${PORTVERSION}-src

MAINTAINER=	ports@FreeBSD.org
COMMENT=	EIJIRO English - Japanese Dictionary (EPWING V1 format)

EXTRACT_DEPENDS=${LOCALBASE}/share/freepwing/fpwutils.mk:${PORTSDIR}/japanese/freepwing \
		lha:${PORTSDIR}/archivers/lha
BUILD_DEPENDS=	${LOCALBASE}/libexec/freepwing/catdump:${PORTSDIR}/japanese/freepwing \
		ja-p5-Jcode>=0:${PORTSDIR}/japanese/p5-Jcode

MANUAL_PACKAGE_BUILD=	Needs data from CDROM
MAKE_JOBS_UNSAFE=	yes

RESTRICTED=	The original dictionary is not free
USES=		dos2unix gmake perl5
DOS2UNIX_FILES=	Makefile
WRKSRC=		${WRKDIR}/eijiro-fpw${PORTVERSION}
PORTDOCS=	readme.sjis
DICT_PATH?=	/cdrom
SRCFILE?=	eijiro52.txt

PLIST_FILES=	share/dict/eijiro-fpw/eijiro/data/honmon \
		share/dict/eijiro-fpw/catalogs
PLIST_DIRS=	share/dict/eijiro-fpw/eijiro/data \
		share/dict/eijiro-fpw/eijiro \
		share/dict/eijiro-fpw

# For eijiro included in a book sold by ALC Inc.
# (http://www.alc.co.jp/alcshop/eng/eijiro/)
# Avoid copying uncompressed srcfile, it is > 50Mb

.if exists(${DICT_PATH}/${SRCFILE})		# uncompressed
SOURCE_FILE=	${DICT_PATH}/${SRCFILE}
.else						# assume decompression works
SOURCE_FILE=	${WRKDIR}/${SRCFILE}
.endif
MAKE_ARGS+=	SRCFILE=${SOURCE_FILE:Q}

OPTIONS_DEFINE=	DOCS

.include <bsd.port.options.mk>

post-extract:
	@if [ -f ${DICT_PATH}/eijiro-original/*.exe ]; then \
	  lha xiw=${WRKDIR} ${DICT_PATH}/eijiro-original/*.exe '*/${SRCFILE}'; \
	fi
	@if [ ! -f ${SOURCE_FILE:Q} ]; then \
	  ${ECHO} "###################################################"; \
	  ${ECHO} "I cannot find a file ${DICT_PATH}/${SRCFILE}"; \
	  ${ECHO} "Specify the Eijiro Dictionary file with the full path"; \
	  ${ECHO} "and excecute the following command again:"; \
	  ${ECHO} "  make DICT_PATH=${DICT_PATH} SRCFILE=${SRCFILE}"; \
	  ${ECHO} ""; \
	  ${ECHO} "Notice: DICT_PATH must be a full path to the file."; \
	  ${ECHO} "###################################################"; \
	  ${FALSE}; \
	fi
	${CP} ${LOCALBASE}/share/freepwing/fpwutils.mk ${WRKSRC}

post-build:
	cd ${WRKSRC}; ${CP} catalogs.sjis catalogs.txt; \
	${SETENV} CATDUMPFLAGS="-e sjis" fpwmake catalogs

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/share/dict/eijiro-fpw/eijiro/data \
		${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/honmon \
		${STAGEDIR}${PREFIX}/share/dict/eijiro-fpw/eijiro/data
	${INSTALL_DATA} ${WRKSRC}/catalogs \
		${STAGEDIR}${PREFIX}/share/dict/eijiro-fpw
	${INSTALL_DATA} ${WRKSRC}/readme.sjis ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
