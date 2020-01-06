# Generated source defined in one directory but
# used in another.

e = executable('sideprog', 'sideprog.cpp', simple_ch, complex_ch,
  override_options : ['unity=off'],
  include_directories : ['../withpath'],
  dependencies : dep)
test('sideprog', e)
