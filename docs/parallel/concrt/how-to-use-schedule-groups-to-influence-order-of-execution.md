---
title: '方法: スケジュール グループを使用して、実行の順序に影響を与える |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c41617f562a0abefdecf74d52e7a886ad6326f9e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>方法: スケジュール グループを使用して実行順序に影響を与える
同時実行ランタイムでは、タスクをスケジュールする順序は非確定的です。 ただし、スケジューリング ポリシーを使用して、タスクの実行順序に影響を与えることができます。 このトピックの内容と共にスケジュール グループを使用する方法を示しています、 [concurrency::schedulingprotocol](reference/concurrency-namespace-enums.md#policyelementkey)タスクの実行順序に影響を与えるスケジューラ ポリシー。  

  
 例では、一連のタスクを 2 回、それぞれ異なるスケジューリング ポリシーを使用して実行します。 どちらのポリシーでも、処理リソースの最大数は 2 つに制限されます。 最初の実行で、`EnhanceScheduleGroupLocality`ポリシーは、既定値し、2 つ目の実行で、`EnhanceForwardProgress`ポリシー。 `EnhanceScheduleGroupLocality` ポリシーでは、1 つのスケジュール グループ内の各タスクが終了または生成するまですべてのタスクを実行します。 `EnhanceForwardProgress` ポリシーでは、1 つのタスクが終了または生成すると、ラウンドロビン方式で次のスケジュール グループに移動します。  
  
 各スケジュール グループに関連するタスクが含まれている場合、`EnhanceScheduleGroupLocality` ポリシーを使用すると、通常、タスク間でキャッシュの局所性が保持されるため、パフォーマンスが向上します。 `EnhanceForwardProgress` ポリシーを使用すると、タスクを次に進めることができるため、スケジュール グループ間で公平にスケジュールを設定する必要がある場合に便利です。  
  
## <a name="example"></a>例  
 この例で定義、`work_yield_agent`から派生するクラス[concurrency::agent](../../parallel/concrt/reference/agent-class.md)です。 `work_yield_agent` クラスでは、1 つの作業単位を実行し、現在のコンテキストを生成した後、別の作業単位を実行します。 エージェントを使用して、 [concurrency::wait](reference/concurrency-namespace-functions.md#wait)協調的に他のコンテキストで実行できるように、現在のコンテキストを生成する関数。  
  
 この例では、`work_yield_agent` オブジェクトを 4 つ作成します。 スケジューラ ポリシーを設定してエージェントの実行順序に影響を与える方法がわかるように、最初の 2 つのエージェントと残りの 2 つのエージェントを別々のスケジュール グループに関連付けます。 この例では、 [concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)メソッドを作成、 [concurrency::schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)オブジェクト。 例では、4 つすべてのエージェントを 2 回実行します。それぞれの実行で、異なるスケジューリング ポリシーを使用します。  
  
 [!code-cpp[concrt-scheduling-protocol#1](../../parallel/concrt/codesnippet/cpp/how-to-use-schedule-groups-to-influence-order-of-execution_1.cpp)]  
  
 この例を実行すると、次の出力が生成されます。  
  
```Output  
Using EnhanceScheduleGroupLocality...  
group 0,
    task 0: first loop...  
group 0,
    task 1: first loop...  
group 0,
    task 0: waiting...  
group 1,
    task 0: first loop...  
group 0,
    task 1: waiting...  
group 1,
    task 1: first loop...  
group 1,
    task 0: waiting...  
group 0,
    task 0: second loop...  
group 1,
    task 1: waiting...  
group 0,
    task 1: second loop...  
group 0,
    task 0: finished...  
group 1,
    task 0: second loop...  
group 0,
    task 1: finished...  
group 1,
    task 1: second loop...  
group 1,
    task 0: finished...  
group 1,
    task 1: finished...  
 
Using EnhanceForwardProgress...  
group 0,
    task 0: first loop...  
group 1,
    task 0: first loop...  
group 0,
    task 0: waiting...  
group 0,
    task 1: first loop...  
group 1,
    task 0: waiting...  
group 1,
    task 1: first loop...  
group 0,
    task 1: waiting...  
group 0,
    task 0: second loop...  
group 1,
    task 1: waiting...  
group 1,
    task 0: second loop...  
group 0,
    task 0: finished...  
group 0,
    task 1: second loop...  
group 1,
    task 0: finished...  
group 1,
    task 1: second loop...  
group 0,
    task 1: finished...  
group 1,
    task 1: finished...  
```  
  
 どちらのポリシーでも、イベントの順序は同じになります。 ただし、`EnhanceScheduleGroupLocality` を使用するポリシーでは、最初のスケジュール グループに属するエージェントを両方開始した後に、2 番目のグループに属するエージェントを開始します。 `EnhanceForwardProgress` を使用するポリシーでは、最初のスケジュール グループのエージェントを 1 つ開始した後、2 番目のグループの最初のエージェントを開始します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コード例をコピーし、Visual Studio プロジェクトに貼り付けるかという名前のファイルに貼り付けます`scheduling-protocol.cpp`Visual Studio コマンド プロンプト ウィンドウで、次のコマンドを実行します。  
  
 **cl.exe/EHsc scheduling-protocol.cpp**  
  
## <a name="see-also"></a>関連項目  
 [スケジュール グループ](../../parallel/concrt/schedule-groups.md)   
 [非同期エージェント](../../parallel/concrt/asynchronous-agents.md)

