---
title: 'Gewusst wie: Verwenden spezifischer Ausnahmen in einem Catch-Block'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 424db46c879974a9859637f9a2a5dfcd4494a3c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571797"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Gewusst wie: Verwenden spezifischer Ausnahmen in einem Catch-Block

Im Allgemeinen empfiehlt es sich beim Programmieren, einen bestimmten Ausnahmetyp abzufangen, anstatt eine grundlegende `catch`-Anweisung zu verwenden.

Wenn eine Ausnahme auftritt, wird sie von unten nach oben durch den Stapel übergeben, und jeder Block erhält die Möglichkeit, sie zu behandeln. Die Reihenfolge der catch-Anweisungen ist wichtig. Platzieren Sie catch-Blöcke für bestimmte Ausnahmen vor einen allgemeinen Block zum Abfangen von Ausnahmen. Andernfalls gibt der Compiler möglicherweise einen Fehler aus. Der richtige catch-Block wird ermitteln, indem der Typ der Ausnahme mit dem Namen der im catch-Block angegebenen Ausnahme abgeglichen wird. Wenn kein bestimmter catch-Block vorhanden ist, wird die Ausnahme durch einen allgemeinen catch-Block abgefangen, sofern vorhanden.

Das folgende Codebeispiel verwendet einen `try`/`catch`-Block, um eine <xref:System.InvalidCastException> abzufangen. Das Beispiel erstellt eine Klasse namens `Employee` mit einer einzigen Eigenschaft für die Mitarbeiterstufe („employee level“, `Emlevel`). Eine Methode, `PromoteEmployee`, übernimmt ein Objekt und erhöht die Mitarbeiterstufe. Eine <xref:System.InvalidCastException> tritt auf, wenn eine <xref:System.DateTime>-Instanz an die `PromoteEmployee`-Methode übergeben wird.

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>Siehe auch  
[Ausnahmen](index.md)
