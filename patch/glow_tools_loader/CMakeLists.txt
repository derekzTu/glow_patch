find_package(Threads REQUIRED)
add_executable(cifar10
                 cifar10.cpp)
target_link_libraries(cifar10
                      PRIVATE
                        Backends
                        ExecutionEngine
                        Graph
                        IR
                        Support
			Threads::Threads
                        LLVMSupport)

add_executable(mnist
                 mnist.cpp)
target_link_libraries(mnist
                      PRIVATE
                        Backends
                        ExecutionEngine
                        Graph
                        IR
                        Optimizer
                        Support
			Threads::Threads
                        LLVMSupport)

add_executable(ptb
                 ptb.cpp)
target_link_libraries(ptb
                      PRIVATE
                        Backends
                        ExecutionEngine
                        Graph
                        IR
                        Support
			Threads::Threads
                        LLVMSupport)

add_executable(char-rnn
                 char-rnn.cpp)
target_link_libraries(char-rnn
                      PRIVATE
                        Backends
                        ExecutionEngine
                        Graph
                        IR
                        Optimizer
			Threads::Threads
                        Support)

add_executable(fr2en
                 fr2en.cpp)
target_link_libraries(fr2en
                      PRIVATE
                        Base
                        ExecutionEngine
                        IR
                        Optimizer
                        Quantization
                        Support
			Threads::Threads
                        LLVMSupport)

add_executable(lenet-loader
                 lenet-loader.cpp)
target_link_libraries(lenet-loader
                      PRIVATE
                        ExecutionEngine
                        Graph
                        Importer
			Threads::Threads
                        Support)

if(GLOW_WITH_CPU)
  add_executable(resnet-verify
                   resnet-verify.cpp)
  target_link_libraries(resnet-verify
                        PRIVATE
                          ExecutionEngine
                          Graph
			  Threads::Threads
                          Importer)

  add_executable(resnet-runtime
                   resnet-runtime.cpp)
  target_link_libraries(resnet-runtime
                        PRIVATE
                          Backends
                          ExecutionContext
                          ExecutionEngine
                          HostManager
                          Partitioner
                          Graph
                          Importer
			  Threads::Threads
                          Optimizer)
  target_include_directories(resnet-runtime PUBLIC ${CMAKE_SOURCE_DIR}/lib)

  add_executable(tracing-compare
                   tracing-compare.cpp)
  target_link_libraries(tracing-compare
                        PRIVATE
                          Backend
                          Backends
                          ExecutionEngine
                          Graph
                          Importer
			  Threads::Threads
                          Optimizer)
endif()


if(GLOW_WITH_BUNDLES)
  add_subdirectory(bundles)
endif()
