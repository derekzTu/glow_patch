find_package(Threads REQUIRED)
add_executable(image-classifier
  Loader.cpp
  ImageClassifier.cpp)

target_link_libraries(image-classifier
                      PRIVATE
                        Backends
                        Base
                        Converter
                        ExecutionEngine
                        HostManager
                        Graph
                        Importer
                        Optimizer
                        Quantization
			Threads::Threads
                        LLVMSupport)

add_executable(text-translator
  Loader.cpp
  TextTranslator.cpp)

target_link_libraries(text-translator
                      PRIVATE
                        Backends
                        Base
                        Converter
                        Graph
                        HostManager
                        Importer
                        ExecutionEngine
                        Optimizer
                        Quantization
			Threads::Threads
                        LLVMSupport)

add_executable(model-runner
  Loader.cpp
  ModelRunner.cpp)

target_link_libraries(model-runner
                      PRIVATE
                        Backends
                        Base
                        Converter
                        Graph
                        HostManager
                        Importer
                        ExecutionEngine
                        Optimizer
                        Quantization
			Threads::Threads
                        LLVMSupport)
