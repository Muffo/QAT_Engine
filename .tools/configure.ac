#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.68])
AC_INIT([libqat], [1.0], [])
AC_CONFIG_SRCDIR([config.h.in])
AC_CONFIG_HEADERS([config.h])
AM_INIT_AUTOMAKE([foreign])

#Libtool for generating shared library

LT_INIT
AC_PROG_LIBTOOL
AC_PROG_LN_S
AC_CONFIG_MACRO_DIR([m4])

# Parameter parsing for disabling the feature

AC_ARG_ENABLE(qat_rsa,
              AS_HELP_STRING([--disable-qat_rsa],
                             [Disable accelerated RSA offload]),
              , disable_qat_rsa=unset)
AC_SUBST(disable_qat_rsa)


AC_ARG_ENABLE(qat_ciphers,
              AS_HELP_STRING([--disable-qat_ciphers],
                             [Disable accelerated CIPHERS offload]),
              , disable_qat_ciphers=unset)
AC_SUBST(disable_qat_ciphers)


AC_ARG_ENABLE(qat_ecdh,
              AS_HELP_STRING([--disable-qat_ecdh],
                             [Disable accelerated ECDH offload]),
              , disable_qat_ecdh=unset)
AC_SUBST(disable_qat_ecdh)


AC_ARG_ENABLE(qat_ecdsa,
              AS_HELP_STRING([--disable-qat_ecdsa],
                             [Disable accelerated ECDSA offload]),
              , disable_qat_ecdsa=unset)
AC_SUBST(disable_qat_ecdsa)


AC_ARG_ENABLE(qat_dsa,
              AS_HELP_STRING([--disable-qat_dsa],
                             [Disable accelerated DSA offload]),
              , disable_qat_dsa=unset)
AC_SUBST(disable_qat_dsa)


AC_ARG_ENABLE(qat_dh,
              AS_HELP_STRING([--disable-qat_dh],
                             [Disable accelerated DH offload]),
              , disable_qat_dh=unset)
AC_SUBST(disable_qat_dh)


AC_ARG_ENABLE(qat_prf,
              AS_HELP_STRING([--disable-qat_prf],
                             [Disable accelerated PRF offload]),
              , disable_qat_prf=unset)
AC_SUBST(disable_qat_prf)


# Parameter parsing for enabling debug/warnings

AC_ARG_ENABLE(qat_debug,
              AS_HELP_STRING([--enable-qat_debug],
                             [Enable Engine Debug Messages]),
              , enable_qat_debug=unset)
AC_SUBST(enable_qat_debug)


AC_ARG_ENABLE(qat_warnings,
              AS_HELP_STRING([--enable-qat_warnings],
                             [Enable Engine Warning Messages]),
              , enable_qat_warnings=unset)
AC_SUBST(enable_qat_warnings)

AC_ARG_ENABLE(qat_mem_debug,
              AS_HELP_STRING([--enable-qat_mem_debug],
                             [Enable Memory Driver Debug Messages]),
              , enable_qat_mem_debug=unset)
AC_SUBST(enable_qat_mem_debug)

AC_ARG_ENABLE(qat_mem_warnings,
              AS_HELP_STRING([--enable-qat_mem_warnings],
                             [Enable Memory Driver Warning Messages]),
              , enable_qat_mem_warnings=unset)
AC_SUBST(enable_qat_mem_warnings)

# Environment setting : Required for building the library

AC_ARG_WITH(qat_dir,
              AS_HELP_STRING([--with-qat_dir],
                             [Path to the Intel Quickassist Technology Driver source code]),
              , with_qat_dir=unset)
AC_SUBST(with_qat_dir)

AC_ARG_WITH(upstream_driver_cmd_dir,
              AS_HELP_STRING([--with-upstream_driver_cmd_dir],
                             [Path to the Intel Common Memory Driver source code when used by the Upstream Intel Quickassist Technology Driver. This option is not related to which Memory Driver is used by the Engine itself. There is no need to set this option if not using the Upstream version of the Intel Quickassist Technology Driver]),
              , with_upstream_driver_cmd_dir=unset)
AC_SUBST(with_upstream_driver_cmd_dir)

AC_ARG_WITH(qat_install_dir,
              AS_HELP_STRING([--with-qat_install_dir],
                             [Path to the Intel Quickassist Technology Driver build output]),
              , with_qat_install_dir=unset)
