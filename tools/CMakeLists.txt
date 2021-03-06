# Copyright (c) 2015-2016 The Khronos Group Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and/or associated documentation files (the
# "Materials"), to deal in the Materials without restriction, including
# without limitation the rights to use, copy, modify, merge, publish,
# distribute, sublicense, and/or sell copies of the Materials, and to
# permit persons to whom the Materials are furnished to do so, subject to
# the following conditions:
#
# The above copyright notice and this permission notice shall be included
# in all copies or substantial portions of the Materials.
#
# MODIFICATIONS TO THIS FILE MAY MEAN IT NO LONGER ACCURATELY REFLECTS
# KHRONOS STANDARDS. THE UNMODIFIED, NORMATIVE VERSIONS OF KHRONOS
# SPECIFICATIONS AND HEADER INFORMATION ARE LOCATED AT
#    https://www.khronos.org/registry/
#
# THE MATERIALS ARE PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
# EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
# MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
# IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
# CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
# TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
# MATERIALS OR THE USE OR OTHER DEALINGS IN THE MATERIALS.

if (NOT ${SPIRV_SKIP_EXECUTABLES})
  set(SPIRV_INSTALL_TARGETS spirv-as spirv-dis spirv-val)

  add_executable(spirv-as ${CMAKE_CURRENT_SOURCE_DIR}/as/as.cpp)
  spvtools_default_compile_options(spirv-as)
  target_link_libraries(spirv-as PRIVATE ${SPIRV_TOOLS})
  target_include_directories(spirv-as
    PRIVATE ${spirv-tools_BINARY_DIR} ${spirv-tools_SOURCE_DIR}/source)

  add_executable(spirv-dis ${CMAKE_CURRENT_SOURCE_DIR}/dis/dis.cpp)
  spvtools_default_compile_options(spirv-dis)
  target_link_libraries(spirv-dis PRIVATE ${SPIRV_TOOLS})
  target_include_directories(spirv-dis PRIVATE ${spirv-tools_BINARY_DIR})

  add_executable(spirv-val ${CMAKE_CURRENT_SOURCE_DIR}/val/val.cpp)
  spvtools_default_compile_options(spirv-val)
  target_link_libraries(spirv-val PRIVATE ${SPIRV_TOOLS})
  target_include_directories(spirv-val
    PRIVATE ${spirv-tools_BINARY_DIR} ${spirv-tools_SOURCE_DIR}/source)

  install(TARGETS ${SPIRV_INSTALL_TARGETS}
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib)
endif()
