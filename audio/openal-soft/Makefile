# $FreeBSD$

PORTNAME=	openal-soft
PORTVERSION=	1.17.2
PORTREVISION=	1
CATEGORIES=	audio
MASTER_SITES=	http://kcat.strangesoft.net/openal-releases/

MAINTAINER=	mva@FreeBSD.org
COMMENT=	Software implementation of the OpenAL specification

LICENSE=	LGPL20

CONFLICTS=	openal-200[0-9]*

USES=		tar:bzip2 cmake compiler:c11
USE_LDCONFIG=	yes
CMAKE_ARGS+=	-DSHARE_INSTALL_DIR:STRING=${ETCDIR} \
		-DALSOFT_REQUIRE_JACK:BOOL=OFF \
		-DALSOFT_REQUIRE_OSS:BOOL=ON \
		-DALSOFT_REQUIRE_SOLARIS:BOOL=OFF \
		-DALSOFT_REQUIRE_SNDIO:BOOL=OFF \
		-DALSOFT_REQUIRE_QSA:BOOL=OFF \
		-DALSOFT_BACKEND_ALSA:BOOL=OFF \
		-DALSOFT_BACKEND_WAVE:BOOL=ON \
		-DALSOFT_UTILS:BOOL=ON \
		-DALSOFT_EXAMPLES:BOOL=OFF

OPTIONS_DEFINE=		FLUIDSYNTH CONFIG JACK PORTAUDIO PULSEAUDIO SNDIO
OPTIONS_SUB=		yes
CONFIG_DESC=		Install configuration utility (needs Qt 4.x)

#ALSA_CMAKE_ON=		-DALSOFT_REQUIRE_ALSA:BOOL=ON
#ALSA_CMAKE_OFF=		-DALSOFT_BACKEND_ALSA:BOOL=OFF
#ALSA_LIB_DEPENDS=	libasound.so:audio/alsa-lib
CONFIG_CMAKE_ON=	-DALSOFT_NO_CONFIG_UTIL:BOOL=OFF
CONFIG_CMAKE_OFF=	-DALSOFT_NO_CONFIG_UTIL:BOOL=ON
CONFIG_USE=		QT4=corelib,gui,qmake_build,moc_build,rcc_build,uic_build
FLUIDSYNTH_CMAKE_ON=	-DALSOFT_REQUIRE_FLUIDSYNTH:BOOL=ON
FLUIDSYNTH_CMAKE_OFF=	-DALSOFT_MIDI_FLUIDSYNTH:BOOL=OFF
FLUIDSYNTH_LIB_DEPENDS=	libfluidsynth.so:audio/fluidsynth
JACK_CMAKE_ON=		-DALSOFT_REQUIRE_JACK:BOOL=ON
JACK_CMAKE_OFF=		-DALSOFT_BACKEND_JACK:BOOL=OFF
JACK_LIB_DEPENDS=	libjack.so:audio/jack
PORTAUDIO_CMAKE_ON=	-DALSOFT_REQUIRE_PORTAUDIO:BOOL=ON
PORTAUDIO_CMAKE_OFF=	-DALSOFT_BACKEND_PORTAUDIO:BOOL=OFF
PORTAUDIO_LIB_DEPENDS=	libportaudio.so:audio/portaudio
PULSEAUDIO_CMAKE_ON=	-DALSOFT_REQUIRE_PULSEAUDIO:BOOL=ON
PULSEAUDIO_CMAKE_OFF=	-DALSOFT_BACKEND_PULSEAUDIO:BOOL=OFF
PULSEAUDIO_LIB_DEPENDS=	libpulse-simple.so:audio/pulseaudio
SNDIO_CMAKE_ON=		-DALSOFT_REQUIRE_SNDIO:BOOL=ON
SNDIO_CMAKE_OFF=	-DALSOFT_BACKEND_SNDIO:BOOL=OFF
SNDIO_LIB_DEPENDS=	libsndio.so:audio/sndio

post-patch:
	@${REINPLACE_CMD} 's|/etc/openal|${ETCDIR}|' \
		${WRKSRC}/Alc/alcConfig.c
	@${REINPLACE_CMD} 's|$${SHARE_INSTALL_DIR}/openal|${ETCDIR}|' \
		${WRKSRC}/CMakeLists.txt

.include <bsd.port.mk>