AC_SUBST(with_qat_install_dir)


AC_ARG_WITH(openssl_dir,
              AS_HELP_STRING([--with-openssl_dir],
                             [Path to the OpenSSL source code]),
              , with_openssl_dir=unset)
AC_SUBST(with_openssl_dir)


AC_ARG_WITH(openssl_install_dir,
              AS_HELP_STRING([--with-openssl_install_dir],
                             [Path to where the OpenSSL libraries are installed to. The Engine will be installed to the lib/engines subdirectory of this path]),
              , with_openssl_install_dir=unset)
AC_SUBST(with_openssl_install_dir)


AC_ARG_WITH(cmd_dir,
              AS_HELP_STRING([--with-cmd_dir],
                             [Path to the Intel Common Memory Driver source code. This should be specified to force the Engine to use the Intel Common Memory Driver rather than the supplied Memory Driver]),
              , with_cmd_dir=unset)
AC_SUBST(with_cmd_dir)

AC_ARG_WITH(cc_opt,
              AS_HELP_STRING([--with-cc_opt],
                             [Sets additional parameters that will be added to the CFLAGS]),
              , with_cc_opt=unset)
AC_SUBST(with_cc_opt)

AC_ARG_WITH(ld_opt,
              AS_HELP_STRING([--with-ld_opt],
                             [Sets additional parameters that will be used during linking]),
              , with_ld_opt=unset)
AC_SUBST(with_ld_opt)

AC_ARG_ENABLE(multi_thread,
            AS_HELP_STRING([--enable-multi_thread],
                           [Enable using a multi threaded version of the user space part of the supplied memory driver. Please see the documentation on limitations of using this option]),
              , enable_multi_thread=unset)
AC_SUBST(enable_multi_thread)

AC_ARG_ENABLE(qat_mux,
            AS_HELP_STRING([--enable-qat_mux],
                           [Enable linking against a build of the Intel Quickassist Technology Driver that supports multiple accelerator hardware versions. Please see the documentation for more details]),
              , enable_qat_mux=unset)
AC_SUBST(enable_qat_mux)

# ERROR message if mandatory options are not provided

if test "x$with_qat_dir" = "xunset"
then
  AC_MSG_ERROR([--with-qat_dir is not set, set it to the path to the Intel Quickassist Technology Driver source code. e.g: --with-qat_dir=/path/to/qat_driver])
fi

if test "x$with_qat_install_dir" = "xunset"
then
  AC_MSG_ERROR([--with-qat_install_dir is not set, set it to the path to the Intel Quickassist Technology Driver build output. e.g: --with-qat_install_dir=/path/to/qat_driver/build])
fi

if test "x$with_openssl_dir" = "xunset"
then
  AC_MSG_ERROR([--with-openssl_dir is not set, set it to the path to the OpenSSL source code. e.g: --with-openssl_dir=/path/to/openssl])
fi

if test "x$with_openssl_install_dir" = "xunset"
then
  AC_MSG_ERROR([--with-openssl_install_dir is not set, set it to the path to where the OpenSSL libraries are installed. e.g: --with-openssl_install_dir=/path/to/openssl_install])
fi

ac_default_prefix=$with_openssl_install_dir

# The below flag with_upstream_driver is needed only when building against upstream driver
if test "x$with_upstream_driver_cmd_dir" = "xunset"
then
  AC_MSG_NOTICE([--with-upstream_driver_cmd_dir is not set. If building against the Upstream Intel Quickassist Technology Driver then set it to point to the path to the Intel Common Memory Driver source/library files. e.g: --with-upstream_driver_cmd_dir=/path/to/libusdm_drv_s.so])
fi
# Checking the parameters given and parsing the relevant flags

if test "x$disable_qat_rsa" = "xunset"
then
  disable_qat_rsa="-DOPENSSL_ENABLE_QAT_RSA"
  AC_MSG_NOTICE([Offloading RSA to Hardware])
else
  disable_qat_rsa="-DOPENSSL_DISABLE_QAT_RSA"
  AC_MSG_NOTICE([Not Offloading RSA to Hardware])
fi

if test "x$disable_qat_ciphers" = "xunset"
then
  disable_qat_ciphers="-DOPENSSL_ENABLE_QAT_CIPHERS"
  AC_MSG_NOTICE([Offloading CIPHERS to Hardware])
