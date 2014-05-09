# $OpenBSD: Makefile.template,v 1.67 2013/07/10 15:22:23 bcallah Exp $
# $FreeBSD/NetBSD: credit FreeBSD/NetBSD if thats where the port came from $
# $Id$

COMMENT =		Jappix addon for Roundcube

V =			0.2.4
P = 			jappix4roundcube
DISTNAME =		rcube-${P}-${V}
CATEGORIES =		mail

HOMEPAGE =		https://code.google.com/p/jappix4roundcube/

MAINTAINER =		Olivier Mehani <shtrom+openbsd@ssji.net>

# Apache License 2.0
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_FTP =	Yes

MASTER_SITES =		https://${P}.googlecode.com/files/
DISTFILES =		${P}-plugin-jappixembedded-v${V}.tar

RUN_DEPENDS =		mail/roundcubemail

NO_BUILD =		Yes
NO_TEST =		Yes
PKG_ARCH =		*

PREFIX=        		${VARBASE}/www
INSTDIR=       		${PREFIX}/roundcubemail/plugins/
SUBST_VARS =		INSTDIR

post-extract:
	mkdir -p ${WRKSRC}
	# fails when trying to move $WRKSRC into itself
	-mv ${WRKDIR}/* ${WRKSRC}/
	mv ${WRKSRC}/systrace.policy ${WRKDIR}

do-install:
	${INSTALL_DATA_DIR} ${INSTDIR}
	cp -Rp ${WRKSRC} ${INSTDIR}/${P}

.include <bsd.port.mk>
