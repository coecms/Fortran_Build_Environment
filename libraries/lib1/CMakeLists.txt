project(lib1)

file(GLOB ${PROJECT_NAME}_sources "*.f90")

message("Sources for project ${PROJECT_NAME}: ${${PROJECT_NAME}_sources}")

add_library(${PROJECT_NAME} ${${PROJECT_NAME}_sources})
