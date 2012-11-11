# $RuOBSD: Makefile,v 1.6 2011/08/03 08:31:36 dinar Exp $

PKGNAME=	ikiwiki-${VERSION}
VERSION=	3.20121017
CATEGORIES=	www
MASTER_SITES=	${MASTER_SITE_DEBIAN_POOL} \
		ftp://ftp.de.debian.org/debian/pool/main/i/ikiwiki/ \
		ftp://ftp.freebsd.org/pub/FreeBSD/ports/distfiles/
		
DISTNAME=	ikiwiki_${VERSION}

MAINTAINER=	dinar@yantel.ru
COMMENT=	A wiki compiler

BUILD_DEPENDS= www/p5-HTML-Parser \
               devel/p5-Locale-gettext \
               www/p5-CGI-FormBuilder \
               www/p5-CGI-Session \
               devel/p5-Time-TimeDate \
               www/p5-HTML-Scrubber \
               www/p5-HTML-Template \
               textproc/p5-Text-Markdown \
               www/p5-URI \
               textproc/p5-XML-Simple \
               devel/p5-YAML-XS
#               mail/p5-Mail-Sendmail \
#               converters/p5-Encode \
#
RUN_DEPENDS=   devel/p5-File-MimeInfo \
               net/p5-RPC-XML \
               www/p5-XML-Feed \
               security/p5-Authen-Passphrase \
               devel/p5-File-chdir \
               devel/p5-File-ReadBackwards \
               devel/cvsps \
               devel/p5-Scalar-List-Utils \
               www/p5-HTML-Tree \
               lang/python/2.6

# Dependencies according to [0]
# [0] http://ikiwiki.info/install/
#BUILD_DEPENDS=	p5-Text-Markdown \
#		p5-URI \
#		www/p5-HTML-Parser \
#		p5-HTML-Template \
#		p5-YAML-XS \
#		p5-HTML-Scrubber
#RUN_DEPENDS=	${BUILD_DEPENDS}

WRKDIST=	${WRKDIR}/ikiwiki

# GPL
PERMIT_PACKAGE_CDROM=	Yes
PERMIT_PACKAGE_FTP=	Yes
PERMIT_DISTFILES_CDROM=	Yes
PERMIT_DISTFILES_FTP=	Yes

CONFIGURE_STYLE=	perl
USE_GMAKE=	yes
USE_GETTEXT=	yes

FLAVORS =		search
FLAVOR ?=

.if ${FLAVOR:L:Msearch}
RUN_DEPENDS+=	security/p5-Digest-SHA1 \
		databases/p5-Search-Xapian \
		www/xapian-omega
.endif



.include <bsd.port.mk>
