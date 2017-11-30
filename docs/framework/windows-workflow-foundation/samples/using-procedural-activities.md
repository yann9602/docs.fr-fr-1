---
title: "Utilisation d'activités procédurales"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2c391316959829c77d16dd87af51d9fe1915dc88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-procedural-activities"></a>Utilisation d'activités procédurales
L'exemple utilise les activités <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch> et <xref:System.Activities.Statements.WriteLine> pour implémenter un jeu d'estimation. Le jeu d'estimation sélectionne un nombre aléatoire et le joueur doit deviner ce nombre. Lorsque le joueur soumet une estimation incorrecte, le workflow fournit une indication signalant si la valeur à deviner est supérieure ou inférieure. Si le joueur devine le nombre en moins de 7 tentatives, un message de félicitation spécial s'affiche à l'attention de l'utilisateur.  
  
## <a name="custom-activities-in-this-sample"></a>Activités personnalisées dans cet exemple  
  
### <a name="readline"></a>ReadLine  
 Lit une ligne de texte à partir de la console. Cette activité dérive de la classe <xref:System.Activities.NativeActivity> et crée un signet qui est repris par l'application console lorsqu'une ligne est lue.  
  
### <a name="promptint"></a>PromptInt  
 Invite l'utilisateur à taper un nombre, puis le lit à partir d'une fenêtre de console. L'activité dérive de <xref:System.Activities.Activity%601> et utilise les activités <xref:System.Activities.Statements.WriteLine> et `ReadLine`.  
  
##### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution GuessingGame.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`  
  
## <a name="see-also"></a>Voir aussi
