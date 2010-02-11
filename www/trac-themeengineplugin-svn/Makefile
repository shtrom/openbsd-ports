# $OpenBSD: Makefile,v 1.4 2009/02/18 14:06:45 sthen Exp $

COMMENT=		theme plugin for trac

V=			7530
EXTRACT_SUFX=		.zip
# Download from http://trac-hacks.org/wiki/ThemeEnginePlugin#DownloadandSource
DISTNAME=		themeengineplugin-r${V}
PKGNAME=		trac-themeengineplugin-svn-${V}p0
CATEGORIES=		www devel

MAINTAINER=		Olivier Mehani <shtrom-openbsd@ssji.net>

HOMEPAGE=		http://trac-hacks.org/wiki/ThemeEnginePlugin

FETCH_MANUALLY=		Yes

# BSD
PERMIT_PACKAGE_CDROM=   Yes
PERMIT_PACKAGE_FTP=     Yes
PERMIT_DISTFILES_CDROM= Yes
PERMIT_DISTFILES_FTP=   Yes

RUN_DEPENDS=		::www/trac

BUILD_DEPENDS=		::devel/py-setuptools \
			::lang/python/2.4

NO_REGRESS=		Yes
WRKDIST=		${WRKDIR}/themeengineplugin/0.11/

MODULES=		lang/python

MODPY_SETUPTOOLS=	Yes

post-extract: 
	find ${WRKDIST} -type f -exec chmod a+r {} \;
	find ${WRKDIST} -type f -name \*.py -exec chmod a+x {} \;

.include <bsd.port.mk>
