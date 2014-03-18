# $Id$
# $OpenBSD: Makefile.template,v 1.67 2013/07/10 15:22:23 bcallah Exp $

COMMENT =		fast and easy-to-use PHP feed parser

V=			1.3.1
DISTNAME =		simplepie-${V}
PKGNAME =		php-${DISTNAME}
CATEGORIES =		www

HOMEPAGE =		http://www.simplepie.org/

MAINTAINER =		Olivier Mehani <shtrom-openbsd@ssji.net>

# BSD
PERMIT_PACKAGE_CDROM =	Yes

MASTER_SITES =		https://github.com/simplepie/simplepie/archive/
DIST_SUBDIR =		${DISTNAME}
DISTFILES =		${V}${EXTRACT_SUFX}

NO_TEST =		Yes
PKG_ARCH =		*


# Although this library is not PEAR, installing it into
# ${PREFIX}/pear/lib will make sure it's picked up by PHP
# without the need to adjust the include path in php.ini
#DOCDIR = 		${PREFIX}/share/doc/${PKGNAME}
#SHAREDIR = 		${PREFIX}/share/php-${MODPHP_VERSION}/SimplePie/
#EXAMPLEDIR = 		${PREFIX}/share/examples/php-${MODPHP_VERSION}/SimplePie/
PREFIX =		${VARBASE}/www
INSTDIR =		${PREFIX}/pear/lib/SimplePie/

SUBST_VARS =		INSTDIR

MODULES =		lang/php 
RUN_DEPENDS =		textproc/libxml \
			lang/php/${MODPHP_VERSION},-curl

do-build:
	cd ${WRKSRC}; php-${MODPHP_VERSION} build/compile.php

do-install:
	${INSTALL_DATA_DIR} ${INSTDIR}
	cp -Rp ${WRKSRC}/library ${INSTDIR}
	cp -Rp ${WRKSRC}/autoloader.php ${INSTDIR}
	cp -Rp ${WRKSRC}/SimplePie.compiled.php ${INSTDIR}/..
	ln -s SimplePie.compiled.php ${INSTDIR}/../simplepie.inc
	chown -R ${SHAREOWN}:${SHAREGRP} ${INSTDIR}
#	${INSTALL_DATA_DIR} ${SHAREDIR}
#	cp -Rp ${WRKSRC}/build ${SHAREDIR}
#	cp -Rp ${WRKSRC}/compatibility_test ${SHAREDIR}
#	cp -Rp ${WRKSRC}/tests ${SHAREDIR}
#	${INSTALL_DATA_DIR} ${DOCDIR}
#	cp -Rp ${WRKSRC}/README.markdown ${DOCDIR}
#	cp -Rp ${WRKSRC}/LICENSE.txt ${DOCDIR}
#	${INSTALL_DATA_DIR} ${EXAMPLEDIR}
#	cp -Rp ${WRKSRC}/demo/* ${EXAMPLEDIR}
#	chown -R ${SHAREOWN}:${SHAREGRP} ${INSTDIR} ${SHAREDIR} ${DOCDIR} ${EXAMPLEDIR}

.include <bsd.port.mk>
