---
title: Workflowsicherheit
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: 8acfd0640478cf67309fe53a99707c7d96c5a635
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519580"
---
# <a name="workflow-security"></a>Workflowsicherheit
Windows Workflow Foundation (WF) wird in mehrere unterschiedliche Technologien, wie z. B. Microsoft SQL Server und Windows Communication Foundation (WCF) integriert. Die Interaktion mit diesen Technologien kann zu Sicherheitsproblemen für den Workflow führen, falls diese nicht ordnungsgemäß durchgeführt wird.  
  
## <a name="persistence-security-concerns"></a>Sicherheitsaspekte der Persistenz  
  
1.  Workflows, die eine <xref:System.Activities.Statements.Delay>-Aktivität und Persistenz verwenden, müssen von einem Dienst erneut aktiviert werden. Windows AppFabric verwendet den Workflowverwaltungsdienst (WMS), um Workflows mit abgelaufenen Zeitgebern erneut zu aktivieren. WMS erstellt einen <xref:System.ServiceModel.WorkflowServiceHost> zum Hosten des erneut aktivierten Workflows. Wenn der WMS-Dienst beendet wird, werden beibehaltene Workflows nicht erneut aktiviert, wenn deren Zeitgeber ablaufen.  
  
2.  Die permanente Instanziierung sollte vor dem Zugriff durch böswillige Entitäten außerhalb der Anwendungsdomäne geschützt werden. Darüber hinaus sollten Entwickler sicherstellen, dass schädlicher Code nicht in derselben Anwendungsdomäne wie der Code für die permanente Instanziierung ausgeführt werden kann.  
  
3.  Die permanente Instanziierung sollte nicht mit erweiterten Berechtigungen (Administrator) ausgeführt werden.  
  
4.  Die Daten, die außerhalb der Anwendungsdomäne verarbeitet werden, sollten geschützt werden.  
  
5.  Anwendungen, die eine Sicherheitsisolation erfordern, sollten nicht dieselbe Instanz wie die Schemaabstraktion verwenden. Derartige Anwendungen sollten verschiedene Speicheranbieter oder Speicheranbieter verwenden, die für die Verwendung unterschiedlicher Speicherinstanziierungen konfiguriert wurden.  
  
## <a name="sql-server-security-concerns"></a>SQL Server-Sicherheitsaspekte  
  
-   Wenn eine hohe Zahl an untergeordneten Aktivitäten, Speicherorten, Lesezeichen, Hosterweiterungen oder Bereichen verwendet wird oder wenn Lesezeichen mit sehr großen Nutzlasten verwendet werden, kann es zu einer Überlastung des Arbeitsspeichers kommen. Außerdem kann während des Persistenzvorgangs eine unangemessen hohe Menge an Datenbankspeicherplatz zugeordnet werden. Sie können dieses Risiko reduzieren, indem Sie die Sicherheit auf Objekt- und Datenbankebene verwenden.  
  
-   Bei der Verwendung von <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> muss der Instanzspeicher gesichert werden. Weitere Informationen finden Sie unter [Best Practices für SQL Server](http://go.microsoft.com/fwlink/?LinkId=164972).  
  
-   Vertrauliche Daten im Instanzspeicher sollten verschlüsselt werden. Weitere Informationen finden Sie unter [SQL-Sicherheitsverschlüsselung](http://go.microsoft.com/fwlink/?LinkId=164976).  
  
-   Da die Datenbank-Verbindungszeichenfolge häufig in einer Konfigurationsdatei enthalten ist, sollte Sicherheit auf Windows-Ebene (ACL) verwendet werden, um sicherzustellen, dass die Konfigurationsdatei (normalerweise "Web.Config") sicher ist und dass keine Anmelde- und Kennwortdaten in der Verbindungszeichenfolge enthalten sind. Die Windows-Authentifizierung sollte stattdessen zwischen der Datenbank und dem Webserver verwendet werden.  
  
## <a name="considerations-for-workflowservicehost"></a>Überlegungen zu WorkflowServiceHost  
  
-   Windows Communication Foundation (WCF)-Endpunkte, die zur Verwendung in Workflows sollten geschützt werden. Weitere Informationen finden Sie unter [Sicherheitsübersicht](http://go.microsoft.com/fwlink/?LinkID=164975).  
  
-   Sie können die Autorisierung auf Hostebene mit <xref:System.ServiceModel.ServiceAuthorizationManager> implementieren. Finden Sie unter [Vorgehensweise: Erstellen eines benutzerdefinierten Autorisierungs-Managers für einen Dienst](http://go.microsoft.com/fwlink/?LinkId=192228) Details. Dies wird auch im folgenden Beispiel dargestellt: [Sichern von Workflowdiensten](../../../docs/framework/windows-workflow-foundation/samples/securing-workflow-services.md).  
  
-   Der ServiceSecurityContext für die eingehende Nachricht ist über den Zugriff auf OperationContext auch im Workflow verfügbar.  Finden Sie unter [zugreifen auf OperationContext aus einem Workflowdienst](../../../docs/framework/wcf/feature-details/accessing-operationcontext-from-a-workflow-service.md) Details.  
  
## <a name="wf-security-pack-ctp"></a>WF-Sicherheitspaket CTP  
 Das Microsoft WF-Sicherheitspaket CTP 1 ist die erste Community Technology Preview (CTP) Version einer Reihe von Aktivitäten und deren Implementierung auf Basis [Windows Workflow Foundation](http://msdn.microsoft.com/netframework/aa663328.aspx)in [.NET Framework 4](http://msdn.microsoft.com/netframework/default.aspx) (WF (4) und die [Windows Identity Foundation (WIF)](http://msdn.microsoft.com/security/aa570351.aspx).  Das Microsoft WF-Sicherheitspaket CTP 1 enthält beide Aktivitäten und deren Designer, die veranschaulichen, wie einfach verschiedene sicherheitsrelevante Szenarien mithilfe von Workflows aktiviert werden können, darunter:  
  
1.  Wechseln zu einer Clientidentität im Workflow  
  
2.  Workflowinterne Autorisierung, z. B. PrincipalPermission und Validierung von Ansprüchen  
  
3.  Authentifiziertes Messaging mit im Workflow angegebenen ClientCredentials, z. B. Benutzername/Kennwort oder ein Token, das von einem Sicherheitstokendienst (STS) abgerufen wurde  
  
4.  Übertragen eines Clientsicherheitstokens an einen Back-End-Dienst (anspruchsbasierte Delegierung) mithilfe von WS-Trust ActAs  
  
Weitere Informationen und den download der WF-Sicherheitspaket CTP finden Sie unter: [WF-Sicherheitspaket CTP](http://wf.codeplex.com/releases/view/48114)