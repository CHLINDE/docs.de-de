---
title: Anforderung-Antwort-Korrelation
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: c38854ad42ad4dddce5171482f3ddcfe5bd16b61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497203"
---
# <a name="request-reply-correlation"></a>Anforderung-Antwort-Korrelation
Anforderung-Antwort-Korrelation wird verwendet, mit einem <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> -Paar, das einen bidirektionalen Vorgang in einem Workflowdienst und mit implementieren eine <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> -Paar, das einen bidirektionalen in eine andere Web Vorgang -Dienst. Beim Aufrufen der eines bidirektionalen Vorgangs in einem WCF-Dienst der Dienst kann entweder eine herkömmliche imperative codebasierte Windows Communication Foundation (WCF)-Dienst, oder es kann ein Workflowdienst sein. Zum Verwenden der Anforderung-Antwort-Korrelation muss eine bidirektionale Bindung wie <xref:System.ServiceModel.BasicHttpBinding> verwendet werden. Die Schritte zum Initialisieren der Korrelation sind für das Aufrufen und Implementieren eines bidirektionalen Vorgangs gleich und werden in diesem Abschnitt behandelt.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Verwenden der Korrelation in einem bidirektionalen Vorgang mit Receive/SendReply  
 Ein <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> Paar wird verwendet, um einen bidirektionalen Vorgang in einem Workflowdienst zu implementieren. Die Laufzeit verwendet die Anforderung-Antwort-Korrelation, um sicherzustellen, dass die Antwort an den richtigen Aufrufer weitergeleitet wird. Wenn ein Workflow dann mit <xref:System.ServiceModel.Activities.WorkflowServiceHost> gehostet wird, beispielsweise Workflowdienste, ist die standardmäßige Korrelationsinitialisierung ausreichend. In diesem Szenario eine <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> -Paar von einem Workflow verwendet wird, und es ist keine spezielle korrelationskonfiguration erforderlich.  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a>Explizites Initialisieren der Anforderung-Antwort-Korrelation  
 Wenn andere bidirektionale Vorgänge parallel laufen, sollte die Korrelation explizit konfiguriert werden. Dies kann geschehen, indem Sie angeben einer <xref:System.ServiceModel.Activities.CorrelationHandle> und <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, oder durch Platzieren der <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> innerhalb von einer <xref:System.ServiceModel.Activities.CorrelationScope>. In diesem Beispiel wird auf Anforderung-Antwort-Korrelation konfiguriert eine <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> Paar.  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 Anstatt die Korrelation explizit zu konfigurieren, können Sie auch eine <xref:System.ServiceModel.Activities.CorrelationScope>-Aktivität verwenden. <xref:System.ServiceModel.Activities.CorrelationScope> stellt ein implizites <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekt für die darin enthaltenen Messagingaktivitäten bereit. In diesem Beispiel wird eine <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> Paar befindet sich innerhalb einer <xref:System.ServiceModel.Activities.CorrelationScope>. Es ist keine explizite Korrelationskonfiguration erforderlich.  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =   
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 Falls zusätzliche Korrelationen erforderlich sind, können diese mit der <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A>-Eigenschaft der jeweiligen Messagingaktivitäten konfiguriert werden, indem die gewünschten `CorrelationInitializer`-Typen verwendet werden.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Verwenden der Korrelation in einem bidirektionalen Vorgang mit Send/ReceiveReply  
 Während der <xref:System.ServiceModel.Activities.Receive> Aktivität kann nur verwendet werden, in einem von gehosteten Workflowdienst <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> und <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> Paar in einem Workflow, der eine Methode für einen Webdienst aufrufen muss verwendet werden kann. Wenn der Workflow mit <xref:System.ServiceModel.Activities.WorkflowServiceHost> gehostet wird, gilt die im vorherigen Abschnitt beschriebene Standardkorrelation. Falls nicht, muss die Korrelation entweder explizit mit den gewünschten Objekten <xref:System.ServiceModel.Activities.CorrelationInitializer> und <xref:System.ServiceModel.Activities.CorrelationHandle> oder per impliziter Handleverwaltung von <xref:System.ServiceModel.Activities.CorrelationScope> konfiguriert werden.  
  
 Bei Verwendung **Hinzufügen eines Dienstverweises** für einen Dienst mit bidirektionalen Vorgängen, werden Aktivitäten generiert, Wrap eine <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> -paaraktivität intern mit der Anforderung/Antwort-Korrelation explizit angegeben.
