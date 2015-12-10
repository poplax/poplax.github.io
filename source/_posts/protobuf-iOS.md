title: Use Protobuf (iOS)
date: 2015-11-30 20:13:33
tags:
- iOS
- C/C++
category:
- Tech
---


## 安装Protobuf

__两个方法安装:__

1. Google官方Protobuf项目,[官方文档](https://developers.google.com/protocol-buffers/docs/overview)
2. 通过Homebrew安装,`brew install protobuf`

## 支持iOS

- 用这个[版本](https://github.com/alexeyxo/protobuf-objc) 安装会覆盖掉`brew protobuf`
- 第二个方法支持iOS,看[这里](https://gist.github.com/BennettSmith/9487468ae3375d0db0cc)
    
<!-- more -->

### Get the Script

    git clone https://gist.github.com/9487468ae3375d0db0cc.git build-protobuf`

### Performing the Build

``` shell
$ cd build-protobuf
$ ./build-protobuf.sh

```

Add `--interactive` to the above script if you would like the script to stop after each major operation. This makes it easier to inspect the output from the various steps for potential errors.

Add `--master` if you would prefer to build from the master branch in the Google Protobuf git repo.

### Results

Build results are found in a folder called `protobuf-{version}`, where `{version}` will be either `2.6.1` or `master`. This folder contains `bin`, `include` and `lib` folders.

### Integration with Xcode

Create a build rule in your Xcode project with the following settings.

```shell

Process *Source files with names matching:* `*.proto`
Using *Custom script:*

cd ${INPUT_FILE_DIR}
${SRCROOT}/Google/protobuf/bin/protoc --proto_path=${INPUT_FILE_DIR} ${INPUT_FILE_PATH} --cpp_out=${DERIVED_FILE_DIR}

Output Files
$(DERIVED_FILE_DIR)/$(INPUT_FILE_BASE).pb.cc
$(DERIVED_FILE_DIR)/$(INPUT_FILE_BASE).pb.h

```


