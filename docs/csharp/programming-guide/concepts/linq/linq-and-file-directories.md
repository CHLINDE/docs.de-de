---
title: LINQ und Dateiverzeichnisse (C#)
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: 6368be7265b6dca298509d691edf0688240e8e25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325018"
---
# <a name="linq-and-file-directories-c"></a>LINQ und Dateiverzeichnisse (C#)
Viele Dateisystemvorgänge sind im Wesentlichen Abfragen und sind deshalb für die LINQ-Vorgehensweise gut geeignet.  
  
 Bitte beachten Sie, das die Abfragen in diesem Abschnitt nichtdestruktiv sind. Sie werden nicht verwendet, um den Inhalt der ursprünglichen Dateien und Ordner zu ändern. Dies entspricht der Regel, nach der Abfragen keine Nebeneffekte haben sollen. Allgemein gilt, dass jeder Code (einschließlich Abfragen, die Operatoren zum Erstellen/Aktualisieren/Löschen ausführen), der Quelldaten modifiziert, von Code getrennt sein sollte, der Daten lediglich abfragt.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
 [How to: Query for Files with a Specified Attribute or Name (C#) (Vorgehensweise: Abfragen von Dateien mit einem angegebenen Attribut oder Namen (C#))](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Hier erfahren Sie, wie Sie nach Dateien suchen, indem Sie eine oder mehrere Eigenschaften des Objekts <xref:System.IO.FileInfo> betrachten.  
  
 [Vorgehensweise: Gruppieren von Dateien nach Erweiterung (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Hier erfahren Sie, wie Sie Gruppen des Objekts <xref:System.IO.FileInfo> nach deren Dateinamenerweiterung zurückgeben.  
  
 [Vorgehensweise: Abfragen der Gesamtzahl an Bytes in einem Ordnersatz (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)  
 Hier erfahren Sie, wie Sie die Gesamtzahl von Bytes in allen Dateien einer angegebenen Verzeichnisstruktur zurückgeben.  
  
 [Vorgehensweise: Vergleichen des Inhalts von zwei Ordnern (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)  
 Hier erfahren Sie, wie Sie alle Dateien, die sich ein zwei angegebenen Ordnern befinden, zurückgeben können; ebenso erfahren Sie, wie Sie die Dateien, die sich nur in einem der zwei Ordner befinden, zurückgeben können.  
  
 [How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#) (Vorgehensweise: Abfragen der größten Datei oder der größten Dateien in einer Verzeichnisstruktur (LINQ) (C#))](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 Hier erfahren Sie, wie Sie die größte oder kleinste Datei oder eine angegebene Anzahl von Dateien in einer Verzeichnisstruktur zurückgeben können.  
  
 [Vorgehensweise: Abfragen von Dateiduplikaten in einer Verzeichnisstruktur (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Hier erfahren Sie, wie Sie die Dateien nach Dateinamen gruppieren können, die an mehr als einer Stelle in einer angegebenen Verzeichnisstruktur vorkommen. Ebenfalls lernen Sie, wie sie komplexere Vergleiche mit einer benutzerdefinierten Vergleichsfunktion durchführen können.  
  
 [Vorgehensweise: Abfragen des Inhalts von Dateien in einem Ordner (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-lin.md)  
 Hier erfahren Sie, wie Sie Ordner in einer Struktur durchlaufen, jede Datei öffnen und die Inhalte der Datei abfragen können.  
  
## <a name="comments"></a>Kommentare  
 Das Erstellen einer Datenquelle, die die Inhalte des Dateisystems angemessen repräsentieren, kommt mit einer gewissen Komplexität. Die Beispiele in diesem Abschnitt geben Ihnen einen ersten Überblick über <xref:System.IO.FileInfo>-Objekte, der alle Dateien in einem angegebenen Stammordner mit all seinen Unterordnern repräsentiert. Der tatsächliche Zustand jedes <xref:System.IO.FileInfo> verändert sich möglicherweise in der Zeit zwischen Beginn und Ende der Ausführung einer Abfrage. Sie können beispielsweise eine Liste von <xref:System.IO.FileInfo>-Objekten erstellen, um diese als Datenquelle zu verwenden. Wenn Sie versuchen, auf die Eigenschaft `Length` einer Abfrage zuzugreifen, versucht das <xref:System.IO.FileInfo>-Objekt, auf das Dateisystem zuzugreifen, um den Wert von `Length` zu aktualisieren. Wenn die Datei nicht mehr existiert, erhalten Sie eine <xref:System.IO.FileNotFoundException> in Ihrer Abfrage, obwohl Sie keine direkte Abfrage an das Dateisystem vornehmen. Einige Abfragen in diesem Bereich verwenden eine getrennte Methode, die diese bestimmten Ausnahmen in gewissen Fällen verarbeitet. Des Weiteren können Sie Ihre Datenquelle auf dem neuesten Stand halten, indem Sie den <xref:System.IO.FileSystemWatcher> verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
