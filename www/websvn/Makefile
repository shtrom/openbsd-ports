# $OpenBSD: Makefile.template,v 1.68 2013/10/02 07:34:45 ajacoutot Exp $
# $Id$
# Original from: Olivier Mehani <shtrom-openbsd@ssji.net>

COMMENT =		offers a Web view onto subversion repositories

DISTNAME =		websvn-2.3.3
CATEGORIES =		www devel

HOMEPAGE =		http://www.websvn.info

MAINTAINER =		Olivier Mehani <shtrom-openbsd@ssji.net>

# GPL-2+
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_FTP =	Yes

MASTER_SITES =		http://websvn.tigris.org/files/documents/1380/49056/
EXTRACT_SUFX =		.tar.gz

MODULES =		lang/php
RUN_DEPENDS =		devel/subversion>=1.4

NO_BUILD =		Yes
NO_TEST =		Yes

PKG_ARCH =		*

PREFIX =		${VARBASE}/www
INSTDIR =		${PREFIX}/websvn
SUBST_VARS =		INSTDIR

do-install:
	${INSTALL_DATA_DIR} ${INSTDIR}
	cp -Rp ${WRKSRC}/* ${INSTDIR}
	${INSTALL_DATA_DIR} ${PREFIX}/conf/modules.sample/
	${INSTALL_DATA} ${FILESDIR}/websvn.conf ${PREFIX}/conf/modules.sample/websvn.conf.dist
	mv ${INSTDIR}/include/distconfig.php  ${INSTDIR}/include/config.php.dist
	chown -R ${SHAREOWN}:${SHAREGRP} ${INSTDIR}

.include <bsd.port.mk>
