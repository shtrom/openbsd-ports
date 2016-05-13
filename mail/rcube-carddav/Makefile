# $OpenBSD: Makefile.template,v 1.73 2016/01/11 09:17:22 sthen Exp $
#
COMMENT =	CardDAV adapter for Roundcube
V =		1.0.0
DISTNAME =	rcube-carddav-${V}

GH_ACCOUNT =	blind-coder
GH_PROJECT =	rcmcarddav
GH_TAGNAME =	carddav_${V}

CATEGORIES =	mail

HOMEPAGE =	http://www.benjamin-schieder.de/carddav.html

MAINTAINER =	Olivier Mehani <shtrom+openbsd@ssji.net>

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes

RUN_DEPENDS =		mail/roundcubemail

NO_BUILD =		Yes
NO_TEST =		Yes
PKG_ARCH =		*

PREFIX =		${VARBASE}/www
INSTDIR =		${PREFIX}/roundcubemail/plugins
SUBST_VARS =		INSTDIR

do-install:
	${INSTALL_DATA_DIR} ${INSTDIR}
	cp -Rp ${WRKDIST} ${INSTDIR}/carddav

.include <bsd.port.mk>
