---
title: Blockieren der Anwendungsausführung durch Beenden eines asynchronen Vorgangs
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
ms.openlocfilehash: db46025ca1169f2f93a5b8eabb62a06ccc4bb95e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567418"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Blockieren der Anwendungsausführung durch Beenden eines asynchronen Vorgangs
Anwendungen, die während des Wartens auf die Ergebnisse eines asynchronen Vorgangs nicht weiterarbeiten können, werden blockiert, bis der Vorgang abgeschlossen ist. Verwenden Sie eine der folgenden Optionen, um den Hauptthread Ihrer Anwendung zu blockieren, während Sie darauf warten, dass ein asynchroner Vorgang abgeschlossen wird:  
  
-   Rufen Sie die Methode **End***OperationName* für asynchrone Vorgänge auf. Dieser Ansatz wird in diesem Thema veranschaulicht.  
  
-   Verwenden Sie die Eigenschaft <xref:System.IAsyncResult.AsyncWaitHandle%2A> des Ergebnisses <xref:System.IAsyncResult>, welches durch die Methode **Begin***OperationName* für asynchrone Vorgänge zurückgegeben wird. Ein Beispiel zur Veranschaulichung dieses Ansatzes finden Sie unter [Blockieren der Anwendungsausführung mithilfe von AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Anwendungen, die die Methode **End***OperationName* zum Blockieren verwenden, bis ein asynchroner Vorgang abgeschlossen ist, rufen in der Regel die Methode **Begin***OperationName* auf, arbeiten alle Tasks ab, die ohne die Ergebnisse des Vorgangs ausgeführt werden können, und rufen dann die Methode **End***OperationName* auf.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel demonstriert die Verwendung von asynchronen Methoden in der <xref:System.Net.Dns>-Klasse, um Informationen aus dem Domain Name System für einen benutzerdefinierten Computer abzurufen. Beachten Sie, dass `null` (`Nothing` in Visual Basic) für die Parameter <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` und `stateObject` übergeben wird, da diese Argumente bei diesem Ansatz nicht benötigt werden.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Siehe auch  
 [Ereignisbasiertes asynchrones Muster (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Event-based Asynchronous Pattern Overview (Übersicht über ereignisbasierte asynchrone Muster)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
