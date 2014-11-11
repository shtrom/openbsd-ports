# $Id$
# $OpenBSD: Makefile.template,v 1.67 2013/07/10 15:22:23 bcallah Exp $

COMMENT =		application for saving web pages and reading them later

V=			1.8.0
DISTNAME =		wallabag-${V}
PKGNAME =		${DISTNAME}
CATEGORIES =		www

HOMEPAGE =		https://www.wallabag.org

MAINTAINER =		Olivier Mehani <shtrom-openbsd@ssji.net>

# WTFPL
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_FTP =	Yes

MASTER_SITES0 =		https://github.com/wallabag/wallabag/archive/
MASTER_SITES1 =		http://static.wallabag.org/files/
DIST_SUBDIR =		${DISTNAME}
DISTFILES =		${V}${EXTRACT_SUFX}:0 vendor.zip:1

NO_BUILD =		Yes
NO_TEST =		Yes
PKG_ARCH =		*

PREFIX =		${VARBASE}/www
INSTDIR =		${PREFIX}/wallabag
SUBST_VARS =		INSTDIR V

MODULES =		lang/php 
RUN_DEPENDS =		textproc/libxml \
			lang/php/${MODPHP_VERSION},-tidy \
			lang/php/${MODPHP_VERSION},-curl

do-install:
	mkdir -p ${INSTDIR}
	cp -Rp ${WRKSRC}/* ${INSTDIR}
	cp -Rp ${WRKSRC}/../vendor ${INSTDIR}
	${INSTALL_DATA_DIR} ${PREFIX}/conf/modules.sample/
	${INSTALL_DATA} ${FILESDIR}/wallabag.conf ${PREFIX}/conf/modules.sample/wallabag.conf.dist
	find ${INSTDIR} -name .gitignore -exec rm {} \;
	find ${INSTDIR} -name .htaccess -exec mv {} {}.dist \;
	chown -R ${SHAREOWN}:${SHAREGRP} ${INSTDIR}
	chown www:www ${INSTDIR}/db
	chown www:www ${INSTDIR}/cache
	# XXX
	chown www:www ${INSTDIR}/inc/3rdparty/htmlpurifier/HTMLPurifier/DefinitionCache/Serializer

.include <bsd.port.mk>
