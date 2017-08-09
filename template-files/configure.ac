dnl   ****  READ ME FIRST ****
dnl Update the parameters provided to AC_INIT below.
dnl Additionally, the project name 'SKELETON_PROJECT' has been provided to
dnl pkg-config. As such, CFLAGS and LIBS instructions will also be prefixed
dnl with 'SKELETON_PROJECT_'. If you update this value, be sure to update the
dnl references in src/Makefile.am as well!


dnl Initialization
AC_PREREQ([2.69])
AC_INIT([__PROJECT_NAME__], [__PROJECT_VERSION__], [__PROJECT_EMAIL__],, [])
dnl AC_USE_SYSTEM_EXTENSIONS must be called prior to any macros that use the
dnl C compile (such as AX_CHECK_COMPILE_FLAG below, or the CHECK_LIB calls)
AC_USE_SYSTEM_EXTENSIONS
AC_CONFIG_SRCDIR([src/main.c])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4/])

AM_INIT_AUTOMAKE([foreign no-exeext -Wall -Wno-override -Wno-extra-portability])
AM_SILENT_RULES([yes])
dnl Libtool is a life saver if your project starts getting complex
LT_INIT()

dnl Shopping List
AC_PROG_CC([gcc])
AC_PROG_INSTALL
PKG_PROG_PKG_CONFIG

dnl AR warnings (see https://bugzilla.redhat.com/show_bug.cgi?id=1155273)
m4_divert_text([DEFAULTS], [: "${ARFLAGS=cr} ${AR_FLAGS=cr}"])

dnl Projects should use modern C
AX_CHECK_COMPILE_FLAG([-std=gnu11], [CFLAGS+=" -std=gnu11"], AC_MSG_ERROR([
  **************************************************************************
  **** The gnu99 standard is required for this project. See config.log  ****
  **** for more information.                                            ****
  **************************************************************************]))

dnl Libraries
PKG_CHECK_MODULES([SKELETON_PROJECT], [
                   glib-2.0
                   gtk+-3.0
                   ])

# Checks for header files.
AC_CHECK_HEADERS([stddef.h stdlib.h string.h strings.h unistd.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_TYPE_SIZE_T

# Look for C99 types
AC_CHECK_TYPES([uint8_t, uint16_t, uint32_t])

AC_C_INLINE

if test "$ac_cv_c_inline" != no ; then
  AC_DEFINE(HAVE_INLINE,1, Define to 1 if inline is supported)
  AC_SUBST(HAVE_INLINE)
fi

AC_FUNC_ERROR_AT_LINE
AC_FUNC_MALLOC
AC_FUNC_STRNLEN
AC_CHECK_FUNCS([bzero memmove memset strerror])

dnl Output
AC_CONFIG_FILES([Makefile
                 README.md
                 resources/Makefile
                 src/Makefile
                 tests/Makefile])
AC_OUTPUT

echo \
"-------------------------------------------------

 ${PACKAGE_NAME} Version ${PACKAGE_VERSION}

 Prefix: '${prefix}'.
 Compiler: '${CC} ${CFLAGS} ${CPPFLAGS}'

 Now type 'make @<:@<target>@:>@'
   where the optional <target> is:
     all                - build all binaries (default)
     install            - install everything

--------------------------------------------------"
