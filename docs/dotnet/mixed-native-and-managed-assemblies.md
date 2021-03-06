---
title: 混在 (ネイティブおよびマネージ) アセンブリ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 469e0429408e1b8afed65889539202650cd28413
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704790"
---
# <a name="mixed-native-and-managed-assemblies"></a>混在 (ネイティブおよびマネージ) アセンブリ

混在アセンブリは、アンマネージ マシン語命令と MSIL 命令の両方を含むことができます。 これにより、混在アセンブリは、全体としてはアンマネージのコンポーネントとの互換性を維持しながら、.NET コンポーネントを呼び出したり、.NET コンポーネントから呼び出したりできます。 混在アセンブリを使用すると、開発者は、マネージ機能とアンマネージ機能が混在したアプリケーションを作成できます。 このため、混在アセンブリは、既存の Visual C++ アプリケーションを .NET プラットフォームに移行するのに理想的です。

たとえば、アンマネージ関数でのみ構成された既存のアプリケーションにできます .NET プラットフォームに 1 つのモジュールを再コンパイルして、 **/clr**コンパイラ スイッチ。 以降、このモジュールで .NET 機能を使用できるようになりますが、アプリケーションの残りの部分との互換性は維持されたままです。 この方法を使用すると、アプリケーションを要素ごとに少しずつ .NET プラットフォームに変換できます。 同じファイル内の関数ごとに、マネージ コードとアンマネージのコンパイルの間を決定することも (を参照してください[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md))。

Visual C を使用して混合マネージ アセンブリの生成のみがサポートしている、 **/clr**コンパイラ オプション。 **/Clr: 純粋な**と **/clr:safe**コンパイラ オプションが Visual Studio 2015 では廃止され、Visual Studio 2017 でサポートされていません。 純粋なアセンブリまたは検証可能なマネージ アセンブリを必要とする場合は、c# を使用して作成するをお勧めします。

以前のバージョンの Visual C コンパイラ ツールセットには、次の 3 つの種類のマネージ アセンブリの生成がサポートされている: 混合、純粋、および検証します。 後者 2 つは、後ほど[純粋なコードと検証可能なコード (C + + CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)です。

## <a name="in-this-section"></a>このセクションの内容

[方法:/clr:pure に移行](../dotnet/how-to-migrate-to-clr.md)<br/>
アプリケーションへの .NET 機能の導入またはアプリケーション内の .NET 機能の更新を行うための推奨処理手順について説明します。

[方法: MFC および ATL コードを使用して/clr のコンパイル](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
共通言語ランタイムをターゲットに既存の MFC および ATL プログラムをコンパイルする方法について説明します。

[混在アセンブリの初期化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
"ローダー ロック" の問題とそのソリューションについて説明します。

[混在アセンブリのためのライブラリ サポート](../dotnet/library-support-for-mixed-assemblies.md)<br/>
ネイティブ ライブラリを使用する方法について説明 **/clr**コンパイルします。

[パフォーマンスに関する考慮事項](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
混在アセンブリとデータ マーシャリングのパフォーマンスへの影響について説明します。

[アプリケーション ドメインと Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
アプリケーション ドメインに対する Visual C++ サポートについて説明します。

[ダブル サンキング](../dotnet/double-thunking-cpp.md)<br/>
マネージ関数のネイティブ エントリ ポイントのパフォーマンスへの影響について説明します。

[/Clr で CLR シャット ダウン時に消費して構築された COM オブジェクトの例外の回避](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
コンパイルされた COM オブジェクトを使用するマネージ アプリケーションの適切なシャット ダウンする方法について説明 **/clr**です。

[方法: CRT ライブラリ DLL との依存関係を削除して部分信頼アプリケーションを作成する](../dotnet/create-a-partially-trusted-application.md)<br/>
Msvcm90.dll との依存関係を削除することによって、Visual C を使用して部分的に信頼された共通言語ランタイム アプリケーションを作成する方法について説明します。

混在アセンブリのコーディングのガイドラインの詳細については、MSDN の記事を参照してください。 [、概要の管理/管理されていないコードの相互運用性](https://msdn.microsoft.com/en-us/library/ms973872.aspx)です。

## <a name="see-also"></a>関連項目

- [ネイティブと .NET の相互運用性](../dotnet/native-and-dotnet-interoperability.md)
