project('voxel-voxel', 'cpp', 'c')

cc = meson.get_compiler('c')
cxx = meson.get_compiler('cpp')

c_args = []
cpp_args = []
link_args = []
name_suffix = []
dependencies = []

if host_machine.system() == 'windows'
  # Raylib configuration
  cmake = import('cmake')
  raylib_opts = cmake.subproject_options()
  raylib_opts.set_install(false)
  raylib_opts.add_cmake_defines({
    'BUILD_EXAMPLES': 'OFF',
  })
  
  raylib_subproject = cmake.subproject('raylib', options: raylib_opts)
endif

dependencies += dependency('raylib_dep')

# Project files
inc_dirs = [include_directories(
  'src',
)]

is_freebsd = host_machine.system().startswith('freebsd')

if host_machine.system() == 'windows'
  dependencies += [
    cc.find_library('winmm'),
  ]
elif host_machine.system() == 'linux'  or is_freebsd
  dependencies += [
    cc.find_library('m'),
    cc.find_library('dl'),
  ]
  inc_dirs += include_directories(
    '/usr/local/include/',
  )
endif

sources = files(
  'src/main.cpp',
)

executable('voxel-voxel',
  sources,
  c_args: c_args,
  cpp_args: cpp_args,
  dependencies: dependencies,
  include_directories: inc_dirs,
  link_args: link_args,
  name_suffix: name_suffix,
)
