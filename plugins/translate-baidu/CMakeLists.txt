# 百度翻译插件：复用翻译共享层，按开放平台签名协议调用通用翻译接口

qt_add_plugin(mark-shot-translate-baidu
    SHARED
    baidu_translate_config.cpp
    baidu_translate_config.h
    baidu_translate_plugin.cpp
    baidu_translate_plugin.h
    baidu_translate_request.cpp
    baidu_translate_request.h
    baidu_translate_signer.cpp
    baidu_translate_signer.h
)

target_include_directories(mark-shot-translate-baidu PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_SOURCE_DIR}/plugin-sdk
)
target_link_libraries(mark-shot-translate-baidu
    PRIVATE
        mark-shot-translate-common
        Qt6::Core
        Qt6::Network
)

install(TARGETS mark-shot-translate-baidu
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}/mark-shot/plugins
        RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR}/mark-shot/plugins)

message(STATUS "mark-shot: translate-baidu plugin enabled")
