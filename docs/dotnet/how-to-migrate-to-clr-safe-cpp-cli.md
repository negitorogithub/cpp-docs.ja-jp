---
title: '方法: clr への移行: セーフ (C + + CLI) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- migration [C++], verifiable assemblies
- upgrading Visual C++ applications, verifiable assemblies
- verifiable assemblies [C++], migrating to
- /clr compiler option [C++], migrating to /clr:safe
ms.assetid: 75f9aae9-1dcc-448a-aa11-2d96f972f9d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d72be19eb893a74a17a988e8c14c6bdaba766cbc
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704515"
---
# <a name="how-to-migrate-to-clrsafe-ccli"></a>方法: /clr:safe に移行する (C++/CLI)

> [!IMPORTANT]
> **/Clr: 純粋な**と **/clr:safe**コンパイラ オプションが Visual Studio 2015 では廃止され、Visual Studio 2017 でサポートされていません。 安全な CLR アセンブリを必要がある場合は、c# コードを移植するをお勧めします。

以前のバージョンの Visual Studio 2017 前に、から、Visual C コンパイラ ツールセットを使用している場合を使用して検証可能なコンポーネントを生成することができます **/clr:safe**、各エラーを生成するコンパイラが検証不能なコード コンス トラクターです。

## <a name="remarks"></a>コメント

次の問題は、検証エラーを生成します。

- ネイティブ型です。 使用していない場合でも、ネイティブ クラス、構造体、ポインター、または配列の宣言はコンパイルをできなくなります。

- グローバル変数

- 共通言語ランタイムの関数呼び出しを含む、任意のアンマネージ ライブラリへの関数呼び出し

- 検証可能な関数を含めることはできません、 [static_cast 演算子](../cpp/static-cast-operator.md)ダウン キャストのためです。 [Static_cast 演算子](../cpp/static-cast-operator.md)使用できますが、プリミティブ型の間でキャストのダウン キャストの[safe_cast](../windows/safe-cast-cpp-component-extensions.md)または C スタイルのキャスト (として実装されている、 [safe_cast](../windows/safe-cast-cpp-component-extensions.md))使用する必要があります。

- 検証可能な関数を含めることはできません、 [reinterpret_cast Operator](../cpp/reinterpret-cast-operator.md) (または任意の C スタイル キャストと同等)。

- 検証可能な関数が算術演算を実行できません、 [interior_ptr (C + + CLI)](../windows/interior-ptr-cpp-cli.md)です。 割り当てるし、逆参照、可能性がありますのみです。

- 検証可能な関数は、スローのみまたはスローする前に、値の型をボックス化する必要がありますので、参照型へのポインターをキャッチします。

- 検証可能な関数は、検証可能な関数を呼び出すことができますのみ (含まれているなど、共通言語ランタイムへの呼び出しは許可されません`AtEntry` / `AtExit`、グローバル コンス トラクターが許可されていないため)。

- 検証可能なクラスを使用できない<xref:System.Runtime.InteropServices.LayoutKind>です。

- ため、パラメーターを宣言できません main 関数に EXE をビルドするには場合、<xref:System.Environment.GetCommandLineArgs%2A>コマンドライン引数を取得するために使用する必要があります。

- 仮想関数への非仮想呼び出しを行います。 例えば:

   ```cpp
   // not_verifiable.cpp
   // compile with: /clr
   ref struct A {
      virtual void Test() {}
   };

   ref struct B : A {};

   int main() {
      B^ b1 = gcnew B;
      b1->A::Test();   // Non-virtual call to virtual function
   }
   ```

また、次のキーワードは、検証可能なコードでは使用できません。

- [アンマネージ](../preprocessor/managed-unmanaged.md)と[パック](../preprocessor/pack.md)プラグマ

- [naked](../cpp/naked-cpp.md)と[整列](../cpp/align-cpp.md) [_ _declspec](../cpp/declspec.md)修飾子

- [__asm](../assembler/inline/asm.md)

- [__based](../cpp/based-grammar.md)

- [_ _try](../cpp/try-except-statement.md)と `__except`

## <a name="see-also"></a>関連項目

- [純粋なコードと検証可能なコード (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
