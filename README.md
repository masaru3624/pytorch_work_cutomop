# pytorch_work_cutomop
customopwork

https://pytorch.org/tutorials/advanced/torch_script_custom_ops.html

example-app: cpp内でtorch関数を使う例
src:example-app.cpp
bin:build/example-app

warp-perspective:python modeuleにcutome moduleを追加する例
src:op.cpp
lib:build/libwarp_perspective.so

build command

cmake -DCMAKE_PREFIX_PATH=/your_torch_path  ..
#e.g. cmake -DCMAKE_PREFIX_PATH=/home/a5093235/.local/lib/python3.6/site-packages/torch/  ..
cd build
make

run example:

python3
>>import torch
>>torch.ops.load_library("./libwarp_perspective.so")
>>torch.ops.my_ops.warp_perspective(torch.randn(32, 32), torch.rand(3, 3))
tensor([[ 0.0000,  0.0000,  0.0000,  0.0000,  0.0000,  0.0000,  0.0000,  0.0000],
        [ 0.0000, -0.1751,  0.0000,  0.0000,  0.0000,  0.0000,  0.0000,  0.0000],
        [ 0.0000, -0.3397, -0.4344, -0.0494,  0.0000,  0.0000,  0.0000,  0.0000],
        [ 0.0000, -0.2176, -0.4648, -0.4065, -0.0955,  0.0000,  0.0000,  0.0000],
        [ 0.0000, -0.1578, -0.3645, -0.5133, -0.3630, -0.1344,  0.0000,  0.0000],
        [ 0.0000, -0.1179, -0.2952, -0.4230, -0.5333, -0.3339, -0.1510, -0.0365],
        [ 0.0000, -0.0980, -0.2386, -0.3589, -0.4653, -0.5272, -0.3194, -0.1743],
        [ 0.0000, -0.0784, -0.2008, -0.3070, -0.4025, -0.4900, -0.4811, -0.3194]])

