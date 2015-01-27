# $OpenBSD: Makefile.template,v 1.68 2013/10/02 07:34:45 ajacoutot Exp $

COMMENT =		self-hosted media publishing platform
VERSION = 0.7.1
DISTNAME =		mediagoblin-${VERSION}
CATEGORIES =		www

HOMEPAGE =		http://mediagoblin.org/

MAINTAINER =		Olivier Mehani <shtrom+openbsd@ssji.net>

# AGPLv3+
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_FTP =	Yes

MASTER_SITES =		https://gitorious.org/mediagoblin/mediagoblin/archive/
DISTFILES =		v${VERSION}.tar.gz

MODULES =		lang/python
MODPY_SETUPTOOLS =	Yes
BUILD_DEPENDS =		devel/py-virtualenv
RUN_DEPENDS =		graphics/py-Imaging		\
			textproc/py-lxml

# www/py-paste			\
# www/py-pastescript		\
# databases/py-sqlalchemy-migrate \
# devel/py-mock			\
# graphics/py-ExifRead

#TEST_DEPENDS =		???

#NO_BUILD =		Yes

WRKDIST =		${WRKDIR}/mediagoblin-mediagoblin

INSTDIR =		${PREFIX}/share/mediagoblin
SUBST_VARS =		INSTDIR VERSION

do-build:
	cd ${WRKSRC}; virtualenv .
	cd ${WRKSRC}; ./bin/python ./setup.py develop

do-install:
	mkdir -p ${INSTDIR}
	cp -Rp ${WRKSRC}/* ${INSTDIR}
	ln -s ../share/mediagoblin/bin/gmg ${PREFIX}/bin/gmg
	install -m 644 files/nginx.mediagoblin.conf ${INSTDIR}/
	install -m 755 -d ${WRKINST}/var/mediagoblin

do-test:
	cd ${WRKSRC} && sh ./run_tests.sh


.include <bsd.port.mk>
