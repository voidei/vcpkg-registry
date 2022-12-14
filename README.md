# CLib Util - VCPKG Registry

[VCPKG](https://vcpkg.io) Registry for various packages used for, or assisting with, CommonLibSSE and SKSE plugin development.

## Currently included packages&colon;

* [AutoTOML](https://github.com/Ryan-rsm-McKenzie/AutoTOML) - [Ryan-rsm-McKenzie](https://github.com/Ryan-rsm-McKenzie)
* [CLib Util](https://github.com/powerof3/CLibUtil) - [powerof3](https://github.com/powerof3)
* [InfinityUI](https://github.com/alexsylex/InfinityUI) - [alexsylex](https://github.com/alexsylex)
* [MergeMapper](https://github.com/alandtse/MergeMapper) - [alandtse](https://github.com/alandtse)
* [SimpleINI Wrapper](https://github.com/powerof3/simpleini) - [powerof3](https://github.com/powerof3)

## How to use&colon;

### Add the following to your vcpkg-configuration.json file&colon;

```json
{
    "$schema": "https://raw.githubusercontent.com/microsoft/vcpkg-tool/main/docs/vcpkg-configuration.schema.json",
    "registries": [
        {
            "kind": "git",
            "repository": "https://github.com/voidei/clib-utils-vcpkg-repository",
            "baseline": "20024b93cc048815af81db9608df020d25850f2d",
            "packages": [
                "autotoml",
                "clib-util",
                "infinity-ui",
                "mergemapper",
                "simpleini-po3"
            ]
        }
    ]
}
```

#### Note: Replace the `baseline` section with the latest commit hash&period;

### Then add the following to your CMakeLists.txt&colon;

#### [AutoTOML](https://github.com/shad0wshayd3/AutoTOML/)

```cmake
find_package(AutoTOML CONFIG REQUIRED)
target_link_libraries(main PRIVATE AutoTOML::AutoTOML::)
```

#### [Clib Util&colon;](https://github.com/powerof3/CLibUtil)

```cmake
find_path(CLIB_UTIL_INCLUDE_DIRS "ClibUtil/utils.hpp")
target_include_directories(main PRIVATE ${CLIB_UTIL_INCLUDE_DIRS})
```

#### [Infinity UI&colon;](https://github.com/alexsylex/InfinityUI)

```cmake
find_path(INFINITY_UI_INCLUDE_DIRS "API.h")
target_include_dirs(main PRIVATE ${INFINITY_UI_INCLUDE_DIRS})
```

#### [MergeMapper&colon;](https://github.com/alandtse/MergeMapper)

```cmake
find_path(MERGEMAPPER_INCLUDE_DIRS "MergeMapperPluginAPI.h")
add_library(${PROJECT_NAME} SHARED ${MERGEMAPPER_INCLUDE_DIRS}/MergeMapperPluginAPI.cpp)
target_include_directories(main PRIVATE ${MERGEMAPPER_INCLUDE_DIRS})
```

#### [SimpleINI - PO3 Wrapper&colon;](https://github.com/powerof3/simpleini)

```cmake
find_path(SIMPLEINI_INCLUDE_DIRS "ConvertUTF.c")
target_include_directories(main PRIVATE ${SIMPLE_INI_INCLUDE_DIRS})
```

<!--
#### [MCM Helper&colon;](https://github.com/Exit-9B/MCM-Helper)

```cmake
todo
```
-->

### After then, you can include any of the files by doing the following&colon;

```h
// AutoTOML
#include <AutoTOML.hpp>

// ClibUtil
#include <ClibUtil/distribution.hpp>
#include <ClibUtil/rng.hpp>
#include <ClibUtil/string.hpp>

// Infinity UI
#include <API.h>

// MergeMapper
#include <MergeMapperPluginAPI.h>

// SimpleINI - PO3 Wrapper
#include <SimpleIni.h>

// MCM Helper
#include <todo>
```

## Other VCPKG Registries&colon;

### [Color-Glass Studios](https://gitlab.com/colorglass/vcpkg-colorglass)

`A Vcpkg repository for Color-Glass Studios development.`

This registry contains ports for **CommonLibSSE**, as well as several other packages used for modding Skyrim SE, or Fallout 4.

### [Mrowr Purr's VCPKG repository](https://github.com/mrowrpurr/vcpkg-repo)

This registry, maintained by [Mrowr Purr](https://github.com/mrowrpurr), is currently relatively small, but has some useful tools contained in it.

### [Skyrim Scripting VCPKG Registry](https://github.com/SkyrimScripting/vcpkg)

This registry, maintained by several members, is another relatively small one, but still contains some useful tools.
