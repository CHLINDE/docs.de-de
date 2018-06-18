---
title: 'Gewusst wie: Implementieren von Benachrichtigungen bei Eigenschaftenänderungen'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: a9c0fb433e2fa65e28db3b793e038b49f9d6353b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555989"
---
# <a name="how-to-implement-property-change-notification"></a>Gewusst wie: Implementieren von Benachrichtigungen bei Eigenschaftenänderungen
Zur Unterstützung von automatischen <xref:System.Windows.Data.BindingMode.OneWay>-Bindings oder <xref:System.Windows.Data.BindingMode.TwoWay>-Bindings an die Ziel-Bindungseigenschaften bei dynamischen Änderungen der Bindungsquelle (z. B. um ein Vorschaufenster automatisch zu aktualisieren, wenn der Benutzer ein Formular bearbeitet hat), muss die Klasse die erforderliche Benachrichtigung auslösen. In diesem Beispiel wird gezeigt, wie eine Klasse erstellt wird, welche  <xref:System.ComponentModel.INotifyPropertyChanged> enthält.  
  
## <a name="example"></a>Beispiel  
 Um <xref:System.ComponentModel.INotifyPropertyChanged> zu implementieren, müssen Sie das <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> Ereignis deklarieren und die `OnPropertyChanged`-Methode erstellen. Dann lösen Sie für jede Eigenschaft, wofür Sie Änderungsbenachrichtigungen aktiv sein sollen, das `OnPropertyChanged`-Ereignis aus.
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Ein Beispiel gezeigt, wie die `Person` Klasse kann verwendet werden, um Unterstützung <xref:System.Windows.Data.BindingMode.TwoWay> binden, finden Sie unter [steuern, wann der TextBox-Text die Quelle aktualisiert](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Bindungsquellen](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Übersicht zur Datenbindung](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Themen zu Vorgehensweisen](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
