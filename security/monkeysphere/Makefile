# New ports collection makefile for:   monkeysphere
# Date created:        2008-09-11 23:38:27-0400
# FreeBSD contributor: Daniel Kahn Gillmor <dkg@fifthhorseman.net>
# OpenBSD port:        Olivier Mehani <shtrom-openbsd@ssji.net>
#
# $FreeBSD: ports/security/monkeysphere/Makefile,v 1.2 2010/09/22 05:21:28 pgollucci Exp $
# $Id$
#

COMMENT=	use the OpenPGP web of trust to verify ssh connections
PORTNAME=	monkeysphere
PORTVERSION=	0.32
DISTNAME=	${PORTNAME}-${PORTVERSION}
PKGNAME=        ${DISTNAME}p1
CATEGORIES=	security
HOMEPAGE=	http://web.monkeysphere.info/
MAINTAINER=	shtrom-openbsd@ssji.net

# GPL
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM=	Yes
PERMIT_DISTFILES_FTP=	Yes

MASTER_SITES=	http://archive.monkeysphere.info/debian/pool/monkeysphere/m/monkeysphere/
# hack for debian orig tarballs
DISTFILES=	${PORTNAME}_${PORTVERSION}.orig.tar.gz

RUN_DEPENDS=	gpg:${PORTSDIR}/security/gnupg1 \
		lockfile:${PORTSDIR}/mail/procmail \
		bash:${PORTSDIR}/shells/bash \
		${SITE_PERL}/${PERL_ARCH}/Crypt/OpenSSL/RSA.pm:${PORTSDIR}/security/p5-Crypt-OpenSSL-RSA \
		${SITE_PERL}/${PERL_ARCH}/Digest/SHA1.pm:${PORTSDIR}/security/p5-Digest-SHA1

MAN1=		monkeysphere.1 openpgp2ssh.1 pem2openpgp.1
MAN7=		monkeysphere.7
MAN8=		monkeysphere-host.8 monkeysphere-authentication.8
MANCOMPRESSED=	yes

USERS=	monkeysphere
GROUPS=	monkeysphere

MAKE_ARGS=	ETCPREFIX=${PREFIX} MANPREFIX=${PREFIX}/man ETCSUFFIX=.sample

# use proper system paths for FreeBSD instead of debian's:
post-patch:
	@${REINPLACE_CMD} -e 's|/etc/monkeysphere|/usr/local/etc/monkeysphere|g' \
	  ${WRKSRC}/src/share/defaultenv \
	  ${WRKSRC}/src/transitions/0.23 \
	  ${WRKSRC}/man/man1/monkeysphere.1 \
	  ${WRKSRC}/man/man8/monkeysphere-authentication.8 \
	  ${WRKSRC}/man/man8/monkeysphere-host.8 \
	  ${WRKSRC}/etc/monkeysphere-authentication.conf
	@${REINPLACE_CMD} -e 's|/var/lib/monkeysphere|/var/monkeysphere|g' \
	  ${WRKSRC}/src/transitions/0.23 \
	  ${WRKSRC}/man/man1/monkeysphere.1 \
	  ${WRKSRC}/man/man8/monkeysphere-authentication.8 \
	  ${WRKSRC}/man/man8/monkeysphere-host.8 \
	  ${WRKSRC}/src/monkeysphere-host \
	  ${WRKSRC}/src/monkeysphere-authentication \
	  ${WRKSRC}/doc/getting-started-admin.mdwn
	@${REINPLACE_CMD} -e 's|/usr/share/monkeysphere|/usr/local/share/monkeysphere|g' \
	  ${WRKSRC}/src/monkeysphere-host \
	  ${WRKSRC}/src/monkeysphere-authentication \
	  ${WRKSRC}/src/monkeysphere
	# and clean up cruft from the sed replacements:
	${FIND} ${WRKSRC} -name '*.bak' -delete

post-install:
	@if [ ! -f ${PREFIX}/etc/monkeysphere/monkeysphere.conf ]; then \
		${CP} -p ${PREFIX}/etc/monkeysphere/monkeysphere.conf.sample ${PREFIX}/etc/monkeysphere/monkeysphere.conf ; \
	fi
	@if [ ! -f ${PREFIX}/etc/monkeysphere/monkeysphere-host.conf ]; then \
		${CP} -p ${PREFIX}/etc/monkeysphere/monkeysphere-host.conf.sample ${PREFIX}/etc/monkeysphere/monkeysphere-host.conf ; \
	fi
	@if [ ! -f ${PREFIX}/etc/monkeysphere/monkeysphere-authentication.conf ]; then \
		${CP} -p ${PREFIX}/etc/monkeysphere/monkeysphere-authentication.conf.sample ${PREFIX}/etc/monkeysphere/monkeysphere-authentication.conf ; \
	fi
.if !defined(PACKAGE_BUILDING)
	@${SETENV} ${SH} ${PKGINSTALL} ${PKGNAME} POST-INSTALL
.endif

post-deinstall:
	@${SETENV} ${SH} ${PKGDEINSTALL} ${PKGNAME} POST-DEINSTALL

.include <bsd.port.mk>
