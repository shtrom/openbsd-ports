# $OpenBSD: Makefile.template,v 1.67 2013/07/10 15:22:23 bcallah Exp $

COMMENT =		application for saving web pages and reading them later

V=			2.1.5
DISTNAME =		wallabag-${V}
PKGNAME =		${DISTNAME}
CATEGORIES =		www

HOMEPAGE =		https://www.wallabag.org

MAINTAINER =		Olivier Mehani <shtrom-openbsd@ssji.net>

# MIT
PERMIT_PACKAGE_CDROM =	Yes

GH_ACCOUNT =		wallabag
GH_PROJECT =		wallabag
GH_TAGNAME =		$V
# DIST_SUBDIR =		${DISTNAME}

NO_TEST =		Yes # Disable tests by default as they download more libraries into the package root
PKG_ARCH =		*

PREFIX =		${VARBASE}/www
INSTDIR =		${PREFIX}/wallabag
SUBST_VARS =		INSTDIR V MODPHP_BIN

MODULES =		lang/php
BUILD_DEPENDS =		devel/gmake
TEST_DEPENDS =		devel/apache-ant
RUN_DEPENDS =		textproc/libxml \
			lang/php/${MODPHP_VERSION},-gd \
			lang/php/${MODPHP_VERSION},-tidy \
			lang/php/${MODPHP_VERSION},-curl
do-build:
	perl -pi -e '$$. == 1 && s|^.*env php.*$$|\#!${MODPHP_BIN}|;' \
			-e 'close ARGV if eof;' \
			$$(grep -IR '[e]nv php' ${WRKSRC}/ | sed s/:.*//)
	# Avoid interactive configuration
	cp ${WRKSRC}/app/config/parameters.yml.dist ${WRKSRC}/app/config/parameters.yml
	cd ${WRKSRC}; SYMFONY_ENV=prod composer install --no-dev -o --prefer-dist
	rm ${WRKSRC}/app/config/parameters.yml
	rm ${WRKSRC}/data/db/wallabag.sqlite
	perl -pi -e '$$. == 1 && s|^.*env php.*$$|\#!${MODPHP_BIN}|;' \
			-e 'close ARGV if eof;' \
			$$(grep -IR '[e]nv php' ${WRKSRC}/vendor | sed s/:.*//)

do-test:
	cp ${WRKSRC}/app/config/parameters.yml.dist ${WRKSRC}/app/config/parameters.yml
	cd ${WRKSRC}; gmake test
	rm ${WRKSRC}/app/config/parameters.yml

do-install:
	cp -Rp ${WRKSRC} ${INSTDIR}
	rm -rf \
		${INSTDIR}/docker \
		${INSTDIR}/docs \
		${INSTDIR}/tests
	${INSTALL_DATA_DIR} ${PREFIX}/conf/modules.sample/
	${INSTALL_DATA} ${FILESDIR}/wallabag.conf \
		${PREFIX}/conf/modules.sample/wallabag.conf.dist
	find ${INSTDIR} \( \
		-name '*.orig' \
		-o -name .gitignore \
		-o -name .gitkeep \
		\) -exec rm {} \;
	chown -R ${SHAREOWN}:${SHAREGRP} ${INSTDIR}
	chown -R www:www \
		${INSTDIR}/app/config \
		${INSTDIR}/bin \
		${INSTDIR}/data/ \
		${INSTDIR}/var \
		${INSTDIR}/vendor

.include <bsd.port.mk>
