---
title: Mise en forme des messages dans les services de workflow
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 726ce98f3fe11bbc3cd13d90cdae335c0741efe6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="formatting-messages-in-workflow-services"></a>Mise en forme des messages dans les services de workflow
Cet exemple montre comment différents types utilisateur peuvent être utilisés dans des activités de messagerie (services WF). L'exemple de service est un service d'approbation des dépenses simple qui expose trois opérations. `ApproveExpense` prend un type de contrat de données et montre comment utiliser des types connus. L'opération retourne `true` ou `false` selon le montant de la dépense. `ApprovePO`prend un type XmlSerializer et retourne `true` ou `false` selon le montant de frais.`ApprovedVendor` prend un type de contrat de message et retourne `true` ou `false` si le fournisseur figure dans la liste des fournisseurs approuvés ou si la demande provient du service financier (le service financier peut utiliser n’importe quel fournisseur).  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Chargez la solution du projet dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et générez le projet.  
  
2.  En premier lieu, exécutez le service, généré dans [répertoire de base de la solution]\FormatterService\bin\debug\.  
  
3.  En second lieu, exécutez l'application cliente, générée dans [répertoire de base de la solution]\FormatterClient\bin\debug.  
  
4.  Le client appelle trois opérations sur le service et imprime les résultats. Une fois cette opération terminée, appuyez sur ENTRÉE pour quitter le client, puis le service.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`