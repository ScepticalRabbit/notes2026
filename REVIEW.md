I am looking at where types are that users need to access and thinking they need to be accessible through a common named interface. We currently have:
    - Shader types seem to live in shaderops_common.zig
    - Mesh types seem to live in meshpipe.zig
    - Camera types seem to live in camera_common.zig
Ideally we should have a consistent naming structure here so public types users have to touch are in a consistent namespace. So maybe we move the relevant types to:
    - shadertypes.zig
    - meshtypes.zig
    - cameratypes.zig
