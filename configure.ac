#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.
#
#################
#    Copyright (C) 2014 Shawn Wilson <swilson@acs.on.ca>
#       
#  This program is free software: you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation, either version 3 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program.  If not, see <http://www.gnu.org/licenses/>.
##################
#
#


AC_PREREQ(2.59)
AC_INIT([xenserver-backup], [2.0.3], [swilson@acs.on.ca])
AM_INIT_AUTOMAKE
AC_PROG_MKDIR_P

# Allow the user to override the default file names & directories.
AC_ARG_VAR(XVA_PATH, "The default path for xva backups")
AC_ARG_VAR(XE_HOST, "The xe hostname or IP address.")
AC_ARG_VAR(XE_PWF, "The filepath for the xe credentials file")
AC_ARG_VAR(VM_NAME_FILE, "The filepath for the list of VMs to backup")


# Here we have to expand the standard autoconf directories into their
# own variables so we can substitute them into the config & crontab
# files.
AS_AC_EXPAND(LOCALSTATEDIR, ${localstatedir}/lib/${PACKAGE})
AS_AC_EXPAND(SYSCONFDIR, ${sysconfdir}/${PACKAGE})
AS_AC_EXPAND(BINDIR, ${bindir})
AS_AC_EXPAND(LOGDIR, ${localstatedir}/log)
AC_SUBST(XVA_PATH, [${XVA_PATH:-${LOCALSTATEDIR}}])
AC_SUBST(XE_HOST, [${XVA_HOST:-"127.0.0.1"}])
AC_SUBST(XVA_RETAIN, [${XVA_RETAIN:-4}])
AC_SUBST(XE_PWF, [${XE_PWF:-${SYSCONFDIR}/xe.pwf}])
AC_SUBST(VM_NAME_FILE, [${VM_NAME_FILE:-${SYSCONFDIR}/vm-backup-list}])


# Here's the default config values.
AC_SUBST(SNAPSHOT_SUFFIX, [snapback])
AC_SUBST(TEMP_SUFFIX, [newbackup])
AC_SUBST(BACKUP_SUFFIX, [backup])
AC_SUBST(WEEKLY_BACKUP_DAY, [Sun])
AC_SUBST(MONTHLY_BACKUP_DAY, [Sun])
AC_SUBST(TEMPLATE_SR, [BackupSR])


# List all the files that autoconf has to do substitiutions on.
AC_CONFIG_FILES(
   [Makefile scripts/Makefile config/Makefile lib/Makefile 
    scripts/xenserver-backup lib/init-functions 
    config/default.conf config/default.crontab])
AC_OUTPUT
