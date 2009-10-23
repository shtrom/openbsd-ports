

COMMENT =		patch management scripts

VERSION=		0.48
DISTNAME =		quilt-${VERSION}
PKGNAME =		${DISTNAME}p0
CATEGORIES =		textproc
HOMEPAGE =		http://savannah.nongnu.org/projects/quilt/
MAINTAINER =		Olivier Mehani <shtrom-openbsd@ssji.net>

# GPL
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_CDROM =Yes
PERMIT_DISTFILES_FTP =	Yes

MASTER_SITES =		${MASTER_SITE_SAVANNAH:=quilt/}

WANTLIB += c
MODULES =		devel/gettext
BUILD_DEPENDS =         ::misc/findutils
RUN_DEPENDS =           ::misc/fileutils ::textproc/gdiff ::textproc/gpatch \
			::archivers/bzip2 ::sysutils/ggrep ::textproc/gsed \
			::devel/p5-Time-TimeDate

USE_GMAKE =		Yes
CONFIGURE_STYLE =	gnu
CONFIGURE_ARGS +=	${CONFIGURE_SHARED} \
			--without-date \
			--without-getopt \
			--with-diff=/usr/local/bin/gdiff \
			--with-find=/usr/local/bin/gfind \
			--with-patch=/usr/local/bin/gpatch \
			--with-sed=/usr/local/bin/gsed
CONFIGURE_ENV =		CPPFLAGS="-I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib"
# Do not use config.site as it makes detection of fileutils fail
CONFIG_SITE =

.include <bsd.port.mk>
