# $OpenBSD: Makefile.template,v 1.73 2016/01/11 09:17:22 sthen Exp $
COMMENT =	Dependency Manager for PHP

P =		composer
V =		1.1.0
DISTNAME =	${P}-${V}
PKGNAME =	php-${DISTNAME}

CATEGORIES =	devel

HOMEPAGE =	https://getcomposer.org/

MAINTAINER =	Olivier Mehani <shtrom-openbsd@ssji.net>

# MIT
PERMIT_PACKAGE_CDROM =	Yes

MASTER_SITES =		${HOMEPAGE}download/
DISTFILES =		${P}-${V}{${V}/${P}}.phar
EXTRACT_ONLY =

MODULES =		lang/php

NO_BUILD =		Yes
NO_TEST =		Yes

do-install:
	mkdir -p ${PREFIX}/bin
	sed -i "s^#!/usr/bin/env php^${TRUEPREFIX}/bin/php-${MODPHP_VERSION}^" \
		${FULLDISTDIR}/${P}-${V}.phar > ${PREFIX}/bin/${P}
	chmod a+x ${PREFIX}/bin/${P}

.include <bsd.port.mk>
