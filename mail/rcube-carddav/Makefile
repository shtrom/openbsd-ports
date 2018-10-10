# $OpenBSD: Makefile.template,v 1.73 2016/01/11 09:17:22 sthen Exp $
#
COMMENT =	CardDAV adapter for Roundcube
V =		3.0.3
DISTNAME =	rcube-carddav-${V}

GH_ACCOUNT =	blind-coder
GH_PROJECT =	rcmcarddav
GH_TAGNAME =	v${V}
MASTER_SITES =	${MASTER_SITES_GITHUB}

CATEGORIES =	mail

HOMEPAGE =	http://www.benjamin-schieder.de/carddav.html

MAINTAINER =	Olivier Mehani <shtrom+openbsd@ssji.net>

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes

MODULES =	lang/php
BUILD_DEPENDS =	www/composer
RUN_DEPENDS =	mail/roundcubemail

NO_TEST =		Yes
PKG_ARCH =		*

PREFIX =		${VARBASE}/www
INSTDIR =		${PREFIX}/roundcubemail/plugins
SUBST_VARS =		INSTDIR

do-build:
	cd ${WRKDIST}; composer install

do-install:
	${INSTALL_DATA_DIR} ${INSTDIR}
	cp -Rp ${WRKDIST} ${INSTDIR}/carddav

.include <bsd.port.mk>
