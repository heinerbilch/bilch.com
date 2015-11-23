title=Sweep3D benchmark
date=2015-08-25
type=post
tags=blog
status=published
~~~~~~

The benchmark was run on a first generation Intel core i7 under FreeBSD 10.1

# MPI version

6 processors, 150 * 150 * 150 grid

    SWEEP3D - Method 5 - Pipelined Wavefront with Line-Recursion
     Version 2.2b
     S6P1   -  6 angles/octant,  4 moments
     global grid: 150x150x150
	       6 domains   -            2 x           3 decomposition
	      15 domain pipelined blocks -          30 k-planes by           2 angles each
     estimated memory usage per domain:   72.5 MB
	     840 global messages per iteration
     92.31% domain parallel efficiency - due to decomposition & blocking
     83.71% multitasking efficiency on  16 processors
     77.27% combined efficiency on a cluster of    6  16-way SMPs
     DSA leakage calculation: ON
     Flux fixups: ON (after           7 iterations)
     Iteration Monitor:
      its =            1  err =    1.0000000000000000        fixs =            0
      its =            2  err =    197.57181285002989        fixs =            0
      its =            3  err =    1.4368357106950367        fixs =            0
      its =            4  err =   0.65970770271194090        fixs =            0
      its =            5  err =   0.40387168404427054        fixs =            0
      its =            6  err =   0.26073702654794151        fixs =            0
      its =            7  err =   0.16989795514010800        fixs =            0
      its =            8  err =   0.24604859576303545        fixs =       873936
      its =            9  err =    7.0476154515000750E-002   fixs =       835176
      its =           10  err =    4.3643270502312058E-002   fixs =       818336
      its =           11  err =    2.6730856594547502E-002   fixs =       809760
      its =           12  err =    1.5593167406099211E-002   fixs =       804960
     Balance quantities:
      External Source:    124.99999999989008     
      Absorption:         124.34686677083241     
      I-leakages:       -0.10465786809836006       0.10465786809836006     
      J-leakages:       -0.10465786809835796       0.10465786809835798     
      K-leakages:       -0.10465786920765073       0.10465786920765072     
     CPU     time was:    22.457457999999999     
     Elapsed time was:    22.670886039733887     
     CPU grind time:   1.155E-02
     Wall grind time:  1.166E-02"

# Single processor

50 * 50 * 50 grid

     SWEEP3D - Method 5 - Pipelined Wavefront with Line-Recursion
     Version 2.2b
     S6P1   -  6 angles/octant,  4 moments
     global grid:  50x 50x 50
	       1 domains   -            1 x           1 decomposition
	       1 domain pipelined blocks -          50 k-planes by           6 angles each
     estimated memory usage per domain:   16.2 MB
	       0 global messages per iteration
    100.00% domain parallel efficiency - due to decomposition & blocking
     94.51% multitasking efficiency on  16 processors
     94.51% combined efficiency on a cluster of    1  16-way SMPs
     DSA leakage calculation: ON
     Flux fixups: ON (after           7 iterations)
     Iteration Monitor:
      its =            1  err =    1.0000000000000000        fixs =            0
      its =            2  err =    1.7751297526290062        fixs =            0
      its =            3  err =   0.65908380221800600        fixs =            0
      its =            4  err =   0.30534867194897863        fixs =            0
      its =            5  err =   0.14123407927259676        fixs =            0
      its =            6  err =    6.2789646139531266E-002   fixs =            0
      its =            7  err =    2.6695594895495889E-002   fixs =            0
      its =            8  err =    1.9956304230270387E-002   fixs =        12000
      its =            9  err =    5.6879301179698560E-003   fixs =        11712
      its =           10  err =    1.8541275633411605E-003   fixs =        11664
      its =           11  err =    6.8107482657488606E-004   fixs =        11664
      its =           12  err =    2.6175220321312121E-004   fixs =        11664
     Balance quantities:
      External Source:    4.0959999999997025     
      Absorption:         3.3434174648285961     
      I-leakages:       -0.12541941963514600       0.12541941963514597     
      J-leakages:       -0.12541941963514469       0.12541941963514469     
      K-leakages:       -0.12541942191566829       0.12541942191566829     
     CPU     time was:    3.0110910000000000     
     Elapsed time was:    3.0291299819946289     
     CPU grind time:   4.182E-02
     Wall grind time:  4.207E-02

