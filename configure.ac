AC_INIT(OVC2, version-2.0)

# Init automake.
AM_INIT_AUTOMAKE([foreign -Wall])

# Check for some basics.
AC_PROG_CC
AC_LANG_C

# No idea what this does.
AM_PROG_CC_C_O

# Check for libc; obviously this is required.
AC_CHECK_LIB([c], [malloc], , [FAILED=yes])
if test "$FAILED" = "yes" ; then
   AC_MSG_ERROR([libc is required for OVC2])
fi

# Check for some other libraries.
PKG_CHECK_MODULES(GTK, [gtk+-2.0 >= 2.12])
PKG_CHECK_MODULES(Gstreamer, [gstreamer-0.10 >= 0.10.11])
PKG_CHECK_MODULES(telepathy, [telepathy-glib >= 0.9.0])

PACKAGE_CFLAGS="-g -Wall $GTK_CFLAGS $Gstreamer_CFLAGS $telepathy_CFLAGS"
PACKAGE_LIBS="-g $GTK_LIBS $Gstreamer_LIBS $telepathy_LIBS"
PACKAGE_LDFLAGS="-export-dynamic $GTK_LDFLAGS $Gstreamer_LDFLAGS"

# Add our own include directory to the PACKAGE_CFLAGS variable.
PACKAGE_CFLAGS="$PACKAGE_CFLAGS -I`pwd`/include"

AC_SUBST([PACKAGE_CFLAGS])
AC_SUBST([PACKAGE_LIBS])
AC_SUBST([PACKAGE_LDFLAGS])

# The files to output
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_FILES([Makefile src/Makefile])

# And finish up.
AC_OUTPUT

