cmake_minimum_required (VERSION 3.11)
project(saleae-logic-SimpleParallelNoClock-Analyzer)

# custom CMake Modules are located in the cmake directory.
set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)

include(ExternalAnalyzerSDK)

set(SOURCES 
source/SimpleParallelNoClockAnalyzer.cpp
source/SimpleParallelNoClockAnalyzer.h
source/SimpleParallelNoClockAnalyzerResults.cpp
source/SimpleParallelNoClockAnalyzerResults.h
source/SimpleParallelNoClockAnalyzerSettings.cpp
source/SimpleParallelNoClockAnalyzerSettings.h
source/SimpleParallelNoClockSimulationDataGenerator.cpp
source/SimpleParallelNoClockSimulationDataGenerator.h
)

add_library(saleae-logic-SimpleParallelNoClock-Analyzer SHARED ${SOURCES})
target_link_libraries(saleae-logic-SimpleParallelNoClock-Analyzer PRIVATE Saleae::AnalyzerSDK)

if(MSVC)
    install(TARGETS saleae-logic-SimpleParallelNoClock-Analyzer RUNTIME DESTINATION "Analyzers")
else()
    install(TARGETS saleae-logic-SimpleParallelNoClock-Analyzer LIBRARY DESTINATION "Analyzers")
endif()

set_post_build_destination(saleae-logic-SimpleParallelNoClock-Analyzer)