# Single processor

150 * 150 * 150 grid

     SWEEP3D - Method 5 - Pipelined Wavefront with Line-Recursion
     Version 2.2b
     S6P1   -  6 angles/octant,  4 moments
     global grid: 150x150x150
	       1 domains   -            1 x           1 decomposition
	       1 domain pipelined blocks -         150 k-planes by           6 angles each
     estimated memory usage per domain:  433.6 MB
	       0 global messages per iteration
    100.00% domain parallel efficiency - due to decomposition & blocking
     98.22% multitasking efficiency on  16 processors
     98.22% combined efficiency on a cluster of    1  16-way SMPs
     DSA leakage calculation: ON
     Flux fixups: ON (after           7 iterations)
     Iteration Monitor:
      its =            1  err =    1.0000000000000000        fixs =            0
      its =            2  err =    197.57181285002989        fixs =            0
      its =            3  err =    1.4368357106950367        fixs =            0
      its =            4  err =   0.65970770271194090        fixs =            0
      its =            5  err =   0.40387168404427054        fixs =            0
      its =            6  err =   0.26073702654794151        fixs =            0
      its =            7  err =   0.16989795514010800        fixs =            0
      its =            8  err =   0.24604859576303545        fixs =       873936
      its =            9  err =    7.0476154515000750E-002   fixs =       835176
      its =           10  err =    4.3643270502312058E-002   fixs =       818336
      its =           11  err =    2.6730856594547502E-002   fixs =       809760
      its =           12  err =    1.5593167406099211E-002   fixs =       804960
     Balance quantities:
      External Source:    125.00000000023280     
      Absorption:         124.34686677080953     
      I-leakages:       -0.10465786809836131       0.10465786809836118     
      J-leakages:       -0.10465786809835748       0.10465786809835753     
      K-leakages:       -0.10465786920765024       0.10465786920765031     
     CPU     time was:    68.332866000000010     
     Elapsed time was:    68.440368890762329     
     CPU grind time:   3.515E-02
     Wall grind time:  3.521E-02

# Build log

