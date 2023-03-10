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

cd your-project
git clone https://github.com/tp-labs/lab03.git
cd
cd your-project/lab03
git config user.name "ne-kit-28"
git config user.email "nickit.nic098@yandex.ru"
git remote set-url origin https://ne-ki-28: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@github.com/ne-kit-28/lab03.git
mkdir formatter_lib
cd formatter_lib
cat > CMakeList.txt
sudo apt  install cmake  # version 3.22.1-1ubuntu1.22.04.1
cmake --version

В CMake:
cmake_minimum_required(VERSION 3.22.1)          
project(formatter_lib)
add_library(formatter STATIC formatter.cpp)


cmake -H. -B_build
cmake --build _build

2 задание 
cd
cd your-project/lab03/formatter_ex_lib
cat > CMakeLists.txt

cmake_minimum_required(VERSION 3.20)
project(formatter_ex)
include_directories(../formatter_lib)
add_subdirectory(../formatter_lib formatter)
add_library(formatter_ex STATIC formatter_ex.cpp)
target_link_libraries(formatter_ex formatter)

cmake -H. -B_build
cmake --build _build

3 задание
cd ../hello_world_application
cat > CMakeLists.txt

cmake_minimum_required(VERSION 3.20)
project(hello_world)
add_executable(hello_world hello_world.cpp)
include_directories(../formatter_ex_lib)
add_subdirectory(../formatter_ex_lib formatter_ex)
target_link_libraries(hello_world formatter_ex)

cmake -H. -B_build
cmake --build _build
cmake --build _build --target hello_world
./_build/hello_world

cd ../solver_application
cat > CMakeLists.txt

cmake_minimum_required(VERSION 3.20)
project(solver)
add_executable(solver equation.cpp)
include_directories(../formatter_ex_lib ../solver_lib)
add_subdirectory(../formatter_ex_lib formatter_ex)
add_subdirectory(../formatter_lib formatter_lib)
add_subdirectory(../solver_lib solver_lib)
target_link_libraries(solver formatter_ex solver_lib)

cd ../solver_lib
cat > CMakeLists.txt

cmake_minimum_required(VERSION 3.20)
project(solver_lib)
add_library(solver_lib STATIC solver.cpp)

cd ../solver_application

cmake -H. -B_build
cmake --build _build
cmake --build _build --target solver
./_build/solver

