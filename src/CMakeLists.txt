set(LIB_NAME "CasperSDK")

include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}/include
    ${CMAKE_CURRENT_SOURCE_DIR}/include/JsonRpc
    ${CMAKE_CURRENT_SOURCE_DIR}/include/JsonRpc/Connection
    ${CMAKE_CURRENT_SOURCE_DIR}/include/JsonRpc/ResultTypes
    ${CMAKE_CURRENT_SOURCE_DIR}/include/Types
    ${CMAKE_CURRENT_SOURCE_DIR}/include/Utils
    ${CMAKE_CURRENT_SOURCE_DIR}/../lib/cryptopp
    ${CMAKE_CURRENT_SOURCE_DIR}/../lib/
)

add_library(${LIB_NAME} SHARED CasperClient.cpp include/Types/CLValue.cpp include/Types/CLType.cpp include/Types/CLTypeParsed.cpp include/Types/GlobalStateKey.cpp include/Types/URef.cpp include/Types/ED25519Key.cpp include/Types/Secp256k1Key.cpp include/Utils/CryptoUtil.cpp include/Utils/StringUtil.cpp include/Utils/CEP57Checksum.cpp include/Types/CLConverter.cpp include/Types/Deploy.cpp include/ByteSerializers/BaseByteSerializer.cpp)

find_package(OpenSSL REQUIRED)

target_link_libraries(${LIB_NAME} ${CMAKE_CURRENT_SOURCE_DIR}/../lib/cryptopp/libcryptopp.a OpenSSL::SSL)
