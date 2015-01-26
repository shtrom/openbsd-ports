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

# "make port-lib-depends-check" can help
#WANTLIB =		???

# where the source files and patches can be fetched
#
MASTER_SITES =		https://gitorious.org/mediagoblin/mediagoblin/archive/
DISTFILES =		v${VERSION}.tar.gz

MODULES =		lang/python
MODPY_SETUPTOOLS =	Yes
# BUILD_DEPENDS =		py-virtualenv
RUN_DEPENDS =		graphics/py-Imaging	\
			textproc/py-lxml

#TEST_DEPENDS =		???

# Is the build automagic or is it interactive
#
#IS_INTERACTIVE =		Yes
#TEST_IS_INTERACTIVE =		Yes

#NO_BUILD =		Yes
#NO_TEST =		Yes

# Overrides for default values
#
#CFLAGS =		???
#LDFLAGS =		???
#MAKE_FILE =		???
#PKG_ARCH =		??? (* for arch-independent packages)
WRKDIST =		${WRKDIR}/mediagoblin-mediagoblin
#WRKSRC =		??? if other than ${WRKDIST}
#WRKBUILD =		??? if other than ${WRKSRC}
#WRKCONF =		??? if other than ${WRKBUILD}

#ALL_TARGET =		???
#INSTALL_TARGET =	???
#TEST_TARGET =		???

post-install:
	rm ${PREFIX}/bin/pybabel

do-test:
	cd ${WRKSRC} && sh ./run_tests.sh


.include <bsd.port.mk>
