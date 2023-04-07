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
       
    !(https://user-images.githubusercontent.com/112895410/230633673-b757dfa8-aee0-4bda-be96-855720a19320.png)

      
