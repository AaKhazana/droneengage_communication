
file(GLOB folder_src "./*.cpp")
file(GLOB folder_helpers "./helpers/*.cpp")
file(GLOB folder_common "./comm_server/*.cpp")
file(GLOB folder_uavos "./de_broker/*.cpp")
file(GLOB folder_general_mission_planner "./de_general_mission_planner/*.cpp")

set(files ${folder_src} ${folder_common} ${folder_helpers} ${folder_uavos} ${folder_general_mission_planner})


add_executable( OUTPUT_BINARY ${files})

set_target_properties( OUTPUT_BINARY 
                PROPERTIES 
                    OUTPUT_NAME "de_comm"
                    SUFFIX ".so"
                )

set(CMAKE_FIND_LIBRARY_SUFFIXES ".a")
include_directories(./3rdparty)
 target_link_libraries(OUTPUT_BINARY   OpenSSL::Crypto OpenSSL::SSL CURL::libcurl Threads::Threads )
 target_link_libraries(OUTPUT_BINARY ${Boost_LIBRARY_DIRS}/libboost_coroutine.a)
 target_link_libraries(OUTPUT_BINARY ${Boost_LIBRARY_DIRS}/libboost_thread.a)
 target_link_libraries(OUTPUT_BINARY ${Boost_LIBRARY_DIRS}/libboost_system.a)
 target_link_libraries(OUTPUT_BINARY ${Boost_LIBRARY_DIRS}/libboost_chrono.a)
 target_link_libraries(OUTPUT_BINARY ${Boost_LIBRARY_DIRS}/libboost_context.a)

