# $OpenBSD: Makefile.template,v 1.68 2013/10/02 07:34:45 ajacoutot Exp $

COMMENT =		self-hosted media publishing platform
VERSION =		0.7.1
DISTNAME =		mediagoblin-${VERSION}
CATEGORIES =		www

HOMEPAGE =		http://mediagoblin.org/

MAINTAINER =		Olivier Mehani <shtrom+openbsd@ssji.net>

# AGPLv3+
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_FTP =	Yes

# XXX: A bit later than the git module, but can't hurt
PDFJSVER =		0.8.1181
PDFJSDIR =		pdf.js-${PDFJSVER}
SKELETONVER =		1.2
SKELETONDIR =		Skeleton-${SKELETONVER}
SPEEDBOATREV =		8873d9b559a4c5b3bb90997227d5455f8730fd48
SPEEDBOATDIR =		sandyseventiesspeedboat-mg-${SPEEDBOATREV}

MASTER_SITES0 =		https://gitorious.org/mediagoblin/mediagoblin/archive/
MASTER_SITES1 =		https://github.com/mozilla/pdf.js/archive/
MASTER_SITES2 =		https://github.com/dhg/Skeleton/archive/
MASTER_SITES3 =		https://github.com/jpope777/sandyseventiesspeedboat-mg/archive/
DISTFILES =		v${VERSION}.tar.gz:0 \
			v${PDFJSVER}.tar.gz:1 \
			v${SKELETONVER}.tar.gz:2 \
			${SPEEDBOATREV}.tar.gz:3

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
	cd ${WRKSRC}; virtualenv --no-site-packages .
	cd ${WRKSRC}; ./bin/python ./setup.py develop

do-install:
	mkdir -p ${INSTDIR}
	cp -Rp ${WRKSRC}/* ${INSTDIR}
	cp -Rp ${WRKDIR}/${PDFJSDIR}/* ${INSTDIR}/extlib/pdf.js/
	cp -Rp ${WRKDIR}/${SKELETONDIR}/* ${INSTDIR}/extlib/skeleton/
	cp -Rp ${WRKDIR}/${SPEEDBOATDIR}/* ${INSTDIR}/extlib/sandyseventiesspeedboat/
	ln -s ../share/mediagoblin/bin/gmg ${PREFIX}/bin/gmg
	install -m 644 files/nginx.mediagoblin.conf ${INSTDIR}/
	install -m 755 -d ${WRKINST}/var/mediagoblin

do-test:
	cd ${WRKSRC} && sh ./run_tests.sh


.include <bsd.port.mk>
