# Created by: Alexey A.Ukhov <auk@startext.de>
# $FreeBSD: head/www/mod_chroot/Makefile 386734 2015-05-19 02:12:57Z amdmi3 $

COMMENT=	module to run Apache2 in a chroot

P=		mod_chroot
V=		0.5
DISTNAME=	${P}-${V}
PKGNAME=	ap2-${DISTNAME}
MODNAME=	${P}
CATEGORIES=	www net

MASTER_SITES=	http://core.segfault.pl/~hobbit/mod_chroot/dist/

MAINTAINER=	shtrom+openbsd@ssji.net

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes

RUN_DEPENDS=	www/apache-httpd
BUILD_DEPENDS=	${RUN_DEPENDS}

AP_FAST_BUILD=	yes

DOCSDIR=	${PREFIX}/share/doc/${P}
PORTDOCS=	INSTALL CAVEATS README.Apache20 README

do-build:
	cd ${WRKSRC} && ${LOCALBASE}/sbin/apxs2 -c -o ${MODNAME}.la ${MODNAME}.c

do-install:
	install -d -m 755 ${PREFIX}/lib/apache2
	${LOCALBASE}/sbin/apxs2 -S LIBEXECDIR=${PREFIX}/lib/apache2 -i -n ${MODNAME} ${WRKSRC}/${MODNAME}.la

post-install:
	install -d -m 755 ${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S|^|${WRKSRC}/|} ${DOCSDIR}

.include <bsd.port.mk>
