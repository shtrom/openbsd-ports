COMMENT =		daemon to ban hosts causing authentication errors
V =			0.9.3
DISTNAME =		fail2ban-${V}
CATEGORIES =		security
HOMEPAGE =		http://www.fail2ban.org/

MAINTAINER =		Olivier Mehani <shtrom+openbsd@ssji.net>

# GPLv2+
PERMIT_PACKAGE_CDROM =	Yes
PERMIT_PACKAGE_FTP =	Yes
PERMIT_DISTFILES_FTP =	Yes

MASTER_SITES =		https://github.com/fail2ban/fail2ban/archive/
DISTFILES =		${V}${EXTRACT_SUFX}

MODULES =		lang/python
MODPY_SETUPTOOLS =	Yes
MODPY_EGG_VERSION =	${V}
MODPY_ADJ_FILES  =	bin/fail2ban-client \
			bin/fail2ban-regex \
			bin/fail2ban-server \
			bin/fail2ban-testcases \
			fail2ban/tests/files/config/apache-auth/digest.py \
			fail2ban/tests/files/ignorecommand.py

NO_TEST =		Yes

post-install:
	mkdir -p ${WRKINST}${TRUEPREFIX}/share/doc/
	mv ${WRKINST}/usr/share/doc/fail2ban ${WRKINST}${TRUEPREFIX}/share/doc/fail2ban
	rmdir ${WRKINST}/usr/share/doc

	rm -rf ${WRKINST}/var/lib

	rm ${WRKINST}/etc/fail2ban/action.d/*ipf*
	rm ${WRKINST}/etc/fail2ban/action.d/firewallcmd*
	rm ${WRKINST}/etc/fail2ban/action.d/iptables*
	rm ${WRKINST}/etc/fail2ban/action.d/osx*
	rm ${WRKINST}/etc/fail2ban/action.d/route.conf
	rm ${WRKINST}/etc/fail2ban/action.d/shorewall.conf
	rm ${WRKINST}/etc/fail2ban/action.d/symbiosis*
	rm ${WRKINST}/etc/fail2ban/action.d/ufw*
	rm ${WRKINST}/etc/fail2ban/paths-debian.conf
	rm ${WRKINST}/etc/fail2ban/paths-fedora.conf
	rm ${WRKINST}/etc/fail2ban/paths-freebsd.conf
	rm ${WRKINST}/etc/fail2ban/paths-osx.conf
	mkdir -p ${WRKINST}${TRUEPREFIX}/share/fail2ban/
	mv ${WRKINST}/etc/fail2ban ${WRKINST}${TRUEPREFIX}/share/fail2ban/etc
	cp ${FILESDIR}/paths-openbsd.conf ${WRKINST}${TRUEPREFIX}/share/fail2ban/etc
	cp ${WRKSRC}/files/bash-completion ${WRKINST}${TRUEPREFIX}/share/fail2ban/

	mkdir -p ${WRKINST}/etc
	cp ${FILESDIR}/fail2ban.rc ${WRKINST}/etc/rc.d/fail2ban

.include <bsd.port.mk>
