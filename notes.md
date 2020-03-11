# cmd/openapi2proto/main.go
* build options for encoder and compiler
* openapi2proto.Transpile

# /transpiler.go
* Transpile is a convenience function that takes an OpenAPI spec file and transpiles it into a Protocol Buffers v3 declaration.
* openapi.LoadFile(srcFn)
* compiler.Compile(s, compilerOptions...)
* protobuf.NewEncoder(dst, encoderOptions...).Encode(p) // encode protocol buffers to text