else
  disable_qat_ciphers="-DOPENSSL_DISABLE_QAT_CIPHERS"
  AC_MSG_NOTICE([Not Offloading CIPHERS to Hardware])
fi

if test "x$disable_qat_ecdh" = "xunset"
then
  disable_qat_ecdh="-DOPENSSL_ENABLE_QAT_ECDH"
  AC_MSG_NOTICE([Offloading ECDH to Hardware])
else
  disable_qat_ecdh="-DOPENSSL_DISABLE_QAT_ECDH"
  AC_MSG_NOTICE([Not Offloading ECDH to Hardware])
fi

if test "x$disable_qat_ecdsa" = "xunset"
then
  disable_qat_ecdsa="-DOPENSSL_ENABLE_QAT_ECDSA"
  AC_MSG_NOTICE([Offloading ECDSA to Hardware])
else
  disable_qat_ecdsa="-DOPENSSL_DISABLE_QAT_ECDSA"
  AC_MSG_NOTICE([Not Offloading ECDSA to Hardware])
fi

if test "x$disable_qat_dsa" = "xunset"
then
  disable_qat_dsa="-DOPENSSL_ENABLE_QAT_DSA"
  AC_MSG_NOTICE([Offloading DSA to Hardware])
else
  disable_qat_dsa="-DOPENSSL_DISABLE_QAT_DSA"
  AC_MSG_NOTICE([Not Offloading DSA to Hardware])
fi

if test "x$disable_qat_dh" = "xunset"
then
  disable_qat_dh="-DOPENSSL_ENABLE_QAT_DH"
  AC_MSG_NOTICE([Offloading DH to Hardware])
else
  disable_qat_dh="-DOPENSSL_DISABLE_QAT_DH"
  AC_MSG_NOTICE([Not Offloading DH to Hardware])
fi

if test "x$disable_qat_prf" = "xunset"
then
  disable_qat_prf="-DOPENSSL_ENABLE_QAT_PRF"
  AC_MSG_NOTICE([Offloading PRF to Hardware])
else
  disable_qat_prf="-DOPENSSL_DISABLE_QAT_PRF"
  AC_MSG_NOTICE([Not Offloading PRF to Hardware])
fi

if test "x$enable_qat_debug" != "xunset"
then
  enable_qat_debug="-DQAT_DEBUG"
  AC_MSG_NOTICE([Enabling Engine Debug Messages])
else
  enable_qat_debug=""
  AC_MSG_NOTICE([Disabling Engine Debug Messages])
fi

if test "x$enable_qat_warnings" != "xunset"
then
  enable_qat_warn="-DQAT_WARN"
  AC_MSG_NOTICE([Enabling Engine Warning Messages])
else
  enable_qat_warn=""
  AC_MSG_NOTICE([Disabling Engine Warning Messages])
fi

if test "x$enable_qat_mem_debug" != "xunset"
then
  enable_qat_mem_debug="-DQAT_MEM_DEBUG"
  AC_MSG_NOTICE([Enabling Memory Driver Debug Messages])
else
  enable_qat_mem_debug=""
  AC_MSG_NOTICE([Disabling Memory Driver Debug Messages])
fi

if test "x$enable_qat_mem_warnings" != "xunset"
then
  enable_qat_mem_warn="-DQAT_MEM_WARN"
  AC_MSG_NOTICE([Enabling Memory Driver Warning Messages])
else
  enable_qat_mem_warn=""
  AC_MSG_NOTICE([Disabling Memory Driver Warning Messages])
fi

# Check for memory driver and parse the CFLAGS for building library

AC_ARG_WITH(includes, AS_HELP_STRING(), , includes="-I\$(with_openssl_dir)/include")
AC_SUBST(includes)

AC_ARG_WITH(cflags, AS_HELP_STRING(), , cflags="-shared -fPIC")
AC_SUBST(cflags)

if test "x$with_cc_opt" != "xunset"
then
AC_ARG_WITH(cflags_cc_opt, AS_HELP_STRING(), , cflags_cc_opt="\$(with_cc_opt)")
AC_SUBST(cflags_cc_opt)
fi

if test "x$with_upstream_driver_cmd_dir" != "xunset"
then
AC_ARG_WITH(cflags_with_upstream_driver_cmd_dir, AS_HELP_STRING(), , cflags_with_upstream_driver_cmd_dir="-DOPENSSL_ENABLE_QAT_UPSTREAM_DRIVER")
AC_SUBST(cflags_with_upstream_driver_cmd_dir)
fi

