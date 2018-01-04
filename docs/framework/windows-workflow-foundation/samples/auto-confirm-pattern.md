---
title: "Modèle de confirmation automatique"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 668aec65-78d3-4636-9c7b-deed643a18f9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3595e501341f64883ce2552f0a3c0850691f38c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="auto-confirm-pattern"></a>Modèle de confirmation automatique
Cet exemple est composé de trois scénarios qui s'exécutent pour illustrer une activité `AutoConfirmScope` personnalisée. Le premier exemple présente l'exécution réussie d'une séquence de quatre activités compensables où la deuxième et la troisième sont imbriqués dans un `AutoConfirmScope`. Le deuxième exemple présente la même séquence avec une exception qui se produit après l'exécution du quatrième <xref:System.Activities.Statements.CompensableActivity>. Le troisième scénario présente la même séquence avec une exception qui se produit dans `AutoConfirmScope` une fois le deuxième <xref:System.Activities.Statements.CompensableActivity> terminé.  
  
 L'exemple illustre le modèle de confirmation automatique où toutes les activités compensables enfants sont confirmées une fois l'étendue terminée avec succès. Ce modèle définit la durée de vie de toutes les activités compensables enfants, lorsqu'elles ne peuvent plus être compensées ou confirmées.  
  
 L'étendue est composée d'un <xref:System.Activities.Statements.TryCatch> où <xref:System.Activities.Statements.TryCatch.Try%2A> est un <xref:System.Activities.Statements.CompensableActivity> interne. Le corps spécifié par l'utilisateur d'`AutoConfirmScope` est le corps du <xref:System.Activities.Statements.CompensableActivity> interne. Lorsque ce <xref:System.Activities.Statements.CompensableActivity> interne se termine, il produit un <xref:System.Activities.Statements.CompensationToken> comme argument de sortie. `AutoConfirmScope` utilise un <xref:System.Activities.Statements.TryCatch.Finally%2A> pour vérifier si le jeton a été produit, et si tel est le cas, il confirme ensuite le <xref:System.Activities.Statements.CompensableActivity> interne. Le <xref:System.Activities.Statements.CompensableActivity> interne appelle la compensation par défaut pour toutes les activités compensables qui peuvent exister dans son corps.  
  
 Le premier scénario illustre l'exécution réussie du workflow. Il montre que la deuxième et la troisième activités compensables sont déjà confirmées lorsque le workflow se termine et que la première et la quatrième sont confirmées. Cela produit un ordre de confirmation de trois, deux, quatre et un.  
  
 Le deuxième scénario présente une exception une fois les quatre activités compensables terminées. Étant donné que la deuxième et la troisième activités compensables sont déjà confirmées, elles ne sont pas affectées, mais les activités une et quatre sont compensées. Cela produit la confirmation de la troisième activité, la confirmation de la deuxième activité, la compensation de la quatrième activité et la compensation de la première activité.  
  
 Le dernier scénario présente l'échec de l'exécution de `AutoConfirmScope`. Dans ce scénario, une exception se produit une fois le deuxième <xref:System.Activities.Statements.CompensableActivity> terminé. Étant donné que la troisième et la quatrième activités compensables ne se sont pas exécutées, elles ne sont pas affectées. Étant donné que l'étendue ne s'est pas terminée avec succès, le deuxième <xref:System.Activities.Statements.CompensableActivity> n'est pas confirmé. Cela produit un ordre de compensation de deux, puis un.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution AutoConfirmSample.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Compensation\AutoConfirm`