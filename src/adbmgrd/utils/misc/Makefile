#-------------------------------------------------------------------------
#
# Makefile--
#    Makefile for utils/misc
#
# IDENTIFICATION
#    src/adbmgrd/utils/misc/Makefile
#
#-------------------------------------------------------------------------

subdir = src/adbmgrd/utils/misc
top_builddir = ../../../..
include $(top_builddir)/src/Makefile.global

override CPPFLAGS := -I. -I$(srcdir) $(CPPFLAGS)

OBJS = guc.o help_config.o pg_rusage.o ps_status.o rbtree.o \
       superuser.o timeout.o tzparser.o

# This location might depend on the installation directories. Therefore
# we can't subsitute it into pg_config.h.
ifdef krb_srvtab
override CPPFLAGS += -DPG_KRB_SRVTAB='"$(krb_srvtab)"'
endif

include $(top_srcdir)/src/adbmgrd/common.mk

# guc-file is compiled as part of guc
guc.o: guc-file.c

# Note: guc-file.c is not deleted by 'make clean',
# since we want to ship it in distribution tarballs.
clean:
	@rm -f lex.yy.c
