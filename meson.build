project('execinfo', 'c', version : '1.0.2', meson_version: '>=1.3.0')

pkg = import('pkgconfig')
prog_python = import('python').find_installation('python3')

compiler = meson.get_compiler('c')
dep_unwind = compiler.find_library('unwind', has_headers: ['libunwind.h'])
if not dep_unwind.found()
    dep_unwind = dependency('libunwind', required: true)
endif

execinfo = library('execinfo', 'execinfo.c',
                   dependencies : [ dep_unwind ],
                   version: meson.project_version(),
                   install : true,
                   pic: true)

install_headers('execinfo.h')

pkg.generate(execinfo, description : 'Standalone implementation of glibc\'s execinfo using libunwind')
