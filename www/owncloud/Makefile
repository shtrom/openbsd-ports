# $Id$

COMMENT =		self-hosted, location independent cloud storage engine

DISTNAME =		owncloud-4.5.0
REVISION =		2
CATEGORIES =		www lang/php
HOMEPAGE =		http://owncloud.org/

MAINTAINER =		Olivier Mehani <shtrom-openbsd@ssji.net>

# AGPLv3
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

MASTER_SITES =		http://mirrors.owncloud.org/releases/
EXTRACT_SUFX =		.tar.bz2

NO_BUILD =	Yes
NO_REGRESS =	Yes
PKG_ARCH =	*

PREFIX =		/var/www
INSTDIR =	${PREFIX}/owncloud

MODULES =		lang/php # Defaults to 5.3 at the time of this writing
RUN_DEPENDS =		lang/php/${MODPHP_VERSION},-curl \
			lang/php/${MODPHP_VERSION},-gd \
			lang/php/${MODPHP_VERSION},-xmlrpc \
			lang/php/${MODPHP_VERSION},-zip

# Put source in the expected place, and use absolute path to php binary (stolen
# and adapted from mail/roundcubemail)
do-configure:
	mv ${WRKDIR}/owncloud/* ${WRKSRC}/
	find ${WRKSRC} -type f -exec perl -pi \
		-e '$$. == 1 && s,^#!.*env.*php.*,#!${MODPHP_BIN},;' \
		-e 'close ARGV if eof;' {} \;

do-install:
	cp -Rp ${WRKSRC} ${INSTDIR}
	${INSTALL_DATA_DIR} ${PREFIX}/conf/modules.sample
	${INSTALL_DATA} ${FILESDIR}/owncloud.conf \
		${PREFIX}/conf/modules.sample/owncloud.conf.dist
	mv ${INSTDIR}/config/config.sample.php ${INSTDIR}/config/config.php.dist
	perl -pi -e 's,/var/www/owncloud,/owncloud,g;' \
		-e 's/"appstoreenabled" =>.*/"appstoreenabled" => false,/;' \
		-e 's/"loglevel" =>.*/"loglevel" => "2",/;' \
		${INSTDIR}/config/config.php.dist

.include <bsd.port.mk>
