PORTNAME=	disque-devel
DISTVERSION=	1.0-rc1
CATEGORIES=	net
PORTREVISION=	1

USE_GITHUB=	yes
GH_TUPLE=	antirez:disque:1.0-rc1

MAINTAINER=	manu@bidouilliste.com
COMMENT=	in-memory, distributed job queue

LICENSE=	BSD3CLAUSE

MAKE_JOBS_UNSAFE=yes

USES+=		gmake
USE_RC_SUBR=	disque
BIN_FILES=	disque disque-server

PKGMESSAGE=	${WRKDIR}/pkg-message

USERS=	disque
GROUPS=	disque

DISQUE_DBDIR?=	/var/db/disque
DISQUE_RUNDIR?=	/var/run/disque
DISQUE_LOGDIR?=	/var/log/disque

SUB_FILES=	pkg-message
SUB_LIST+=	PORTNAME=${PORTNAME} \
	DISQUE_USER=${USERS} \
	DISQUE_DBDIR=${DISQUE_DBDIR} \
	DISQUE_LOGDIR=${DISQUE_LOGDIR} \
	DISQUE_RUNDIR=${DISQUE_RUNDIR}

PLIST_SUB+=	DISQUE_USER=${USERS} \
	DISQUE_GROUP=${GROUPS} \
	DISQUE_LOGDIR=${DISQUE_LOGDIR} \
	DISQUE_DBDIR=${DISQUE_DBDIR} \
	DISQUE_RUNDIR=${DISQUE_RUNDIR}

post-build:
	${SED} ${SUB_LIST:S/$/!g/:S/^/ -e s!%%/:S/=/%%!/} \
		${WRKSRC}/disque.conf > ${WRKDIR}/disque.conf

do-install:
	${INSTALL_PROGRAM} ${BIN_FILES:C!^!${WRKSRC}/src/!} ${STAGEDIR}${PREFIX}/bin/
	${INSTALL_DATA} ${WRKDIR}/disque.conf ${STAGEDIR}${PREFIX}/etc/disque.conf.sample
	${MKDIR} ${STAGEDIR}${DISQUE_LOGDIR} \
		${STAGEDIR}${DISQUE_DBDIR} \
		${STAGEDIR}${DISQUE_RUNDIR}

.include <bsd.port.mk>
