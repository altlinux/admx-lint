find_package(XercesC REQUIRED)
INCLUDE_DIRECTORIES(${XercesC_INCLUDE_DIR})

find_package(Boost 1.40 COMPONENTS program_options REQUIRED)
INCLUDE_DIRECTORIES(${Boost_INCLUDE_DIR})

set(HEADERS
    basetypes.h
    policydefinitionfiles.h
    policydefinitions.h
)

set(SOURCES
    main.cpp
    basetypes.cpp
    policydefinitionfiles.cpp
    policydefinitions.cpp
)

add_executable(${PROJECT_NAME} ${SOURCES})

set_target_properties(${PROJECT_NAME} PROPERTIES OUTPUT_NAME admx-lint)
install(TARGETS ${PROJECT_NAME} DESTINATION bin PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE)

target_link_libraries(${PROJECT_NAME} ${XercesC_LIBRARIES} ${Boost_LIBRARIES})
