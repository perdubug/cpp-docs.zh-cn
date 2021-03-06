---
title: 编译器警告 C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: ada10b5989b714ec4c75a24de1bbb101e1f51ee6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230761"
---
# <a name="compiler-warning-c4957"></a>编译器警告 C4957

> "*cast*"：从 "*cast_from*" 到 "*cast_to*" 的显式强制转换是不可验证的

## <a name="remarks"></a>备注

强制转换会导致不可验证的映像。

某些强制转换是安全的（例如， **`static_cast`** 触发用户定义的转换和的 **`const_cast`** ）。 确保 [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) 生成可验证的代码。

有关详细信息，请参阅[纯代码和可验证代码（c + +/cli）](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

此警告作为错误发出，可通过 [warning](../../preprocessor/warning.md) 杂注或 [/wd](../../build/reference/compiler-option-warning-level.md) 编译器选项禁用该警告。

## <a name="example"></a>示例

以下示例生成 C4957：

```cpp
// C4957.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4957 )
using namespace System;
int main() {
   Object ^ o = "Hello, World!";
   String ^ s = static_cast<String^>(o);   // C4957
   String ^ s2 = safe_cast<String^>(o);   // OK
}
```
