#
#  For more information, please see: http://software.sci.utah.edu
#
#  The MIT License
#
#  Copyright (c) 2020 Scientific Computing and Imaging Institute,
#  University of Utah.
#
#  Permission is hereby granted, free of charge, to any person obtaining a
#  copy of this software and associated documentation files (the "Software"),
#  to deal in the Software without restriction, including without limitation
#  the rights to use, copy, modify, merge, publish, distribute, sublicense,
#  and/or sell copies of the Software, and to permit persons to whom the
#  Software is furnished to do so, subject to the following conditions:
#
#  The above copyright notice and this permission notice shall be included
#  in all copies or substantial portions of the Software.
#
#  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS
#  OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
#  FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL
#  THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
#  LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
#  FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
#  DEALINGS IN THE SOFTWARE.
#


# CMakeLists.txt for Packages/Teem/Dataflow/Modules/Converters

SET(Modules_Legacy_Teem_Converters_SRCS
  ConvertNrrdToField.cc
  ConvertNrrdToMatrix.cc
  SplitFieldIntoNrrdData.cc
)

SET(Modules_Legacy_Teem_Converters_HEADERS
  ConvertNrrdToField.h
  ConvertNrrdToMatrix.h
  SplitFieldIntoNrrdData.h
  share.h
)

SCIRUN_ADD_LIBRARY(Modules_Legacy_Teem_Converters
  ${Modules_Legacy_Teem_Converters_SRCS}
  ${Modules_Legacy_Teem_Converters_HEADERS}
)

TARGET_LINK_LIBRARIES(Modules_Legacy_Teem_Converters
  Dataflow_Network
  Core_Datatypes
  Core_Datatypes_Legacy_Nrrd
  Core_Algorithms_Legacy_Converter #TODO: remove link
  ${SCI_TEEM_LIBRARY}
)

IF(BUILD_SHARED_LIBS)
  ADD_DEFINITIONS(-DBUILD_Modules_Legacy_Teem_Converters)
ENDIF(BUILD_SHARED_LIBS)

SCIRUN_ADD_TEST_DIR(Tests)
