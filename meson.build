project(
  'radxa-penta',
  'cpp',
  version : '0.1',
  meson_version : '>= 1.3.0',
  default_options : ['warning_level=3', 'cpp_std=c++23'],
)

dependencies = [
]

exe = executable(
  'radxa-penta',
  'main.cpp',
  dependencies : dependencies,
)

test('basic', exe)
