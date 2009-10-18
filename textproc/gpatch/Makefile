# $OpenBSD: Makefile,v 1.12 2007/09/15 20:59:38 merdely Exp $

COMMENT=	GNU versions of the patch utility

VERSION=	2.5.9
DISTNAME=	patch-${VERSION}
PKGNAME=	gpatch-${VERSION}p0
CATEGORIES=	textproc
HOMEPAGE=	http://www.gnu.org/software/patch/

# GPL
PERMIT_PACKAGE_FTP=	Yes
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_DISTFILES_FTP=	Yes
PERMIT_DISTFILES_CDROM=	Yes
WANTLIB=		c 

MASTER_SITES=	${MASTER_SITE_GNU:=patch/}

MODULES=	devel/gettext

SEPARATE_BUILD=	simple
CONFIGURE_STYLE=gnu
CONFIGURE_ARGS=	--program-prefix=g
CONFIGURE_ENV=	CPPFLAGS="-I${LOCALBASE}/include" \
		LDFLAGS="-L${LOCALBASE}/lib"

.include <bsd.port.mk>
