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


SET(Modules_Basic_SRCS
  AsyncPortTestModule.cc
  AsyncStreamingTestModule.cc
  DynamicPortTester.cc
  NeedToExecuteTester.cc
  ReceiveComplexScalar.cc
  PrintDatatype.cc
  SendComplexScalar.cc
  ChooseInput.cc
  PortFeedbackTestModules.cc
  PlaceholderModule.cc
  LoggingTester.cc
  CompositeModuleWithStaticPorts.cc
  CompositeModuleWithTypedStaticPorts.cc
  SimulationReaderBaseModule.cc
)

SET(Modules_Basic_HEADERS
  AsyncPortTestModule.h
  AsyncStreamingTestModule.h
  DynamicPortTester.h
  NeedToExecuteTester.h
  ReceiveComplexScalar.h
  PrintDatatype.h
  SendComplexScalar.h
  ChooseInput.h
  PortFeedbackTestModules.h
  LoggingTester.h
  PlaceholderModule.h
  CompositeModuleWithStaticPorts.h
  CompositeModuleWithTypedStaticPorts.h
  SimulationReaderBaseModule.h
  share.h
)

SCIRUN_ADD_LIBRARY(Modules_Basic
  ${Modules_Basic_HEADERS}
  ${Modules_Basic_SRCS}
)

TARGET_LINK_LIBRARIES(Modules_Basic
  Core_Datatypes
  Core_Datatypes_Legacy_Field
  Algorithms_Field
  Dataflow_Network
  Core_Serialization_Network
)

IF(BUILD_SHARED_LIBS)
  ADD_DEFINITIONS(-DBUILD_Modules_Basic)
ENDIF(BUILD_SHARED_LIBS)

SCIRUN_ADD_TEST_DIR(Tests)
