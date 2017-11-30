---
title: "Calculatrice corrélée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d0d3c03b946a1f3805ea6e229e4019540b58286
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="correlated-calculator"></a>Calculatrice corrélée
Cet exemple montre comment utiliser les activités de messagerie (<xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>) dans le concepteur avec une corrélation basée sur le contenu selon un paramètre dans le message. Dans ce scénario, les opérations de la calculatrice sont dans un convoi parallèle. Une instance et une corrélation (selon `CalculatorId`) sont toutes deux créées lorsque le premier message est envoyé au workflow et les messages suivants avec le même `CalculatorId` sont distribués à cette instance jusqu'à l'appel de l'opération de réinitialisation. Le client est implémenté comme une application WPF qui utilise un proxy client basé sur du code pour communiquer avec le service.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Démarrez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des autorisations élevées, ouvrez le fichier solution For.sln.  
  
    1.  Naviguez jusqu'au dossier qui contient [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Cliquez sur Devenv.exe et sélectionnez **exécuter en tant qu’administrateur**.  
  
2.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution CorrelatedCalculator.sln.  
  
3.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
4.  Pour exécuter le projet de service, appuyez sur CTRL+F5.  
  
5.  Une fois que le service est prêt et qu'il écoute les messages, dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet Client et exécutez-le.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`  
  
## <a name="see-also"></a>Voir aussi
