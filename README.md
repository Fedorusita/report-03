# report-03
**1. Сначала выполним обычные команды для создания локального репозитория и первого коммита**  
**2. Перейдем на новую ветку**  
      $ git checkout -b lab  
      $ cat >> CMakeLists.txt << EOF  
      > EOF  
      $ nano CMakeLists.txt  
**3.  Файл CMakeLists имеет следующее содержание**  
    ```cmake_minimum_required(VERSION 3.4)```  
    ```set(CMAKE_CXX_STANDARD 11)```      
    ```set(CMAKE_CXX_STANDARD_REQUIRED ON)```   
    ```project(formatter)```    
    ```add_library(formatter STATIC formatter.cpp)```    
    ```target_include_directories(formatter PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})```   
**4. Аналогично создадим файлы .h / .cpp**   
**5. Проверим работоспособность CMake**  
    ```$ cmake -H. -B_build  
       $ cmake --build _build```  
******

**1. Выполним схожие команды, только другое содержание CMake**  
     cmake_minimum_required(VERSION 3.4)  

set(CMAKE_CXX_STANDARD 11)  
set(CMAKE_CXX_STANDARD_REQUIRED ON)  

project(formatter_ex)  

add_library(formatter_ex STATIC formatter_ex.cpp)  

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_lib ${CMAKE_CURRENT_BINARY_DIR}/formatter) 
target_include_directories(formatter_ex PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})  

target_link_libraries(formatter_ex formatter)  

******

**1. CMake solver_lib**  
cmake_minimum_required(VERSION 3.4)  

set(CMAKE_CXX_STANDARD 11)  
set(CMAKE_CXX_STANDARD_REQUIRED ON)  

project(solver_lib)  

add_library(solver_lib STATIC solver.cpp)  
target_include_directories(solver_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})  


*******

**1.CMake solver_application**
cmake_minimum_required(VERSION 3.4)  

set(CMAKE_CXX_STANDARD 11)  
set(CMAKE_CXX_STANDARD_REQUIRED ON)  

project(solver_example)  

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib ${CMAKE_CURRENT_BINARY_DIR}/solver_lib)  
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib ${CMAKE_CURRENT_BINARY_DIR}/formatter_ex)  

add_executable(example equation.cpp)  

target_link_libraries(example solver_lib formatter_ex)  

**2.Работа программы**  
```$ cmake --build _build --target example```    
```$ ./_build/example```  

******

**1.

  

      
