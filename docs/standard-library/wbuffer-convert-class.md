---
title: wbuffer_convert 类
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: ba8c98075741ae6cb8db0ecdfcb1e18cf4f4f89c
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561110"
---
# <a name="wbuffer_convert-class"></a>wbuffer_convert 类

描述用于控制元素与字节流缓冲区之间的来回传输的流缓冲区。

## <a name="syntax"></a>语法

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
    : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>参数

*Codecvt*\
表示转换对象的[区域设置](../standard-library/locale-class.md)方面。

*Elem*\
宽字符元素类型。

*特征*\
与 Elem** 关联的特征。

## <a name="remarks"></a>注解

此类模板描述了一个流缓冲区，该缓冲区控制类型的元素 `_Elem` （其字符特征由类描述 `Traits` ）与类型的字节流缓冲区之间的传输 `std::streambuf` 。

一系列 `Elem` 值与多字节序列之间的转换由类 `Codecvt<Elem, char, std::mbstate_t>` 的对象执行，这符合标准代码转换方面 `std::codecvt<Elem, char, std::mbstate_t>` 的要求。

此类模板的对象存储：

- 指向其基础字节流缓冲区的指针

- 指向分配的转换对象（在销毁 [wbuffer_convert](../standard-library/wbuffer-convert-class.md) 对象时释放）的指针
