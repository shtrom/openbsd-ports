# $OpenBSD: Makefile,v 1.106.2.3 2016/12/15 09:42:01 ajacoutot Exp $

COMMENT=		easy and universal access to shared and/or personal files

V=			9.0.4
DISTNAME=		nextcloud-${V}

CATEGORIES=		www

HOMEPAGE=		http://nextcloud.org/

MAINTAINER=		Olivier Mehani <shtrom+openbsd@sji.net>

# AGPLv3 (GNU Affero Public License)
# jQuery: MIT / GPLv3
# HTTP: 3 clause BSD
# MDB2: BSD-like
# User: AGPL
# XML/RPC: MIT / PHP
# Silk icons: Creative Commons Attribution
PERMIT_PACKAGE_CDROM=	Yes

GH_ACCOUNT =		nextcloud
GH_PROJECT =		server
GH_TAGNAME =		v$V

MODULES=		lang/php

NO_BUILD=		Yes
NO_TEST=		Yes
PKG_ARCH=		*

WRKDIST=		${WRKDIR}/nextcloud

PREFIX=			${VARBASE}/www
INSTDIR=		${PREFIX}/nextcloud
TINSTDIR=		${TRUEPREFIX}/nextcloud
VR=			${V:R}
SUBST_VARS=		INSTDIR TINSTDIR MODPHP_BIN VR

RUN_DEPENDS=		lang/php/${MODPHP_VERSION},-gd \
			lang/php/${MODPHP_VERSION},-zip

# http user authentication
RUN_DEPENDS +=		lang/php/${MODPHP_VERSION},-curl

# apps extraction
RUN_DEPENDS +=		lang/php/${MODPHP_VERSION},-bz2

# sorting of non-ASCII characters
RUN_DEPENDS +=		lang/php/${MODPHP_VERSION},-intl

# increase file encryption performance
RUN_DEPENDS +=		lang/php/${MODPHP_VERSION},-mcrypt

# distributed caching and Transactional File Locking
RUN_DEPENDS +=		databases/pecl-redis

do-install:
	cp -Rp ${WRKSRC} ${INSTDIR}
	mv ${INSTDIR}/.htaccess ${INSTDIR}/.htaccess.dist
	find ${INSTDIR} -name '*.orig' -print0 | xargs -r0 rm
	chown -R ${BINOWN}:${BINGRP} ${INSTDIR}

	chmod +x ${INSTDIR}/occ
	perl -pi -e '$$. == 1 && s|^.*env php.*$$|\#!${MODPHP_BIN}|;' \
		-e 'close ARGV if eof;' \
		${INSTDIR}/occ

	${INSTALL_DATA_DIR} ${PREFIX}/conf/modules.sample
	${SUBST_CMD} -m 0644 -c ${FILESDIR}/httpd-nextcloud.conf.dist.in \
		${PREFIX}/conf/modules.sample/httpd-nextcloud.conf.dist

.include <bsd.port.mk>
