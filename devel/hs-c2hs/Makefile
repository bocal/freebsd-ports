# Created by: Oliver Braun <obraun@FreeBSD.org>
# $FreeBSD$

PORTNAME=	c2hs
PORTVERSION=	0.26.1
CATEGORIES=	devel haskell

MAINTAINER=	haskell@FreeBSD.org
COMMENT=	C->Haskell FFI tool that gives some cross-language type safety

LICENSE=	GPLv2

USE_CABAL=	dlist language-c>=0.4.7 shelly>=1.0 text yaml>=0.8

XMLDOCS=	doc/users_guide:html

STANDALONE=	yes
EXECUTABLE=	c2hs

MAN1PAGES=	c2hs.1
MAN1SRC=	doc/man1

.include "${.CURDIR}/../../lang/ghc/bsd.cabal.mk"
.include <bsd.port.mk>
