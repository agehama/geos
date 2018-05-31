#################################################################################
#
# GEOS C++ library build configuration for CMake build system
#
# Copyright (C) 2009 Mateusz Loskot <mateusz@loskot.net>
#
# This is free software; you can redistribute and/or modify it under
# the terms of the GNU Lesser General Public Licence as published
# by the Free Software Foundation. 
# See the COPYING file for more information.
#
#################################################################################

#################################################################################
# Install/Uninstall
#################################################################################

# There is a builtin cmake way to get headers in the right location
# for OS X framework, but it's not practical this complex tree

if(APPLE AND GEOS_ENABLE_MACOSX_FRAMEWORK)
  set(installdest GEOS.framework/Versions/${VERSION_MAJOR}/Headers)
else()
  set(installdest include/geos)
endif()

#################################################################################
# Group source files for IDE source explorers (e.g. Visual Studio)
#################################################################################
GenerateSourceGroups(include)
