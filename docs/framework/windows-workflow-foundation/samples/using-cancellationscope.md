---
title: Utilisation de CancellationScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39c5c338-b316-43d6-b7fe-a543281dd1ec
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2082ab8e0a9736cf56b7b551335ed57d082f7c8a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="using-cancellationscope"></a>Utilisation de CancellationScope
Cet exemple montre comment utiliser l'activité <xref:System.Activities.Statements.CancellationScope> pour annuler un travail dans une application.  
  
 De nombreux composants et services de niveau intermédiaire comptent sur la construction de programmation connue des transactions pour gérer l'annulation pour eux.  Toutefois, dans un certain nombre de cas, le travail qui ne peut pas être fait dans une transaction doit être annulé.  Il est plus difficile d'utiliser l'annulation que d'utiliser des transactions, car le travail qui doit être annulé doit être d'abord suivi. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] vous aide en fournissant une activité <xref:System.Activities.Statements.CancellationScope>.  
  
 L'annulation peut être déclenchée à partir d'une activité ou à partir du parent de l'activité.  Les activités enfants sont planifiées par leur activité parente (telles qu'un <xref:System.Activities.Statements.Sequence>, un <xref:System.Activities.Statements.Parallel>, un <xref:System.Activities.Statements.Flowchart> ou une activité composite personnalisée).  L'activité parente peut annuler des activités enfants pour n'importe quelle raison.  Par exemple, une activité <xref:System.Activities.Statements.Parallel> avec trois branches enfants annule les branches enfants restantes chaque fois qu'elle termine une branche et que l'expression <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> prend la valeur `true`. Le workflow peut également être annulé de manière externe par l'application hôte en appelant <xref:System.Activities.WorkflowApplication.Cancel%2A>.  
  
 Pour utiliser l'activité <xref:System.Activities.Statements.CancellationScope>, placez le travail qui doit être annulé dans la propriété <xref:System.Activities.Statements.CancellationScope.Body%2A>, et placez le travail qui est effectué après l'annulation dans la propriété <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>.  
  
 Cet exemple illustre l'annulation d'une activité à partir de l'activité elle-même.  
  
 Le scénario utilisé par l'exemple pour illustrer l'activité <xref:System.Activities.Statements.CancellationScope> est un client qui souhaite acheter dès que possible un billet pour Miami. Il y a deux agences de voyage qui souhaitent traiter l'affaire. L'exemple utilise deux <xref:System.Activities.Statements.CancellationScope> dans une activité <xref:System.Activities.Statements.Parallel> pour modéliser cette logique métier. Le <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> de l'activité <xref:System.Activities.Statements.Parallel> a la valeur `true` ; étant donné que <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> est vérifié une fois chaque branche terminée, cela entraînera l'annulation de la branche restante après la fin de la première branche. L'application cliente demande aux deux agences d'acheter le billet, et lorsque la première confirme que le billet a été acheté, l'application annule la commande auprès de l'autre agence.  
  
## <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution CancelationScopeXAML.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\CancellationScope`