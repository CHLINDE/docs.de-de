---
title: "How to: Create and Execute a Simple PLINQ Query | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PLINQ queries, how to create"
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# How to: Create and Execute a Simple PLINQ Query
Das folgende Beispiel zeigt, wie Sie eine einfache Parallel LINQ\-Abfrage erstellen, indem Sie die <xref:System.Linq.ParallelEnumerable.AsParallel%2A>\-Erweiterungsmethode in der Quellsequenz verwenden und die Abfrage mit der <xref:System.Linq.ParallelEnumerable.ForAll%2A>\-Methode ausführen.  
  
> [!NOTE]
>  In dieser Dokumentation werden Delegaten in PLINQ mithilfe von Lambda\-Ausdrücken definiert.  Wenn Sie in C\# oder Visual Basic nicht mit Lambda\-Ausdrücken vertraut sind, finden Sie unter [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md) entsprechende Informationen.  
  
## Beispiel  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 Dieses Beispiel zeigt das grundlegende Muster zum Erstellen und Ausführen einer beliebigen Parallel LINQ\-Abfrage, wenn die Sortierung der Ergebnissequenz nicht wichtig ist. Unsortierte Abfragen sind im Allgemeinen schneller als sortierte Abfragen.  Die Abfrage partitioniert die Quelle in Aufgaben, die asynchron in mehreren Threads ausgeführt werden.  Die Reihenfolge, in der jede Aufgabe abgeschlossen wird, hängt nicht nur von der Menge der mit der Verarbeitung der Elemente in der Partition verbundenen Arbeit, sondern auch von externen Faktoren ab, beispielsweise wie das Betriebssystem jeden Thread plant.  Dieses Beispiel soll die Nutzung darstellen und wird möglicherweise nicht schneller ausgeführt als die entsprechende sequenzielle LINQ to Objects\-Abfrage.  Weitere Informationen zur Beschleunigung finden Sie unter [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  Weitere Informationen zur Beibehaltung der Sortierung von Elementen in einer Abfrage finden Sie unter [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).  
  
## Siehe auch  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)