# $OpenBSD: Makefile,v 1.6 2017/05/24 07:50:25 benoit Exp $

COMMENT =	client library for the Fast CGI protocol

MODULES =	cpan
PKG_ARCH =	*
DISTNAME =	FCGI-Client-0.09
CATEGORIES =	devel

MAINTAINER =	Olivier Mehani <shtrom+openbsd@ssji.net>

CONFIGURE_STYLE =	modbuild

BUILD_DEPENDS = devel/p5-Module-Build-Tiny

RUN_DEPENDS = devel/p5-Type-Tiny \
	      devel/p5-Moo

# Perl
PERMIT_PACKAGE_CDROM =	Yes

.include <bsd.port.mk>
