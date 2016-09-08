project(lib1)

aux_source_directory("." ${PROJECT_NAME}_sources)

message("Sources for project ${PROJECT_NAME}: ${${PROJECT_NAME}_sources}")
