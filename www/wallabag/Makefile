# $Id$
# $OpenBSD: Makefile.template,v 1.67 2013/07/10 15:22:23 bcallah Exp $

COMMENT =		application for saving web pages and reading them later

V=			1.5.2
DISTNAME =		wallabag-${V}
CATEGORIES =		www

HOMEPAGE =		https://www.wallabag.org

MAINTAINER =		Olivier Mehani <shtrom-openbsd@ssji.net>

# WTFPL
PERMIT_PACKAGE_CDROM =	Yes

MASTER_SITES =		https://github.com/wallabag/wallabag/archive/
DIST_SUBDIR =		${DISTNAME}
DISTFILES =		${V}${EXTRACT_SUFX}

NO_BUILD =		Yes
NO_TEST =		Yes
PKG_ARCH =		*

PREFIX =		${VARBASE}/www
INSTDIR =		${PREFIX}/wallabag
SUBST_VARS =		INSTDIR

MODULES =		lang/php 
RUN_DEPENDS =		textproc/libxml \
			lang/php/${MODPHP_VERSION},-tidy \
			lang/php/${MODPHP_VERSION},-curl \
			lang/php/${MODPHP_VERSION},-sqlite

do-install:
	${INSTALL_DATA_DIR} ${INSTDIR}
	cp -Rp ${WRKSRC}/* ${INSTDIR}
	find ${INSTDIR} -name .gitignore -exec rm {} \;
	find ${INSTDIR} -name .htaccess -exec mv {} {}.dist \;
	chown -R ${SHAREOWN}:${SHAREGRP} ${INSTDIR}
	chown www:www ${INSTDIR}/db
	chown www:www ${INSTDIR}/cache

.include <bsd.port.mk>
