# Created by: Steven Kreuzer <skreuzer@exit2shell.com>
# $FreeBSD$

PORTNAME=	ratproxy
PORTVERSION=	1.58
CATEGORIES=	security
MASTER_SITES=	GOOGLE_CODE

MAINTAINER=	skreuzer@FreeBSD.org
COMMENT=	Semi-automated, largely passive web application security audit tool

BROKEN=		Unfetchable (google code has gone away)

USES=		shebangfix ssl
CFLAGS+=	-I${OPENSSLINC}
LDFLAGS+=	-L${OPENSSLLIB}

WRKSRC=		${WRKDIR}/${PORTNAME}

SHEBANG_FILES=	ratproxy-report.sh
PLIST_FILES=	bin/ratproxy \
		bin/ratproxy-report.sh

post-patch:
	@${REINPLACE_CMD} -e 's#-Wno-pointer-sign##g' \
		-e "s|\(-lcrypto\)|${LDFLAGS} \1|g" ${WRKSRC}/Makefile

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/ratproxy ${STAGEDIR}${PREFIX}/bin
	${INSTALL_SCRIPT} ${WRKSRC}/ratproxy-report.sh ${STAGEDIR}${PREFIX}/bin

.include <bsd.port.mk>
