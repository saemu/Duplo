
set(SRCS
    ArgumentParser.cpp
    CstyleCommentsFilter.cpp
    CstyleUtils.cpp
    Duplo.cpp
    FileTypeBase.cpp
    FileTypeFactory.cpp
    FileType_C.cpp
    FileType_CS.cpp
    FileType_S.cpp
    FileType_Unknown.cpp
    FileType_VB.cpp
    HashUtil.cpp
    Main.cpp
    NoopLineFilter.cpp
    Options.cpp
    SourceFile.cpp
    SourceLine.cpp
    StringUtil.cpp
    TextFile.cpp
)

set(HDRS
    ArgumentParser.h
    CstyleCommentsFilter.h
    CstyleUtils.h
    Duplo.h
    FileTypeBase.h
    FileTypeFactory.h
    FileType_C.h
    FileType_CS.h
    FileType_S.h
    FileType_Unknown.h
    FileType_VB.h
    Fwd.h
    HashUtil.h
    IFileType.h
    ILineFilter.h
    NoopLineFilter.h
    Options.h
    SourceFile.h
    SourceLine.h
    StringUtil.h
    TextFile.h
)

add_executable(duplo)
target_sources(duplo PRIVATE ${SRCS} ${HDRS})
target_compile_features(duplo PRIVATE cxx_std_17)


target_compile_definitions(duplo PRIVATE
                           DUPLO_VERSION=${DUPLO_VERSION}
                           )

target_compile_options(duplo PRIVATE
                       $<$<CXX_COMPILER_ID:MSVC>:/W4;/WX>
                       $<$<CXX_COMPILER_ID:GNU,Clang,AppleClang>:-Wall;-Wextra;-fstack-protector-all>
                       $<$<CXX_COMPILER_ID:GNU,Clang,AppleClang>:$<$<CONFIG:Debug>:-g;-O0;-fno-inline>>
                       $<$<CXX_COMPILER_ID:GNU,Clang,AppleClang>:$<$<CONFIG:Release>:-O3>>
                       )

target_link_options(duplo PRIVATE
                    $<$<CXX_COMPILER_ID:GNU>:-static-libgcc;-static-libstdc++>
                    $<$<CXX_COMPILER_ID:GNU,Clang>:-static>)
