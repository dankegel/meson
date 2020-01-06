# Testing protobuf files that are deeply hierarchical
# and must preserve their path segments in output files
# because protoc will always put it in there.

simple_ch = custom_target(
  'simple.pb.[ch]',
  input    : ['com/mesonbuild/simple.proto'],
  output   : ['com/mesonbuild/simple.pb.cc', 'com/mesonbuild/simple.pb.h'],
  # using @OUTDIR@ here results in com/mesonbuild being repeated
  command  : [protoc, '--proto_path=@CURRENT_SOURCE_DIR@', '--cpp_out=withpath', '@INPUT@'],
)

complex_ch = custom_target(
  'complex.pb.[ch]',
  input    : ['com/mesonbuild/subsite/complex.proto'],
  output   : ['com/mesonbuild/subsite/complex.pb.cc', 'com/mesonbuild/subsite/complex.pb.h'],
  # using @OUTDIR@ here results in com/mesonbuild/subsite being repeated
  command  : [protoc, '--proto_path=@CURRENT_SOURCE_DIR@', '--cpp_out=withpath', '@INPUT@'],
)

e = executable('pathprog', 'pathprog.cpp', simple_ch, complex_ch,
  override_options : ['unity=off'],
  dependencies : dep)
test('pathprog', e)
