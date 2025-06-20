project('nvjpg', ['c', 'cpp'], version: '1.1.0',
    default_options: [
        'buildtype=release',
        'default_library=static',
        'b_ndebug=if-release',
        'b_lto=false',
        'strip=false',
        'warning_level=2',
        'c_std=gnu11',
        'cpp_std=gnu++20',
    ],
)

nvj_inc = include_directories('include')

nvj_src = files(
    'lib/decoder.cpp',
    'lib/image.cpp',
    'lib/surface.cpp',
)

nvj_lib = library('oss-nvjpg', nvj_src, include_directories: nvj_inc)

nvj_dep = declare_dependency(include_directories: nvj_inc, link_with: nvj_lib)

ex1 = executable('render-rgb',
    'examples/render-rgb.cpp',
    dependencies: [nvj_dep, dependency('SDL2', required: true)],
    build_by_default: false,
)

ex2 = executable('render-rgb-downscale',
    'examples/render-rgb-downscale.cpp',
    dependencies: [nvj_dep, dependency('SDL2', required: true)],
    build_by_default: false,
)

ex3 = executable('render-yuv',
    'examples/render-yuv.cpp',
    dependencies: [nvj_dep, dependency('SDL2', required: true)],
    build_by_default: false,
)

alias_target('examples', ex1, ex2, ex3)
