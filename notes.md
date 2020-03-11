# cmd/openapi2proto/main.go
* build options for encoder and compiler
* openapi2proto.Transpile

# /transpiler.go
* Transpile is a convenience function that takes an OpenAPI spec file and transpiles it into a Protocol Buffers v3 declaration.
* openapi.LoadFile(srcFn): decode -> map[interface{}]interace{} -> map[string]interface{}
* compiler.Compile(s, compilerOptions...)
* protobuf.NewEncoder(dst, encoderOptions...).Encode(p) // encode protocol buffers to text

# openapi.LoadFile
## openapi/openapi.go
* LoadFile loads an OpenAPI spec from a file, or a remote HTTP(s) location. This function also resolves any external references.
* resovled external references --> interface{} --> Re-encode (Encode + Unmarshal, inline all $refs) --> openapi.Spec

## openapi/external.go
* Resolve external refs and return interface{} which is the type yaml/json decoder returns
* YAML serializers are really, really, really annoying in that it decodes maps into map[interface{}]interface{} instead of map[string]interface{}. Keys behind the interface{} could be strings, ints, etc, so we convert them into map types that we can actually handle, namely map[string]interface{}: turn int16, int64, bool, float64... into strings.
* map[interface{}]interace{} -- reflect APIs (slow) --> map[string]interface{}

#compiler.Compile

