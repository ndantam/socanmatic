#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.65])
AC_INIT([socia], [0.0.1], [ntd@gatech.edu])
AM_INIT_AUTOMAKE([-Wall])
AC_CONFIG_SRCDIR([include/socia.h])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4])

# Checks for programs.
AC_USE_SYSTEM_EXTENSIONS
AC_PROG_CC
AC_PROG_CC_C89
AC_PROG_LIBTOOL

AC_C_RESTRICT
AC_C_INLINE
AC_C_CONST

# Checks for header files.
AC_CHECK_HEADERS([arpa/inet.h fcntl.h inttypes.h stdint.h stdlib.h string.h sys/socket.h syslog.h unistd.h time.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_HEADER_STDBOOL
AC_TYPE_INT32_T
AC_TYPE_MODE_T
AC_TYPE_OFF_T
AC_TYPE_PID_T
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T
AC_TYPE_UINT32_T
AC_TYPE_UINT64_T
AC_TYPE_UINT8_T

AC_CHECK_SIZEOF(void *)
AC_CHECK_SIZEOF(uint64_t)
AC_CHECK_SIZEOF(unsigned long)
AC_CHECK_SIZEOF(unsigned long long)

# Check 32/64 safe format specifiers
AC_CHECK_DECLS([PRIuPTR,PRIu64,PRIx64])
AC_CHECK_DECL([PRIuPTR],
        [],
        [AC_DEFINE([PRIuPTR], ["ul"], [Assume this is unsigned long])])

# Checks for library functions.
AC_FUNC_FORK
AC_FUNC_MALLOC
AC_FUNC_MMAP
AC_FUNC_REALLOC
AC_FUNC_STRTOD
AC_CHECK_FUNCS([ftruncate isascii memmove memset munmap socket strcasecmp strchr strdup strerror strtol])
AC_SEARCH_LIBS([clock_gettime],[rt])


# Enable maximum warnings
AX_CFLAGS_WARN_ALL

dnl The AX_CHECK_COMPILER_FLAGS maco was renamed to AX_CHECK_COMPILE_FLAG
dnl Checking for both versions
m4_ifdef([AX_CHECK_COMPILE_FLAG],
         [AC_DEFUN([APPEND_FLAG],
                   [AX_CHECK_COMPILE_FLAG([$1], [CFLAGS="$1 $CFLAGS"])])])

m4_ifdef([AX_CHECK_COMPILER_FLAGS],
         [AC_DEFUN([APPEND_FLAG],
                   [AX_CHECK_COMPILER_FLAGS([$1], [CFLAGS="$1 $CFLAGS"])])])

dnl If we found the flag checking macro, check some flags
m4_ifdef([APPEND_FLAG],
         [APPEND_FLAG([-Wextra])
          APPEND_FLAG([-Wconversion])
          APPEND_FLAG([-Wpointer-arith])
          APPEND_FLAG([-Wfloat-equal])
          APPEND_FLAG([-Wshadow])
          APPEND_FLAG([-Wwrite-strings])
          APPEND_FLAG([-Wc++-compat])])

# Doxygen
DX_HTML_FEATURE(ON)
DX_PDF_FEATURE(OFF)
DX_PS_FEATURE(OFF)
DX_INIT_DOXYGEN(ach)

AC_CONFIG_FILES([Makefile])
AC_OUTPUT