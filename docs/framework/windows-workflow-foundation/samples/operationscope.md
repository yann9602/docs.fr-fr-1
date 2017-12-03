---
title: OperationScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 242a9e32063deda0593552b70bf91dec3af7c346
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="operationscope"></a>OperationScope
Cet exemple montre comment les activités de messagerie, <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>, peuvent être utilisées pour exposer une activité personnalisée existante en tant qu'opération dans un service de workflow. Cet exemple inclut une nouvelle activité personnalisée appelée `OperationScope`. Elle est destinée à faciliter le développement d'un service de workflow en permettant aux utilisateurs de créer le corps de leurs opérations séparément en tant qu'activités personnalisées et de les exposer facilement en tant qu'opérations de service à l'aide de l'activité `OperationScope`. Par exemple, une activité `Add` personnalisée que prend deux arguments `in` et qui retourne un argument `out` pourrait être exposée en tant qu'opération `Add` sur le service de workflow en le déposant dans un `OperationScope`.  
  
 L'étendue fonctionne en inspectant l'activité fournie comme étant son corps. Tous les arguments `in` non liés sont supposés être des entrées du message entrant. Tous les arguments `out`, qu'ils soient liés ou non, sont supposés être des sorties dans le message de réponse suivant. Le nom de l'opération exposée provient du nom complet de l'activité `OperationScope`. Le résultat final est que l'activité de corps est incluse dans un wrapper dans un <xref:System.ServiceModel.Activities.Receive> et un <xref:System.ServiceModel.Activities.SendReply> avec les paramètres provenant des messages liés aux arguments de l'activité.  
  
 Cet exemple expose un service de workflow à l'aide de points de terminaison HTTP. Pour s'exécuter, des listes de contrôle d'accès (ACL) d'URL appropriées doivent être ajoutées. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Configuration de HTTP et HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353). L’exécution de la commande suivante à une invite de commandes avec élévation de privilèges ajoute les ACL appropriées (Vérifiez que votre domaine et le nom d’utilisateur sont substitués pour le domaine %\\%username%).  
  
 **netsh http ajouter urlacl url = http : / / + : 8000 / utilisateur = domaine %\\%UserName%**  
  
### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez la solution OperationScope.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Définir plusieurs projets de démarrage en cliquant sur la solution dans l’Explorateur de solutions et en sélectionnant **définir les projets de démarrage**. Ajoutez Scénario et Scenario_Client (dans cet ordre) en tant que plusieurs projets de démarrage.  
  
3.  Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
    > [!WARNING]
    >  Cette étape est requise pour consulter le workflow BankService.xaml en raison de l'activité personnalisée `OperationScope`.  
  
4.  Appuyez sur CTRL+F5 pour exécuter l'application. La console Scenario_Client vous demande des entrées, et la sortie correspondante s'affiche sur la console Scenario.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`