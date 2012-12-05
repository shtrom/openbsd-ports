# $Id$
# Based on [0]
# [0] http://article.gmane.org/gmane.os.openbsd.ports/710

COMMENT=	"Perl module implementing Simple platform independent mailer"

VERSION=	0.79
DISTNAME=	Mail-Sendmail-${VERSION}
PKGNAME=	p5-${DISTNAME}
CATEGORIES=	mail perl5

HOMEPAGE= 	http://alma.ch/perl/mail.htm#Mail::Sendmail
MAINTAINER=	Jim Geovedi <jim@corebsd.or.id>

PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM=	Yes
PERMIT_DISTFILES_FTP=	Yes

MASTER_SITES=	${MASTER_SITE_PERL_CPAN:=Mail/}

CONFIGURE_STYLE=	perl

# Install additional example file
EXAMPLE_LOC=	${PREFIX}/share/examples/p5-Mail-Sendmail

post-install:
	${INSTALL_DATA_DIR} ${EXAMPLE_LOC}
	@perl -pi -e 's,#!perl,#!/usr/bin/perl,g' ${WRKDIST}/test.pl
	${INSTALL_SCRIPT} ${WRKSRC}/test.pl ${EXAMPLE_LOC}/test.pl
	${INSTALL_DATA} ${WRKSRC}/Sendmail.html ${EXAMPLE_LOC}/Sendmail.html

.include <bsd.port.mk>
