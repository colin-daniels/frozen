add_executable(test_main
        test_main.cpp
        test_set.cpp
        test_map.cpp
        test_unordered_set.cpp
        test_unordered_str_set.cpp
        test_unordered_map.cpp
        test_unordered_map_str.cpp)

set_target_properties(test_main PROPERTIES
        CXX_STANDARD 14
        CXX_STANDARD_REQUIRED ON
        CXX_EXTENSIONS OFF)

target_compile_options(test_main PRIVATE
        -O3 -march=native -Wall -Wextra -W -Werror -Wshadow)

target_link_libraries(test_main frozen)

add_test(main test_main)
