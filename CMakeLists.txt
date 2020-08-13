
cmake_minimum_required (VERSION 3.12 FATAL_ERROR)

project(nifty_site_manager LANGUAGES CXX)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/bin")

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

add_executable(
    nsm
    nsm.cpp
    ConsoleColor.cpp
    DateTimeInfo.cpp
    Directory.cpp
    Expr.cpp
    ExprtkFns.cpp
    Filename.cpp
    FileSystem.cpp
    Getline.cpp
    GitInfo.cpp
    hashtk/HashTk.cpp
    Lolcat.cpp
    LuaFns.cpp
    Lua.cpp
    NumFns.cpp
    Pagination.cpp
    Parser.cpp
    Path.cpp
    ProjectInfo.cpp
    Quoted.cpp
    StrFns.cpp
    SystemInfo.cpp
    Title.cpp
    TrackedInfo.cpp
    Variables.cpp
    WatchList.cpp
    )
target_compile_features(nsm PRIVATE cxx_std_11)
target_link_libraries(nsm PRIVATE Threads::Threads)
target_link_options(nsm PRIVATE -LLua-5.3/src -llua)
target_compile_options(nsm PRIVATE -Wall -Wextra -pedantic)
target_compile_definitions(nsm PRIVATE exprtk_disable_caseinsensitivity __BUNDLED__ __LUA_VERSION_5_3__)
