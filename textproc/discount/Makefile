# $OpenBSD: Makefile,v 1.7 2014/11/01 11:06:55 jca Exp $

COMMENT =		fast C implementation of Markdown

DISTNAME =		discount-2.1.6
EXTRACT_SUFX =		.tar.bz2

CATEGORIES =		textproc

HOMEPAGE =		http://www.pell.portland.or.us/~orc/Code/markdown/

MAINTAINER =		Scott Vokes <vokes.s@gmail.com>

# BSD
PERMIT_PACKAGE_CDROM =	Yes

FLAVORS=	static
FLAVOR?=

.if ${FLAVOR:Mstatic}
STATIC=	-static
CONFIGURE_ENV+=	SHLIBEXT=""
.else
CONFIGURE_ARGS +=	${CONFIGURE_SHARED}
WANTLIB=	c
.endif

MASTER_SITES =		http://www.pell.portland.or.us/~orc/Code/discount/

CONFIGURE_STYLE =	simple
CONFIGURE_SCRIPT =	configure.sh

INSTALL_TARGET =	install.everything
#TEST_TARGET =		test

pre-configure:
	@perl -pi -e 's,\./markdown,\./discount,' ${WRKSRC}/tests/*

pre-build:
	@perl -pi -e 's,^LFLAGS.*,$$& ${STATIC},' ${WRKSRC}/Makefile

.include <bsd.port.mk>
