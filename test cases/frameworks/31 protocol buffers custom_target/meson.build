project('protocol buffer test', 'cpp', default_options: ['cpp_std=c++11'])

protoc = find_program('protoc', required : false)
dep = dependency('protobuf', required : false)

if not protoc.found() or not dep.found()
  error('MESON_SKIP_TEST: protoc tool and/or protobuf pkg-config dependency not found')
endif

generated = custom_target(
  'defs.pb.[ch]',
  input    : ['defs.proto'],
  output   : ['defs.pb.cc', 'defs.pb.h'],
  # @CURRENT_SOURCE_DIR@ is not documented for custom_target?, but works.
  command  : [protoc, '--proto_path=@CURRENT_SOURCE_DIR@', '--cpp_out=@OUTDIR@', '@INPUT@'],
)

e = executable('prog', 'main.cpp', generated, dependencies : dep)
test('prototest', e)

subdir('asubdir')
subdir('withpath')
subdir('sidedir')
