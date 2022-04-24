# github-actions-builds

[![boost-msvc-static](https://github.com/HyperSine/github-actions-builds/actions/workflows/boost-msvc-static.yml/badge.svg)](https://github.com/HyperSine/github-actions-builds/actions/workflows/boost-msvc-static.yml)

[![lief_sdk-msvc-static](https://github.com/HyperSine/github-actions-builds/actions/workflows/lief_sdk-msvc-static.yml/badge.svg)](https://github.com/HyperSine/github-actions-builds/actions/workflows/lief_sdk-msvc-static.yml)

[![llvm_project](https://github.com/HyperSine/github-actions-builds/actions/workflows/llvm_project.yml/badge.svg)](https://github.com/HyperSine/github-actions-builds/actions/workflows/llvm_project.yml)

## 1. 这是什么？

这是我用Github Actions构建第三方工具/库的仓库，主要是给我自己用。

你可以在 [Actions](https://github.com/HyperSine/github-actions-builds/actions) 页面下载编译好的成品。

或者如果你对编译过程、编译成品有任何疑问，你可以开一个issue。

## 2. 为什么会有这个仓库？

作为一个C++开发人员，在windows上编程真的太痛苦了，最头痛的问题还是老生常谈的包管理问题。

因为Visual C++配置的多样化，导致一个库的构建有多种方式，比如

1. 目标platform是x86还是x64？

2. 是debug构建还是release构建？

3. 使用static CRT还是shared CRT？

4. 是static库还是shared库？

因此一个库如果要完整构建恐怕得构建2 ^ 4 = 16次（上面4个方式排列组合）。

对于我们使用的第三方工具或者比较高层的库，那可能还好，因为有些配置方式我们确实不需要。比如，构建llvm的clang组件，我们肯定是选native platform、release模式，然后为了减少编译成品的体积，我们肯定选用shared CRT。你看4个配置方式有3个就固定了。

但对于比较基础的库，比如boost，那你可能上面4个方式每一种组合都要来一遍。

好在微软现在出了vcpkg，上面的过程可能你只要triplet组合一下就能完成构建。但vcpkg不是二进制分发的，它是源码分发的。用户安装一个库得从源码构建多次，一来浪费用户时间，二来也伤用户的硬盘、尤其是用ssd的。

对于我来说，我可不想把我电脑的寿命交代在编译上。因此我开了这个仓库，让github actions代为完成构建。
