# $Id$
# $OpenBSD: Makefile,v 1.17 2008/09/03 13:29:33 sthen Exp $

COMMENT=	wiki and bug tracking system for software projects

MODPY_EGG_VERSION=0.11.5
DISTNAME=	Trac-${MODPY_EGG_VERSION}
PKGNAME=	trac-${MODPY_EGG_VERSION}p0
CATEGORIES=	www devel

MAINTAINER=	Olivier Mehani <shtrom-openbsd@ssji.net>

HOMEPAGE=	http://trac.edgewall.org/

MASTER_SITES=	ftp://ftp.edgewall.com/pub/trac/ \
		http://ftp.edgewall.com/pub/trac/

# BSD
PERMIT_PACKAGE_CDROM=   Yes
PERMIT_PACKAGE_FTP=     Yes
PERMIT_DISTFILES_CDROM= Yes
PERMIT_DISTFILES_FTP=   Yes

MODULES=	lang/python

MY_DEPENDS=	::databases/py-sqlite2 \
		::devel/subversion,-python \
		::textproc/py-docutils \
		::www/clearsilver,python \
		::www/py-genshi

RUN_DEPENDS=	${MY_DEPENDS} \
		::print/enscript

BUILD_DEPENDS=	${MY_DEPENDS}

do-regress:
	@cd ${WRKSRC} && PYTHONPATH=. ${MODPY_BIN} ./trac/test.py

.include <bsd.port.mk>
