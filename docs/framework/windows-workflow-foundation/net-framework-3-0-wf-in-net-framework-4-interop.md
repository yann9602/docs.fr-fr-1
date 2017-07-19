---
title: "Utilisation d&#39;activit&#233;s WF de .NET Framework&#160;3.0&#160;dans .NET Framework&#160;4 avec l&#39;activit&#233; d&#39;interop&#233;rabilit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Utilisation d&#39;activit&#233;s WF de .NET Framework&#160;3.0&#160;dans .NET Framework&#160;4 avec l&#39;activit&#233; d&#39;interop&#233;rabilit&#233;
Le <xref:System.Activities.Statements.Interop> activité est un [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] activité (WF 4.5) qui encapsule un [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activité (WF 3.5) dans un [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] flux de travail. L’activité WF 3 peut être une activité de feuille unique ou une arborescence entière d’activités. L'exécution (notamment l'annulation et gestion des exceptions) et la persistance de l'activité [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] se produisent dans le contexte de l'instance du workflow [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] qui s'exécute.  
  
> [!NOTE]
>  Le <xref:System.Activities.Statements.Interop> n’apparaît pas dans la boîte à outils du Concepteur de flux de travail, sauf si les projets du flux de travail a son **Framework cible** défini sur **.NET Framework 4.5**.  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>Critères pour l'Utilisation d'une Activité WF 3 avec une Activité d'interopérabilité  
 Pour une activité WF 3 s’exécute correctement dans un <xref:System.Activities.Statements.Interop> activité, les critères suivants doivent être remplies :  
  
-   L’activité WF 3 doit dériver de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName>.  
  
-   L'activité WF 3 doit être déclarée comme `public` et ne peut pas être `abstract`.  
  
-   L'activité WF 3 doit avoir un constructeur public par défaut.  
  
-   En raison des limitations dans l’interface de types que le <xref:System.Activities.Statements.Interop> activité peut prendre en charge, <xref:System.Workflow.Activities.HandleExternalEventActivity> et <xref:System.Workflow.Activities.CallExternalMethodActivity> ne peuvent pas être utilisées directement, mais des activités dérivatives créées à l’aide de l’outil d’activité de Communication du flux de travail (WCA.exe) peuvent être utilisée. Consultez [Outils de Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=178889) Pour plus d’informations.  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>Configuration d'une Activité WF 3 Dans une Activité d'interopérabilité  
 Pour configurer et passer des données dans et hors d’une activité WF 3, au-delà des limites d’interopérabilité, les propriétés et les propriétés de métadonnées de l’activité WF 3 sont exposées par le <xref:System.Activities.Statements.Interop> activité. Propriétés de métadonnées de l’activité WF 3 (tel que <xref:System.Workflow.ComponentModel.Activity.Name%2A>) sont exposées via la <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> collection. C’est une collection de paires nom-valeur utilisée pour définir les valeurs pour les propriétés de métadonnées de l’activité WF 3. Une propriété de métadonnées est une propriété secondée par une propriété de dépendance pour laquelle le <xref:System.Workflow.ComponentModel.DependencyPropertyOptions> est défini.  
  
 Les propriétés de l’activité WF 3 sont exposées via la <xref:System.Activities.Statements.Interop.ActivityProperties%2A> collection. Il s’agit d’un ensemble de paires nom-valeur, où chaque valeur est un <xref:System.Activities.Argument> objet, utilisés pour définir les arguments pour les propriétés de l’activité WF 3. Étant donné que la direction d’une propriété d’activité WF 3 ne peut pas être déduite, chaque propriété est présentée comme un <xref:System.Activities.InArgument>/<xref:System.Activities.OutArgument> paire. En fonction de l’utilisation de l’activité de la propriété, vous pouvez souhaiter fournir une <xref:System.Activities.InArgument> entrée, une <xref:System.Activities.OutArgument> entrée, ou les deux. Le nom attendu de la <xref:System.Activities.InArgument> entrée dans la collection est le nom de la propriété comme défini dans l’activité WF 3. Le nom attendu de la <xref:System.Activities.OutArgument> entrée dans la collection est une concaténation du nom de la propriété et la chaîne « Out ».  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>Limitations de l'utilisation d'une activité WF 3 dans une activité d'interopérabilité  
 Les activités WF 3 fournie par le système ne peut pas être directement encapsulées dans un <xref:System.Activities.Statements.Interop> activité. Pour certaines activités WF 3, tel que <xref:System.Workflow.Activities.DelayActivity>, il s’agit, car il existe une activité WF 4.5 analogue. Pour d'autres, les fonctionnalités de cette activité ne sont pas prises en charge. De nombreuses activités fournies par le système de WF 3 peuvent être utilisées dans les workflows encapsulés par le <xref:System.Activities.Statements.Interop> activité, soumis aux restrictions suivantes :  
  
1.  <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Receive> ne peut pas être utilisé dans un <xref:System.Activities.Statements.Interop> activité.  
  
2.  <xref:System.Workflow.Activities.WebServiceInputActivity>, <xref:System.Workflow.Activities.WebServiceOutputActivity>, et <xref:System.Workflow.Activities.WebServiceFaultActivity> ne peut pas être utilisé dans un <xref:System.Activities.Statements.Interop> activité.  
  
3.  <xref:System.Workflow.Activities.InvokeWorkflowActivity> ne peut pas être utilisé dans un <xref:System.Activities.Statements.Interop> activité.  
  
4.  <xref:System.Workflow.ComponentModel.SuspendActivity> ne peut pas être utilisé dans un <xref:System.Activities.Statements.Interop> activité.  
  
5.  Les activités liées à la compensation ne peut pas être utilisées dans un <xref:System.Activities.Statements.Interop> activité.  
  
 Il existe également des caractéristiques comportementales à comprendre concernant l’utilisation des activités WF 3 dans le <xref:System.Activities.Statements.Interop> activité :  
  
1.  WF 3 activités contenues dans un <xref:System.Activities.Statements.Interop> d’activité sont initialisées lorsque le <xref:System.Activities.Statements.Interop> activité est exécutée. Dans WF 4.5 il n'y a pas de phase d'initialisation pour une instance de workflow avant son exécution.  
  
2.  Le runtime WF 4.5 ne pas contrôle instance état workflow lorsqu’une transaction commence, quel que soit l’endroit où la transaction commence (dans ou en dehors d’un <xref:System.Activities.Statements.Interop> activité).  
  
3.  Enregistrements de suivi 3 WF pour les activités au sein d’un <xref:System.Activities.Statements.Interop> activité sont fournis aux participants de suivi de WF 4.5 comme <xref:System.Activities.Tracking.InteropTrackingRecord> objets. <xref:System.Activities.Tracking.InteropTrackingRecord> est un dérivé de <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
4.  Una activité personnalisée WF 3 peut accéder aux données à l'aide de files d'attente de workflow dans l'environnement d'interopération de la même façon qu'au sein de l'exécution du workflow WF 3. Aucune modification du code d'activité personnalisé n'est obligatoire. Sur l’ordinateur hôte, les données sont en file d’attente à une file d’attente du workflow WF 3 en reprenant un <xref:System.Activities.Bookmark>. Le nom du signet est la forme de chaîne de la <xref:System.IComparable> nom de file d’attente de workflow.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de .NET Framework 3.0 ou l’activité de .NET Framework 3.5 dans un Workflow .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/using-a-net-3-0-or-net-3-5-activity-in-a-net-4-5-workflow.md)