if test "x$with_cmd_dir" = "xunset" -a "x$enable_multi_thread" = "xunset"
then
  AC_MSG_NOTICE([ Compiling for QAT_CONTIG_MEMORY])
  AC_ARG_WITH(cflags_qat_contig_mem, AS_HELP_STRING(), , cflags_qat_contig_mem="-DUSE_QAT_CONTIG_MEM -Iqat_contig_mem")
  AC_SUBST(cflags_qat_contig_mem)
else if test "x$with_cmd_dir" = "xunset" -a "x$enable_multi_thread" != "xunset"
then
  AC_MSG_NOTICE([ Compiling for MULTI_THREAD])
  AC_ARG_WITH(cflags_enable_multi_thread, AS_HELP_STRING(), , cflags_enable_multi_thread="-DUSE_QAT_CONTIG_MEM -Iqat_contig_mem")
  AC_SUBST(cflags_enable_multi_thread)
else if test "x$with_cmd_dir" != "xunset"
then
  AC_MSG_NOTICE([ Compiling for COMMON MEMORY DRIVER])
  AC_ARG_WITH(cflags_with_cmd_dir, AS_HELP_STRING(), , cflags_with_cmd_dir="-DUSE_QAE_MEM")
  AC_SUBST(cflags_with_cmd_dir)
  AC_ARG_WITH(includes_with_cmd_dir, AS_HELP_STRING(), , include_with_cmd_dir="-I\$(with_cmd_dir)")
  AC_SUBST(include_with_cmd_dir)
fi
fi
fi

AM_CONDITIONAL([QAT_CONTIG_MEM], [test "x$with_cmd_dir" = "xunset" -a "x$enable_multi_thread" = "xunset"])
AM_CONDITIONAL([QAT_MULTI_THREAD], [test "x$with_cmd_dir" = "xunset" -a "x$enable_multi_thread" != "xunset"])
AM_CONDITIONAL([QAE_MEM], [test "x$with_cmd_dir" != "xunset"])

# Adding driver source for building and linking the library

AC_ARG_WITH(ICP_API_DIR, AS_HELP_STRING(), ,with_ICP_API_DIR="\$(with_qat_dir)/quickassist/include")
AC_SUBST(with_ICP_API_DIR)

AC_ARG_WITH(ICP_SAL_API_DIR, AS_HELP_STRING(), ,with_ICP_SAL_API_DIR="\$(with_qat_dir)/quickassist/lookaside/access_layer/include")
AC_SUBST(with_ICP_SAL_API_DIR)

AC_ARG_WITH(ICP_LAC_API_DIR, AS_HELP_STRING(), ,with_ICP_LAC_API_DIR="\$(with_ICP_API_DIR)/lac")
AC_SUBST(with_ICP_LAC_API_DIR)

AC_ARG_WITH(includes_driver, AS_HELP_STRING(), , includes_driver="-I\$(with_ICP_API_DIR) -I\$(with_ICP_LAC_API_DIR) -I\$(with_ICP_SAL_API_DIR)")
AC_SUBST(includes_driver)

AC_ARG_WITH(DRIVER, AS_HELP_STRING(), , DRIVER="icp_qa_al")
AC_SUBST(DRIVER)

if test "x$enable_qat_mux" != "xunset"
then
AC_ARG_WITH(ICP_MUX_DIR, AS_HELP_STRING(), , with_ICP_MUX_DIR="\$(with_qat_dir)/../QAT1.5/quickassist/include")
AC_SUBST(with_ICP_MUX_DIR)
AC_ARG_WITH(ICP_DC_DIR, AS_HELP_STRING(), , with_ICP_DC_DIR="\$(with_ICP_API_DIR)/dc")
AC_SUBST(with_ICP_DC_DIR)
AC_ARG_WITH(cflags_mux, AS_HELP_STRING(), , cflags_mux="-DWITH_CPA_MUX")
AC_SUBST(cflags_mux)
AC_ARG_WITH(includes_enable_qat_mux, AS_HELP_STRING(), , includes_enable_qat_mux="-I\$(with_ICP_MUX_DIR) -I\$(with_ICP_DC_DIR)")
AC_SUBST(includes_enable_qat_mux)
AC_ARG_WITH(DRIVER, AS_HELP_STRING(), , DRIVER="qat_mux")
AC_SUBST(DRIVER)
fi

