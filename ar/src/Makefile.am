# Source Path

AM_CFLAGS =             -Wundef \
                        -Wstrict-prototypes \
                        -Wno-trigraphs \
                        -g -O0 \
                        -fno-inline \
                        -fno-short-enums \
                        -DMSM8960_ALSA \
                        -fpic \
                        -I ${top_srcdir}/ar/inc

AM_CFLAGS += @AGM_CFLAGS@
AM_CFLAGS += @MMHEADERS_CFLAGS@
AM_CFLAGS += @DIAG_CFLAGS@
AM_CFLAGS += @GLIB_CFLAGS@
AM_CFLAGS += @TINYALSA_CFLAGS@

audftm_c_sources =      DALSYS_common.c \
                        audio_ftm_afe_loopback.c \
                        audio_ftm_driver_fwk.c \
                        audio_ftm_dtmf_basic_op.c \
                        audio_ftm_dtmf_tone_gen.c \
                        audio_ftm_hw_drv_ar.c \
                        audio_ftm_pcm_loopback.c \
                        audio_ftm_pcm_record.c \
                        audio_ftm_tone_play.c \
                        audio_ftm_util_fifo.c \
                        ftm_audio_dispatch_ar.c \
                        ftm_audio_main.c \
                        audio_ftm_diag_mem.c \
                        audio_ftm_pcm_play.c \
                        audio_ftm_ext_loopback.c \
                        fft.c

bin_PROGRAMS = mm_audio_ftm
mm_audio_ftm_SOURCES = $(audftm_c_sources)
mm_audio_ftm_CFLAGS = $(AM_CFLAGS) -DTINYALSA_LIB -DUSE_GLIB -DQC_MODIFIED -DFEATURE_EXPORT_SND -DFEATURE_AUDIO_AGC -DFEATURE_VOC_PCM_INTERFACE -DFEATURE_VOICE_PLAYBACK -DFEATURE_VOICE_RECORD -DVERBOSE -D_DEBUG -DMSM8960_ALSA -DINT_MAX=0x7fffffff -include log/logd.h -D_Nonnull="" -DTINYALSA_LIB
mm_audio_ftm_LDADD = -lm @TINYALSA_LIBS@ -lcutils -llog @DIAG_LIBS@ @GLIB_LIBS@ -ldl

ftmconfdir   = "/etc"
mm_audio_ftm_la_list =  ${top_srcdir}/ar/config/$(MACHINE_ENABLED)/ftm_test_config_sm6150-idp-snd-card
ftmconf_SCRIPTS = $(mm_audio_ftm_la_list)
install-data-hook:
	chmod go+r $(DESTDIR)$(ftmconfdir)/ftm_test_config_sm6150-idp-snd-card
