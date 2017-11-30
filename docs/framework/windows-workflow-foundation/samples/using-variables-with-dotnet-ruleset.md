---
title: "Utilisation de variables avec un Ruleset .NET Framework 3.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 251d4423e09ccbf9fd23cdef8f6e05ebc1fe0ebd
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a>Utilisation de variables avec un Ruleset .NET Framework 3.5
Cet exemple montre comment créer un workflow qui utilise l'activité <xref:System.Activities.Statements.Interop> pour une intégrer une activité personnalisée écrite dans [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] et qui utilise une stratégie et des règles. Le workflow passe des données à l'activité personnalisée en liant des variables aux propriétés de dépendance exposées par l'activité personnalisée.  
  
## <a name="sample-walkthrough"></a>Exemple de procédure pas à pas  
  
#### <a name="to-examine-travelrulelibrary"></a>Pour examiner TravelRuleLibrary  
  
1.  À l'aide de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], ouvrez le fichier solution InteropWith35RuleSet.sln.  
  
2.  Ouvrez TravelRuleSet.cs dans le concepteur de workflow.  
  
     Une activité séquentielle personnalisée qui contient un <xref:System.Workflow.Activities.PolicyActivity> s'affiche.  
  
3.  Double-cliquez sur l'activité de stratégie DiscountPolicy pour examiner les règles.  
  
     L'éditeur de règles s'affiche pour présenter les règles.  
  
4.  Bouton droit sur le `DiscountPolicy` et sélectionnez le **afficher le Code** option pour examiner le code en regard de code c# pour l’activité.  
  
     Observez le paramètre de propriété de dépendance pour `DiscountLevel`. Cela est équivalent à des arguments dans le [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]arguments, consultez [Variables et Arguments](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 C'est un projet de workflow séquentiel qui utilise l'activité <xref:System.Activities.Statements.Interop> pour une intégration à l'ensemble de règles personnalisé créé dans le projet `TravelRuleLibrary`. Les variables sont créées sur l'activité <xref:System.Activities.Statements.Sequence> de niveau supérieur. L'activité <xref:System.Activities.Statements.Interop> est utilisée pour une intégration à l'activité `TravelRuleSet`. Les variables déclarées sur <xref:System.Activities.Statements.Sequence> sont utilisées pour créer une liaison aux propriétés de dépendance.  
  
## <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution InteropWith35RuleSet.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`