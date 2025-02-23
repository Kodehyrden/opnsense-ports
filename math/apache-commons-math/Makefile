PORTNAME=	commons-math
PORTVERSION=	3.6.1
PORTREVISION=	2
CATEGORIES=	math java
MASTER_SITES=	APACHE_COMMONS_SOURCE \
		https://repo1.maven.org/maven2/junit/junit/4.8.2/:source2
PKGNAMEPREFIX=	apache-
DISTNAME=	${PORTNAME}3-${PORTVERSION}-src
DISTFILES=	${DISTNAME}${EXTRACT_SUFX} \
		junit-4.8.2.jar:source2
EXTRACT_ONLY=	${DISTNAME}${EXTRACT_SUFX}

MAINTAINER=	bofh@FreeBSD.org
COMMENT=	Java library of self-contained mathematics and statistics components
WWW=		https://commons.apache.org/proper/commons-math/

LICENSE=	APACHE20

USE_ANT=	yes
USE_JAVA=	yes
USE_LOCALE=	en_US.ISO8859-1

ALL_TARGET=	compile jar
MAKE_ARGS=	-Dlibdir=${WRKDIR} -Dnoget=true

JARFILE=	${PORTNAME:S,3,,}-3.6.jar
DESTJARFILE=	${PORTNAME}.jar
PLIST_FILES+=	${JAVAJARDIR}/${DESTJARFILE}

OPTIONS_DEFINE=	DOCS

NO_ARCH=	yes

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MDOCS}
ALL_TARGET+=	javadoc
PORTDOCS=	LICENSE.txt NOTICE.txt RELEASE-NOTES.txt license-header.txt
.endif

post-extract:
	${MKDIR} ${WRKSRC}/lib
	${CP} ${DISTDIR}/junit-4.8.2.jar ${WRKSRC}/lib/

do-install:
	${MKDIR} ${STAGEDIR}${JAVAJARDIR}
	${INSTALL_DATA} ${WRKSRC}/target/${JARFILE} ${STAGEDIR}${JAVAJARDIR}/${DESTJARFILE}

.if ${PORT_OPTIONS:MDOCS}
	${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/*.txt ${STAGEDIR}${DOCSDIR}/
.endif

.include <bsd.port.mk>
