# $OpenBSD: Makefile,v 1.61 2015/03/31 14:32:32 gonzalo Exp $

COMMENT =	standard compliant weblog

DISTNAME =	wordpress-5.2.2
CATEGORIES =	www

HOMEPAGE =	http://wordpress.org/
MAINTAINER =	Olivier Mehani <shtrom+openbsd@ssji.net>

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes

MASTER_SITES =	${HOMEPAGE}

MODULES =	lang/php

RUN_DEPENDS =	lang/php/${MODPHP_VERSION},-mysqli

NO_BUILD =	Yes
NO_TEST =	Yes
PKG_ARCH =	*

PREFIX =	${VARBASE}/www
INSTDIR =	${PREFIX}/wordpress
WRKDIST =	${WRKDIR}/wordpress

SUBST_VARS =	INSTDIR

do-install:
	${INSTALL_DATA_DIR} ${PREFIX}/wordpress
	cd ${WRKSRC} && pax -rw * ${PREFIX}/wordpress

.include <bsd.port.mk>
