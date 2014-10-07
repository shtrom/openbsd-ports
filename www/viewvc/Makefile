# $OpenBSD: Makefile.template,v 1.68 2013/10/02 07:34:45 ajacoutot Exp $
# $Id$ 
# Original from: Olivier Mehani <shtrom-openbsd@ssji.net>

COMMENT =		browser interface for CVS and Subversion version control repositories

DISTNAME =		viewvc-1.1.22

CATEGORIES =		www devel

HOMEPAGE =		http://www.viewvc.org

MAINTAINER =		Olivier Mehani <shtrom-openbsd@ssji.net>

# 2-clause BSD
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_FTP =	Yes

MASTER_SITES =		http://www.viewvc.org/

BUILD_DEPENDS =	???
RUN_DEPENDS =		devel/python>=2

NO_BUILD =		Yes
NO_TEST =		Yes

PKG_ARCH =		*

PREFIX =		${VARBASE}/www
INSTDIR =		${PREFIX}/viewvc
SUBST_VARS =		INSTDIR

do-install:
	${INSTALL_DATA_DIR} ${INSTDIR}
	cp -Rp ${WRKSRC}/* ${INSTDIR}
	chown -R ${SHAREOWN}:${SHAREGRP} ${INSTDIR}

.include <bsd.port.mk>
