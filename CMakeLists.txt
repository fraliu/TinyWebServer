# 设置项目名称
project(WebServer)

# 禁用优化并开启调试信息
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O0 -g")

## 根据DEBUG变量设置编译选项
#if(DEBUG)
#    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g") # 调试模式
#else()
#    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2") # 发布模式
#endif()

# 查找源文件并添加到可执行文件中
set(SOURCE_FILES
        main.cpp
        ./timer/lst_timer.cpp
        ./http/http_conn.cpp
        ./log/log.cpp
        ./CGImysql/sql_connection_pool.cpp
        webserver.cpp
        config.cpp
)

# 添加包含目录（如果需要）
include_directories(
        ./timer
        ./http
        ./log
        ./CGImysql
)

# 创建可执行文件
add_executable(server ${SOURCE_FILES})

# 链接库
target_link_libraries(server pthread mysqlclient)