if test "x$with_ld_opt" != "xunset"
then
  AC_ARG_WITH(QAT_SHARED_LIB_DEPS_LD, AS_HELP_STRING(), , QAT_SHARED_LIB_DEPS_LD=["\$(with_ld_opt)"])
  AC_SUBST(QAT_SHARED_LIB_DEPS_LD)
fi

if test "x$with_qat_install_dir" != "xunset"
then
  if test "x$with_upstream_driver_cmd_dir" != "xunset"
  then
  AC_ARG_WITH(QAT_SHARED_LIB_DEPS_UPSTREAM_DRIVER, AS_HELP_STRING(), , QAT_SHARED_LIB_DEPS_UPSTREAM_DRIVER=["-Wl,-rpath,\$(with_upstream_driver_cmd_dir) -L\$(with_upstream_driver_cmd_dir) -lusdm_drv_s"])
  AC_SUBST(QAT_SHARED_LIB_DEPS_UPSTREAM_DRIVER)
  AC_ARG_WITH(DRIVER, AS_HELP_STRING(), , DRIVER="qat")
  AC_SUBST(DRIVER)
  AC_ARG_WITH(QAT_SHARED_LIB_DEPS_DRIVER, AS_HELP_STRING(), , QAT_SHARED_LIB_DEPS_DRIVER=["-Wl,-rpath,\$(with_qat_install_dir) -L\$(with_qat_install_dir) -l\$(DRIVER)_s -ludev"])
  AC_SUBST(QAT_SHARED_LIB_DEPS_DRIVER)
  else if test "x$with_upstream_driver_cmd_dir" = "xunset"
  then
    AC_ARG_WITH(QAT_SHARED_LIB_DEPS_DRIVER, AS_HELP_STRING(), , QAT_SHARED_LIB_DEPS_DRIVER=["-Wl,-rpath,\$(with_qat_install_dir) -L\$(with_qat_install_dir) -l\$(DRIVER)_s"])
    AC_SUBST(QAT_SHARED_LIB_DEPS_DRIVER)
  fi
  fi
else if "x$with_qat_install_dir" = "xunset"
then
  if test "x$with_upstream_driver_cmd_dir" != "xunset"
  then
  AC_ARG_WITH(QAT_SHARED_LIB_DEPS_UPSTREAM_DRIVER, AS_HELP_STRING(), , QAT_SHARED_LIB_DEPS_UPSTREAM_DRIVER=["-Wl,-rpath,\$(with_upstream_driver_cmd_dir) -L\$(with_upstream_driver_cmd_dir) -lusdm_drv_s"])
  AC_SUBST(QAT_SHARED_LIB_DEPS_UPSTREAM_DRIVER)
  AC_ARG_WITH(DRIVER, AS_HELP_STRING(), , DRIVER="qat")
  AC_SUBST(DRIVER)
  AC_ARG_WITH(QAT_SHARED_LIB_DEPS_DRIVER, AS_HELP_STRING(), , QAT_SHARED_LIB_DEPS_DRIVER=["-l\$(DRIVER)_s -ludev"])
  AC_SUBST(QAT_SHARED_LIB_DEPS_DRIVER)
  if test "x$with_upstream_driver_cmd_dir" = "xunset"
  then
  AC_ARG_WITH(QAT_SHARED_LIB_DEPS_DRIVER, AS_HELP_STRING(), , QAT_SHARED_LIB_DEPS_DRIVER=["-l\$(DRIVER)_s"])
  AC_SUBST(QAT_SHARED_LIB_DEPS_DRIVER)
  fi 
  fi 
fi
fi

if test "x$with_cmd_dir" != "xunset" -a "x$enable_multi_thread" = "xunset" -a "x$with_upstream_driver_cmd_dir" = "xunset"
then
  AC_ARG_WITH(QAT_SHARED_LIB_DEPS_QAE_MEM, AS_HELP_STRING(), , QAT_SHARED_LIB_DEPS_QAE_MEM=["-Wl,-rpath,\$(with_cmd_dir) -L\$(with_cmd_dir) -lqae_mem_s"])
  AC_SUBST(QAT_SHARED_LIB_DEPS_QAE_MEM)
fi

# Checks for programs.
AC_PROG_CXX
AC_PROG_CC

# Output files from the configure
AC_CONFIG_FILES([Makefile])
AC_OUTPUT