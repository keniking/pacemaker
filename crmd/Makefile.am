#
# Copyright (C) 2004 Andrew Beekhof
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
#
include $(top_srcdir)/Makefile.common

halibdir	= $(CRM_DAEMON_DIR)

## binary progs
halib_PROGRAMS	= crmd

## SOURCES

noinst_HEADERS	= crmd_alerts.h crmd_callbacks.h crmd_fsa.h crmd.h \
		crmd_lrm.h crmd_messages.h crmd_utils.h fsa_defines.h \
		fsa_matrix.h fsa_proto.h membership.h te_callbacks.h \
		tengine.h throttle.h crmd_metadata.h

crmd_CFLAGS	= $(CFLAGS_HARDENED_EXE)
crmd_LDFLAGS	= $(LDFLAGS_HARDENED_EXE)

crmd_LDADD	= $(top_builddir)/lib/fencing/libstonithd.la		\
		$(top_builddir)/lib/transition/libtransitioner.la	\
		$(top_builddir)/lib/pengine/libpe_rules.la		\
		$(top_builddir)/lib/cib/libcib.la			\
		$(top_builddir)/lib/cluster/libcrmcluster.la		\
		$(top_builddir)/lib/common/libcrmcommon.la		\
		$(top_builddir)/lib/services/libcrmservice.la		\
		$(top_builddir)/lib/lrmd/liblrmd.la			\
		$(CLUSTERLIBS)

crmd_SOURCES	= main.c corosync.c crmd_metadata.c			\
		fsa.c control.c messages.c membership.c callbacks.c attrd.c	\
		election.c join_client.c join_dc.c throttle.c			\
		cib.c pengine.c tengine.c lrm.c lrm_state.c remote_lrmd_ra.c	\
		utils.c misc.c te_events.c te_actions.c te_utils.c te_callbacks.c

if BUILD_XML_HELP
man7_MANS 	= crmd.7
endif

CLEANFILES = $(man7_MANS)
