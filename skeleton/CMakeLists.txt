# Created by the script cgal_create_cmake_script
# This is the CMake script for compiling a CGAL application.


project( skeleton_ )

cmake_minimum_required(VERSION 2.8.10)

set(CMAKE_CXX_STANDARD 14)

find_package(CGAL QUIET COMPONENTS Core )

if ( CGAL_FOUND )

  include( ${CGAL_USE_FILE} )

  #-------------------------------------------------------
  # Include Eigen3
  find_package(Eigen3 3.0.91) 
  if(EIGEN3_FOUND) 
    include( ${EIGEN3_USE_FILE} ) 
  else() 
    message(STATUS "NOTICE: Eigen library is not found.") 
  endif() 
  #-------------------------------------------------------

  include( CGAL_CreateSingleSourceCGALProgram )

  create_single_source_cgal_program( "skeleton.cpp" )

else()
  
    message(STATUS "This program requires the CGAL library, and will not be compiled.")
  
endif()

