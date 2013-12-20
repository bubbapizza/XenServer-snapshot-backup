#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ(2.59)
AC_INIT([xenserver-backup], [1.4.1], [swilson@acs.on.ca])
AM_INIT_AUTOMAKE

# Allow the user to pass the progress install directory as a variable.
AC_ARG_VAR(XVA_PATH, "The default path for xva backups")


# Set the default database location and name.
AS_AC_EXPAND(LOCALSTATEDIR, ${localstatedir}/lib/${PACKAGE})
AC_SUBST(XVA_PATH, [${DB_PATH:-${LOCALSTATEDIR}}])


# List all the files that autoconf has to do substitiutions on.
AC_CONFIG_FILES(
   [Makefile scripts/Makefile config/Makefile lib/Makefile 
    scripts/xenserver-backup lib/init-functions 
    config/default-config])
AC_OUTPUT