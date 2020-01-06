# Testing protobuf files that are deeply hierarchical
# and must preserve their path segments in output files
# because protoc will always put it in there.

simple_ch = custom_target(
  'simple.pb.[ch]',
  input    : ['com/mesonbuild/simple.proto'],
  output   : ['simple.pb.cc', 'simple.pb.h'],
  command  : [protoc, '--proto_path=@CURRENT_SOURCE_DIR@', '--cpp_out=@OUTDIR@', '@INPUT@'],
)

complex_ch = custom_target(
  'complex.pb.[ch]',
  input    : ['com/mesonbuild/subsite/complex.proto'],
  output   : ['complex.pb.cc', 'complex.pb.h'],
  command  : [protoc, '--proto_path=@CURRENT_SOURCE_DIR@', '--cpp_out=@OUTDIR@', '@INPUT@'],
)

e = executable('pathprog', 'pathprog.cpp', simple_ch, complex_ch,
  override_options : ['unity=off'],
  dependencies : dep)
test('pathprog', e)
