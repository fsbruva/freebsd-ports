# Created by: Brent B. Powers <bbp2006@columbia.edu>
# $FreeBSD$

PORTNAME=	Net-HL7
PORTVERSION=	0.75
CATEGORIES=	net perl5
MASTER_SITES=	SF/hl7toolkit/hl7api/${PORTVERSION}
PKGNAMEPREFIX=	p5-

MAINTAINER=	bbp2006@columbia.edu
COMMENT=	Net::HL7 - A simple yet flexible API for non-XML HL7 applications

PORTDOCS=	README

USES=		perl5
USE_PERL5=	configure

OPTIONS_DEFINE=	DOCS

PORTDOCS=	README

.include <bsd.port.options.mk>

post-install:
	${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_MAN} ${WRKSRC}/${PORTDOCS} ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
