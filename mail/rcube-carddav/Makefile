COMMENT =	CardDAV adapter for Roundcube
V =		1.0.0
P =		carddav
DISTNAME =	rcube-${P}-${V}

GH_ACCOUNT =	blind-coder
GH_PROJECT =	rcmcarddav
GH_TAGNAME =	carddav_${V}

CATEGORIES =	mail

HOMEPAGE =	http://www.benjamin-schieder.de/carddav.html

MAINTAINER =	Olivier Mehani <shtrom+openbsd@ssji.net>

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_FTP =	Yes

RUN_DEPENDS =		mail/roundcubemail

NO_BUILD =		Yes
NO_TEST =		Yes
PKG_ARCH =		*

PREFIX=        		${VARBASE}/www
INSTDIR=       		${PREFIX}/roundcubemail/plugins
SUBST_VARS =		INSTDIR

do-install:
	${INSTALL_DATA_DIR} ${INSTDIR}
	cp -Rp ${WRKDIST} ${INSTDIR}/carddav
	mv ${INSTDIR}/carddav/config.inc.php.dist ${INSTDIR}/carddav/config.inc.php

.include <bsd.port.mk>