Single CPU version

    build started at Tue Mar 17 13:36:50 CET 2015
    port directory: /usr/ports/benchmarks/sweep3d
    building for: FreeBSD 101Ramd64-default 10.1-RELEASE-p6 FreeBSD 10.1-RELEASE-p6 amd64
    maintained by: heiner_ej@yahoo.de
    ident warning: no id keywords in /usr/local/poudriere/data/.m/101Ramd64-default/ref//usr/ports/benchmarks/sweep3d/Makefile
    Makefile ident: 
    Poudriere version: 3.1.1
    Host OSVERSION: 1001000
    Jail OSVERSION: 1001000

    ---Begin Environment---
    PKGREPOSITORY=/tmp/pkgs
    PACKAGES=/tmp/pkgs
    OSVERSION=1001000
    UNAME_v=FreeBSD 10.1-RELEASE-p6
    UNAME_r=10.1-RELEASE-p6
    BLOCKSIZE=K
    MAIL=/var/mail/root
    STATUS=1
    SAVED_TERM=xterm-256color
    NO_WARNING_PKG_INSTALL_EOL=yes
    MASTERMNT=/usr/local/poudriere/data/.m/101Ramd64-default/ref
    FORCE_PACKAGE=yes
    PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/games:/usr/local/sbin:/usr/local/bin:/root/bin
    POUDRIERE_BUILD_TYPE=bulk
    OLDPWD=/root
    PWD=/
    MASTERNAME=101Ramd64-default
    USER=root
    HOME=/root
    POUDRIERE_VERSION=3.1.1
    TRYBROKEN=yes
    LOCALBASE=/usr/local
    PACKAGE_BUILDING=yes
    ---End Environment---

    ---Begin OPTIONS List---
    ---End OPTIONS List---

    --CONFIGURE_ARGS--
    --prefix=/usr/local ${_LATE_CONFIGURE_ARGS}
    --End CONFIGURE_ARGS--

    --CONFIGURE_ENV--
    XDG_DATA_HOME=/wrkdirs/usr/ports/benchmarks/sweep3d/work  XDG_CONFIG_HOME=/wrkdirs/usr/ports/benchmarks/sweep3d/work  HOME=/wrkdirs/usr/ports/benchmarks/sweep3d/work TMPDIR="/tmp" F77="gfortran48" FC="gfortran48" FFLAGS="-O -Wl,-rpath=/usr/local/lib/gcc48" FCFLAGS="-Wl,-rpath=/usr/local/lib/gcc48" SHELL=/bin/sh CONFIG_SHELL=/bin/sh ADDR2LINE="/usr/local/bin/addr2line" AR="/usr/local/bin/ar" AS="/usr/local/bin/as" CPPFILT="/usr/local/bin/c++filt" GPROF="/usr/local/bin/gprof" LD="/usr/local/bin/ld" NM="/usr/local/bin/nm" OBJCOPY="/usr/local/bin/objcopy" OBJDUMP="/usr/local/bin/objdump" RANLIB="/usr/local/bin/ranlib" READELF="/usr/local/bin/readelf" SIZE="/usr/local/bin/size" STRINGS="/usr/local/bin/strings" CONFIG_SITE=/usr/ports/Templates/config.site lt_cv_sys_max_cmd_len=262144
    --End CONFIGURE_ENV--

    --MAKE_ENV--
    XDG_DATA_HOME=/wrkdirs/usr/ports/benchmarks/sweep3d/work  XDG_CONFIG_HOME=/wrkdirs/usr/ports/benchmarks/sweep3d/work  HOME=/wrkdirs/usr/ports/benchmarks/sweep3d/work TMPDIR="/tmp" F77="gfortran48" FC="gfortran48" FFLAGS="-O -Wl,-rpath=/usr/local/lib/gcc48" FCFLAGS="-Wl,-rpath=/usr/local/lib/gcc48" NO_PIE=yes SHELL=/bin/sh NO_LINT=YES ADDR2LINE="/usr/local/bin/addr2line" AR="/usr/local/bin/ar" AS="/usr/local/bin/as" CPPFILT="/usr/local/bin/c++filt" GPROF="/usr/local/bin/gprof" LD="/usr/local/bin/ld" NM="/usr/local/bin/nm" OBJCOPY="/usr/local/bin/objcopy" OBJDUMP="/usr/local/bin/objdump" RANLIB="/usr/local/bin/ranlib" READELF="/usr/local/bin/readelf" SIZE="/usr/local/bin/size" STRINGS="/usr/local/bin/strings" PREFIX=/usr/local  LOCALBASE=/usr/local  LIBDIR="/usr/lib"  CC="cc" CFLAGS="-O2 -pipe  -fstack-protector -fno-strict-aliasing"  CPP="cpp" CPPFLAGS=""  LDFLAGS=" -Wl,-rpath=/usr/local/lib/gcc48  -L/usr/local/lib/gcc48 -B/usr/local/bin -fstack-protector" LIBS=""  CXX="c++" CXXFLAGS="-O2 -pipe -fstack-protector -fno-strict-aliasing "  MANPREFIX="/usr/local" BSD_INSTALL_PROGRAM="install  -s -o root -g wheel -m 555"  BSD_INSTALL_LIB="install  -s -o root -g wheel -m 444"  BSD_INSTALL_SCRIPT="install  -o root -g wheel -m 555"  BSD_INSTALL_DATA="install  -o root -g wheel -m 0644"  BSD_INSTALL_MAN="install  -o root -g wheel -m 444"
    --End MAKE_ENV--

    --PLIST_SUB--
    OSREL=10.1
    PREFIX=%D
    LOCALBASE=/usr/local
    RESETPREFIX=/usr/local
    PORTDOCS=""
    PORTEXAMPLES=""
    LIB32DIR=lib
    DOCSDIR="share/doc/sweep3d"
    EXAMPLESDIR="share/examples/sweep3d"
    DATADIR="share/sweep3d"
    WWWDIR="www/sweep3d"
    ETCDIR="etc/sweep3d"
    --End PLIST_SUB--

    --SUB_LIST--
    PREFIX=/usr/local
    LOCALBASE=/usr/local
    DATADIR=/usr/local/share/sweep3d
    DOCSDIR=/usr/local/share/doc/sweep3d
    EXAMPLESDIR=/usr/local/share/examples/sweep3d
    WWWDIR=/usr/local/www/sweep3d
    ETCDIR=/usr/local/etc/sweep3d
    --End SUB_LIST--

    ---Begin make.conf---
    USE_PACKAGE_DEPENDS=yes
    BATCH=yes
    WRKDIRPREFIX=/wrkdirs
    PORTSDIR=/usr/ports
    PACKAGES=/packages
    DISTDIR=/distfiles
    ---End make.conf---
    ===================================================
    ===>  License BSD2CLAUSE accepted by the user
    ===========================================================================
    ===================================================
    ===>   sweep3d-2.2b depends on file: /usr/local/sbin/pkg - not found
    ===>    Verifying install for /usr/local/sbin/pkg in /usr/ports/ports-mgmt/pkg
    ===>   Installing existing package /packages/All/pkg-1.4.12.txz
    [101Ramd64-default] Installing pkg-1.4.12...
    [101Ramd64-default] Extracting pkg-1.4.12... done
    Message for pkg-1.4.12:
     If you are upgrading from the old package format, first run:

      # pkg2ng
    ===>   Returning to build of sweep3d-2.2b
    ===========================================================================
    ===================================================
    ===========================================================================
    ===================================================
    ===>  License BSD2CLAUSE accepted by the user
    ===>   sweep3d-2.2b depends on file: /usr/local/sbin/pkg - found
    ===> Fetching all distfiles required by sweep3d-2.2b for building
    ===========================================================================
    ===================================================
    ===>  License BSD2CLAUSE accepted by the user
    ===>   sweep3d-2.2b depends on file: /usr/local/sbin/pkg - found
    ===> Fetching all distfiles required by sweep3d-2.2b for building
    => SHA256 Checksum OK for sweep3d-2.2b.tar.gz.
    ===========================================================================
    ===================================================
    ===========================================================================
    ===================================================
    ===>  License BSD2CLAUSE accepted by the user
    ===>   sweep3d-2.2b depends on file: /usr/local/sbin/pkg - found
    ===> Fetching all distfiles required by sweep3d-2.2b for building
    ===>  Extracting for sweep3d-2.2b
    => SHA256 Checksum OK for sweep3d-2.2b.tar.gz.
    ===========================================================================
    ===================================================
    ===========================================================================
    ===================================================
    ===>  Patching for sweep3d-2.2b
    ===========================================================================
    ===================================================
    ===>   sweep3d-2.2b depends on executable: gfortran48 - not found
    ===>    Verifying install for gfortran48 in /usr/ports/lang/gcc
    ===>   Installing existing package /packages/All/gcc-4.8.4.txz
    [101Ramd64-default] Installing gcc-4.8.4...
    [101Ramd64-default] `-- Installing binutils-2.25...
    [101Ramd64-default] |   `-- Installing gettext-runtime-0.19.4...
    [101Ramd64-default] |   | `-- Installing indexinfo-0.2.2...
    [101Ramd64-default] |   | `-- Extracting indexinfo-0.2.2... done
    [101Ramd64-default] |   `-- Extracting gettext-runtime-0.19.4... done
    [101Ramd64-default] `-- Extracting binutils-2.25... done
    [101Ramd64-default] `-- Installing gcc-ecj-4.5...
    [101Ramd64-default] `-- Extracting gcc-ecj-4.5... done
    [101Ramd64-default] `-- Installing gmp-5.1.3_2...
    [101Ramd64-default] `-- Extracting gmp-5.1.3_2... done
    [101Ramd64-default] `-- Installing mpc-1.0.2_1...
    [101Ramd64-default] |   `-- Installing mpfr-3.1.2_2...
    [101Ramd64-default] |   `-- Extracting mpfr-3.1.2_2... done
    [101Ramd64-default] `-- Extracting mpc-1.0.2_1... done
    [101Ramd64-default] Extracting gcc-4.8.4... done
    Message for gcc-4.8.4:
     To ensure binaries built with this toolchain find appropriate versions
    of the necessary run-time libraries, you may want to link using

      -Wl,-rpath=/usr/local/lib/gcc48

    For ports leveraging USE_GCC, USES=compiler, or USES=fortran this happens
    transparently.
    ===>   Returning to build of sweep3d-2.2b
    ===>   sweep3d-2.2b depends on file: /usr/local/bin/as - found
    ===========================================================================
    ===================================================
    ===========================================================================
    ====>> Recording filesystem state for prebuild... done
    ===================================================
    ===>   sweep3d-2.2b depends on executable: gfortran48 - found
    ===>   sweep3d-2.2b depends on file: /usr/local/bin/as - found
    ===>  Configuring for sweep3d-2.2b
    configure: loading site script /usr/ports/Templates/config.site
    checking for a BSD-compatible install... /usr/bin/install -c -o root -g wheel
    checking whether build environment is sane... yes
    checking for gawk... (cached) /usr/bin/awk
    checking whether make sets $(MAKE)... yes
    checking for Fortran 77 compiler default output file name... a.out
    checking whether the Fortran 77 compiler works... yes
    checking whether we are cross compiling... no
    checking for suffix of executables... 
    checking for suffix of object files... o
    checking whether we are using the GNU Fortran 77 compiler... yes
    checking whether gfortran48 accepts -g... yes
    checking for gcc... cc
    checking whether we are using the GNU C compiler... yes
    checking whether cc accepts -g... yes
    checking for cc option to accept ANSI C... none needed
    checking for style of include used by make... GNU
    checking dependency style of cc... gcc3
    checking how to run the C preprocessor... cpp
    checking if cpp works as expected... cpp: warning: argument unused during compilation: '-E'
    yes

       Build type: sequential

       F77       = gfortran48
       FFLAGS    = -O -Wl,-rpath=/usr/local/lib/gcc48
       CPP       = cpp
       CC        = cc

    configure: WARNING: sequential build; specify --with-mpi or --with-pvm to build the parallel version of Sweep3D
    configure: creating ./config.status
    config.status: creating Makefile
    config.status: creating config.h
    config.status: executing depfiles commands
    ===========================================================================
    ===================================================
    ===>  Building for sweep3d-2.2b
    --- msg_stuff.f ---
    cpp  -P msg_stuff.cpp > msg_stuff.f
    --- all ---
    /usr/bin/make  all-am
    --- decomp.o ---
    --- flux_err.o ---
    --- inner_auto.o ---
    --- octant.o ---
    --- source.o ---
    --- driver.o ---
    --- initialize.o ---
    --- inner.o ---
    --- decomp.o ---
    gfortran48  -O -Wl,-rpath=/usr/local/lib/gcc48 -c -o decomp.o `test -f 'decomp.f' || echo './'`decomp.f
    --- flux_err.o ---
    gfortran48  -O -Wl,-rpath=/usr/local/lib/gcc48 -c -o flux_err.o `test -f 'flux_err.f' || echo './'`flux_err.f
    --- inner_auto.o ---
    gfortran48  -O -Wl,-rpath=/usr/local/lib/gcc48 -c -o inner_auto.o `test -f 'inner_auto.f' || echo './'`inner_auto.f
    --- octant.o ---
    gfortran48  -O -Wl,-rpath=/usr/local/lib/gcc48 -c -o octant.o `test -f 'octant.f' || echo './'`octant.f
    --- source.o ---
    gfortran48  -O -Wl,-rpath=/usr/local/lib/gcc48 -c -o source.o `test -f 'source.f' || echo './'`source.f
    --- driver.o ---
    gfortran48  -O -Wl,-rpath=/usr/local/lib/gcc48 -c -o driver.o `test -f 'driver.f' || echo './'`driver.f
    --- initialize.o ---
    gfortran48  -O -Wl,-rpath=/usr/local/lib/gcc48 -c -o initialize.o `test -f 'initialize.f' || echo './'`initialize.f
    --- inner.o ---
    gfortran48  -O -Wl,-rpath=/usr/local/lib/gcc48 -c -o inner.o `test -f 'inner.f' || echo './'`inner.f
    --- read_input.o ---
    gfortran48  -O -Wl,-rpath=/usr/local/lib/gcc48 -c -o read_input.o `test -f 'read_input.f' || echo './'`read_input.f
    --- sweep.o ---
    --- timers.o ---
    --- sweep.o ---
    gfortran48  -O -Wl,-rpath=/usr/local/lib/gcc48 -c -o sweep.o `test -f 'sweep.f' || echo './'`sweep.f
    --- timers.o ---
    source='timers.c' object='timers.o' libtool=no  depfile='.deps/timers.Po' tmpdepfile='.deps/timers.TPo'  depmode=gcc3 /bin/sh ./depcomp  cc -DHAVE_CONFIG_H -I. -I. -I.      -O2 -pipe  -fstack-protector -fno-strict-aliasing -c `test -f 'timers.c' || echo './'`timers.c
    --- msg_stuff.o ---
    gfortran48  -O -Wl,-rpath=/usr/local/lib/gcc48 -c -o msg_stuff.o `test -f 'msg_stuff.f' || echo './'`msg_stuff.f
    msg_stuff.f:160.30:

		call rcv_real(-1, y, 1, msgtag, info)                       
				  1
    Warning: Rank mismatch in argument 'value' at (1) (rank-1 and scalar)
    msg_stuff.f:166.26:

	     call snd_real(1, value, 1, msgtag, info)                       
			      1
    Warning: Rank mismatch in argument 'value' at (1) (rank-1 and scalar)
    msg_stuff.f:172.22:

	  call bcast_real(value, 1, msgtag, 1, info)                        
			  1
    Warning: Rank mismatch in argument 'value' at (1) (rank-1 and scalar)
    msg_stuff.f:195.29:

		call rcv_real(i, y, 1, msgtag, info)                        
				 1
    Warning: Rank mismatch in argument 'value' at (1) (rank-1 and scalar)
    msg_stuff.f:201.26:

	     call snd_real(1, value, 1, msgtag, info)                       
			      1
    Warning: Rank mismatch in argument 'value' at (1) (rank-1 and scalar)
    msg_stuff.f:207.22:

	  call bcast_real(value, 1, msgtag, 1, info)                        
			  1
    Warning: Rank mismatch in argument 'value' at (1) (rank-1 and scalar)
    msg_stuff.f:230.30:

		call rcv_real(-1, y, 1, msgtag, info)                       
				  1
    Warning: Type mismatch in argument 'value' at (1); passed INTEGER(4) to REAL(8)
    msg_stuff.f:236.26:

	     call snd_real(1, value, 1, msgtag, info)                       
			      1
    Warning: Type mismatch in argument 'value' at (1); passed INTEGER(4) to REAL(8)
    msg_stuff.f:242.21:

	  call bcast_int(value, 1, msgtag, 1, info)                         
			 1
    Warning: Rank mismatch in argument 'value' at (1) (rank-1 and scalar)
    --- sweep ---
    gfortran48  -O -Wl,-rpath=/usr/local/lib/gcc48  -Wl,-rpath=/usr/local/lib/gcc48  -L/usr/local/lib/gcc48 -B/usr/local/bin -fstack-protector -o sweep  decomp.o flux_err.o  inner_auto.o octant.o source.o  driver.o initialize.o inner.o  read_input.o sweep.o timers.o msg_stuff.o  
    ===========================================================================
    ====>> Checking for filesystem violations... done
    ===================================================
    ===>   sweep3d-2.2b depends on executable: gfortran48 - found
    ===========================================================================
    ====>> Recording filesystem state for prestage... done
    ===================================================
    ===>  Staging for sweep3d-2.2b
    ===>   sweep3d-2.2b depends on executable: gfortran48 - found
    ===>   Generating temporary packing list
    /bin/sh ./mkinstalldirs /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/bin
      install  -s -o root -g wheel -m 555 sweep /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/bin/sweep
    /bin/sh ./mkinstalldirs /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/bin
     install  -o root -g wheel -m 555 makeinput /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/bin/makeinput
    /bin/sh ./mkinstalldirs /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/share/sweep3d/examples
    mkdir -p -- /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/share/sweep3d/examples
     install  -o root -g wheel -m 0644 output.150.mpi_2x3 /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/share/sweep3d/examples/output.150.mpi_2x3
     install  -o root -g wheel -m 0644 output.150.single /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/share/sweep3d/examples/output.150.single
     install  -o root -g wheel -m 0644 output.50.pvm_2x3 /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/share/sweep3d/examples/output.50.pvm_2x3
     install  -o root -g wheel -m 0644 output.150.pvm_2x3 /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/share/sweep3d/examples/output.150.pvm_2x3
     install  -o root -g wheel -m 0644 output.50.mpi_2x3 /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/share/sweep3d/examples/output.50.mpi_2x3
     install  -o root -g wheel -m 0644 output.50.single /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/share/sweep3d/examples/output.50.single
     install  -o root -g wheel -m 0644 input.50 /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/share/sweep3d/examples/input.50
     install  -o root -g wheel -m 0644 input.150 /wrkdirs/usr/ports/benchmarks/sweep3d/work/stage/usr/local/share/sweep3d/examples/input.150
    ====> Compressing man pages (compress-man)
    ===========================================================================
    ====> Running Q/A tests (stage-qa)
    ====> Checking for pkg-plist issues (check-plist)
    ===> Parsing plist
    ===> Checking for items in STAGEDIR missing from pkg-plist
    ===> Checking for items in pkg-plist which are not in STAGEDIR
    ===> No pkg-plist issues found (check-plist)
    ====>> Checking for staging violations... done
    ===================================================
    ===>  Building package for sweep3d-2.2b
    ===========================================================================
    ===================================================
    ===========================================================================
    ====>> Recording filesystem state for preinst... done
    ===================================================
    ===>  Installing for sweep3d-2.2b
    ===>   sweep3d-2.2b depends on executable: gfortran48 - found
    ===>  Checking if sweep3d already installed
    ===>   Registering installation for sweep3d-2.2b
    [101Ramd64-default] Installing sweep3d-2.2b...
    ===========================================================================
    ====>> Checking shared library dependencies
     0x0000000000000001 (NEEDED)             Shared library: [libc.so.7]
     0x0000000000000001 (NEEDED)             Shared library: [libgcc_s.so.1]
     0x0000000000000001 (NEEDED)             Shared library: [libgfortran.so.3]
     0x0000000000000001 (NEEDED)             Shared library: [libm.so.5]
     0x0000000000000001 (NEEDED)             Shared library: [libquadmath.so.0]
    ===================================================
    ===>  Deinstalling for sweep3d
    ===>   Deinstalling sweep3d-2.2b
    Updating database digests format... done
    Checking integrity... done (0 conflicting)
    Deinstallation has been requested for the following 1 packages (of 0 packages in the universe):

    Installed packages to be REMOVED:
	    sweep3d-2.2b

    The operation will free 55 KiB.
    [101Ramd64-default] [1/1] Deinstalling sweep3d-2.2b...
    [101Ramd64-default] [1/1] Deleting files for sweep3d-2.2b... done
    ===========================================================================
    ====>> Checking for extra files and directories
