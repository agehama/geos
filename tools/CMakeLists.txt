#################################################################################
#
# GEOS tools (geos-config) build configuration for CMake build system
#
# Copyright (C) 2009 Mateusz Loskot <mateusz@loskot.net>
#
# This is free software; you can redistribute and/or modify it under
# the terms of the GNU Lesser General Public Licence as published
# by the Free Software Foundation. 
# See the COPYING file for more information.
#
#################################################################################

if(UNIX OR MINGW)

  if(APPLE AND GEOS_ENABLE_MACOSX_FRAMEWORK AND GEOS_ENABLE_MACOSX_FRAMEWORK_UNIXCOMPAT)
    set(installdest GEOS.framework/Versions/${VERSION_MAJOR}/unix/bin)
    set(prefix ${CMAKE_INSTALL_PREFIX}/GEOS.framework/Versions/${VERSION_MAJOR}/unix)
  elseif(APPLE AND GEOS_ENABLE_MACOSX_FRAMEWORK)
    # just a dummy so installdest not set
    # want geos-config only for Mac unix build or framework+unixcompat
  else()
    set(installdest bin)
    set(prefix ${CMAKE_INSTALL_PREFIX})
  endif()

  set(exec_prefix ${prefix}/bin)
  set(libdir ${prefix}/lib)
  
  if(installdest)
    configure_file(${CMAKE_CURRENT_SOURCE_DIR}/geos-config.in
                   ${CMAKE_CURRENT_BINARY_DIR}/geos-config @ONLY)
endif()

endif()
