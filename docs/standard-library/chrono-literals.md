---
title: chrono リテラル | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 022f2bb5355b59ca9ee614c79fee310526e094d8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="chrono-literals"></a>chrono リテラル

(C++14) \<chrono> ヘッダーでは、時、分、秒、ミリ秒、マイクロ秒、ナノ秒を表すリテラルの使用を容易にする 12 個の[ユーザー定義リテラル](../cpp/user-defined-literals-cpp.md)が定義されています。 各ユーザー定義リテラルには、整数と浮動小数点数のオーバーロードがあります。 これらのリテラルは、std::chrono がスコープ内にあると自動的にスコープ内になる literals::chrono_literals インライン名前空間で定義されています。

## <a name="syntax"></a>構文

```cpp
inline namespace literals {
    inline namespace chrono_literals {
 // return integral hours
    constexpr chrono::hours operator"" h(unsigned long long Val);

// return floating-point hours
    constexpr chrono::duration<double, ratio<3600>> operator"" h(long double Val);

// return integral minutes
    constexpr chrono::minutes(operator"" min)(unsigned long long Val);

// return floating-point minutes
    constexpr chrono::duration<double, ratio<60>>(operator"" min)(long double Val);

// return integral seconds
    constexpr chrono::seconds operator"" s(unsigned long long Val);

// return floating-point seconds
    constexpr chrono::duration<double> operator"" s(long double Val);

// return integral milliseconds
    constexpr chrono::milliseconds operator"" ms(unsigned long long Val);

// return floating-point milliseconds
    constexpr chrono::duration<double, milli> operator"" ms(long double Val);

// return integral microseconds
    constexpr chrono::microseconds operator"" us(unsigned long long Val);

// return floating-point microseconds
    inline constexpr chrono::duration<double, micro> operator"" us(long double Val);

// return integral nanoseconds
    inline constexpr chrono::nanoseconds operator"" ns(unsigned long long Val);

// return floating-point nanoseconds
    constexpr chrono::duration<double, nano> operator"" ns(long double Val);

}// inline namespace chrono_literals
}// inline namespace literals
```

## <a name="return-value"></a>戻り値

`long long` 引数を受け取るリテラルは、値または対応する型を返します。 浮動小数点数の引数を受け取るリテラルは、[期間](../standard-library/duration-class.md)を返します。

## <a name="example"></a>例

chrono リテラルを使用する方法の例を次に示します。

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="requirements"></a>要件

**ヘッダー**: \<chrono>

**名前空間**: std::literals::chrono_literals

## <a name="see-also"></a>関連項目

[\<chrono>](../standard-library/chrono.md)<br/>
