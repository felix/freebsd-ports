# Created by: Horia Racoviceanu <horia@racoviceanu.com>
# $FreeBSD: head/databases/galera/Makefile 418767 2016-07-19 11:04:13Z mat $

PORTNAME=	galera
PORTVERSION=	25.3.19
DISTVERSIONPREFIX=	3-
DISTVERSIONSUFFIX=.20161129.65ebc0c
PORTREVISION=	1
CATEGORIES=	databases
MASTER_SITES=	http://www.galeracluster.com/freebsd-beta/

MAINTAINER=	info@galeracluster.com
COMMENT=	Synchronous multi-master replication engine

LICENSE=	GPLv2

LIB_DEPENDS=	libboost_date_time.so:devel/boost-libs
BUILD_DEPENDS=	checkmk:devel/libcheck ${LOCALBASE}/include/boost/shared_ptr.hpp:devel/boost-libs

USES=		execinfo python:build scons shebangfix ssl

USE_GCC=	4.8+
GCC_LIBS=	"${LOCALBASE}/lib/${_GCC_BUILD_DEPENDS}"

USE_LDCONFIG=	yes

LDFLAGS+=	-lboost_program_options -lboost_system
MAKE_ARGS+=	--config=force system_asio=0 -j 4

PLIST_FILES=	lib/libgalera_smm.so

OPTIONS_DEFINE=	DEBUG

.include <bsd.port.pre.mk>

.if ${PORT_OPTIONS:MDEBUG}
MAKE_ARGS+=	debug=3
.endif

do-install:
	${INSTALL_LIB} ${WRKDIR}/${DISTNAME}/libgalera_smm.so \
		${STAGEDIR}${PREFIX}/lib/

.include <bsd.port.post.mk>
