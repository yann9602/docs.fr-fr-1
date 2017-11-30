---
title: Obtenir WorkflowInstanceId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f1eb6a1d9cd875d0332bb1d59933f75c807f74e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="get-workflowinstanceid"></a>Obtenir WorkflowInstanceId
Cet exemple montre comment utiliser l'activité personnalisée `GetWorkflowInstanceId` pour retourner l'ID d'instance de workflow.  
  
## <a name="demonstrates"></a>Démonstrations  
 Développement de l'activité personnalisée, comment accéder à l'instance de workflow.  
  
## <a name="discussion"></a>Discussion  
 L'obtention de l'ID d'instance d'un workflow en cours d'exécution requiert l'écriture de code. Si vous souhaitez écrire un workflow complètement déclaratif, vous avez besoin d'une activité qui puisse retourner l'ID d'instance de workflow afin que l'activité puisse être référencée dans le workflow pour fournir une expérience de création de workflow complètement déclaratif. De nombreux scénarios requièrent l'accès à l'ID d'instance, par exemple à des fins d'enregistrement ou d'audit, ou pour exécuter une corrélation au niveau de l'application en retournant l'ID d'instance à un client pour une future association (par exemple, en utilisant cette activité à l'intérieur d'une activité SendReply).  
  
 `GetWorkflowInstanceId` est implémenté comme un <xref:System.Activities.CodeActivity%601> parce qu'il doit retourner une valeur de type <xref:System.Guid>, et il doit avoir accès au <xref:System.Activities.CodeActivityContext> pour l'obtention de l'ID d'instance du workflow. Son implémentation est assez basique.  
  
```  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
protected override Guid Execute(CodeActivityContext context)  
        {  
            return context.WorkflowInstanceId;  
        }  
}  
```  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
