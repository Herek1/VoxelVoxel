project('voxel-voxel', 'cpp')

cxx = meson.get_compiler('cpp')

c_args = []
cpp_args = []
link_args = []
name_suffix = []
dependencies = []

# General configuration
if host_machine.system() == 'windows'
  dependencies += [
    cc.find_library('winmm'),
  ]
elif host_machine.system() == 'linux'
  dependencies += [
    cc.find_library('m'),
    cc.find_library('dl'),
  ]
endif

# Project files
inc_dir = include_directories(
  'src',
)

sources = files(
  'src/main.cpp',
)

executable('voxel-voxel',
  sources,
  c_args: c_args,
  cpp_args: cpp_args,
  dependencies: dependencies,
  include_directories: inc_dir,
  link_args: link_args,
  name_suffix: name_suffix,
)
