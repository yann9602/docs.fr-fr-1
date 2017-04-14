---
title: "Obtenir WorkflowInstanceId | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Obtenir WorkflowInstanceId
Cet exemple montre comment utiliser l'activité personnalisée `GetWorkflowInstanceId` pour retourner l'ID d'instance de workflow.  
  
## Démonstrations  
 Développement de l'activité personnalisée, comment accéder à l'instance de workflow.  
  
## Discussion  
 L'obtention de l'ID d'instance d'un workflow en cours d'exécution requiert l'écriture de code.Si vous souhaitez écrire un workflow complètement déclaratif, vous avez besoin d'une activité qui puisse retourner l'ID d'instance de workflow afin que l'activité puisse être référencée dans le workflow pour fournir une expérience de création de workflow complètement déclaratif.De nombreux scénarios requièrent l'accès à l'ID d'instance, par exemple à des fins d'enregistrement ou d'audit, ou pour exécuter une corrélation au niveau de l'application en retournant l'ID d'instance à un client pour une future association \(par exemple, en utilisant cette activité à l'intérieur d'une activité SendReply\).  
  
 `GetWorkflowInstanceId` est implémenté comme un <xref:System.Activities.CodeActivity%601> parce qu'il doit retourner une valeur de type <xref:System.Guid>, et il doit avoir accès au <xref:System.Activities.CodeActivityContext> pour l'obtention de l'ID d'instance du workflow.Son implémentation est assez basique.  
  
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
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`