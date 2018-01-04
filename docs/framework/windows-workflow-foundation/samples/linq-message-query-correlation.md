---
title: "Corrélation de requête de message LINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1207f371da5b447903e2846229860fd8c214a46e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="linq-message-query-correlation"></a>Corrélation de requête de message LINQ
Cet exemple montre comment effectuer une corrélation basée sur le contenu à l'aide d'une implémentation <xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisée par opposition au <xref:System.ServiceModel.XPathMessageQuery> fourni par le système.  
  
## <a name="demonstrates"></a>Démonstrations  
 <xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisé, corrélation basée sur le contenu.  
  
## <a name="discussion"></a>Discussion  
 Cet exemple montre le mode d'extension à partir de la classe de base <xref:System.ServiceModel.Dispatcher.MessageQuery> pour les besoins de la corrélation. L'implémentation personnalisée, `LinqMessageQuery`, permet aux utilisateurs de fournir un XName à rechercher dans le message à l'aide de XLinq. Les données récupérées par la requête sont utilisées pour former la clé de corrélation afin de distribuer des messages à l'instance de workflow appropriée.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Cet exemple expose un service de workflow à l'aide de points de terminaison HTTP. Pour exécuter cet exemple, bon ACL d’URL doit être ajouté (consultez [configuration de HTTP et HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) pour plus d’informations), soit en exécutant Visual Studio en tant qu’administrateur ou en exécutant la commande suivante à une invite de commandes avec élévation de privilèges pour ajouter les ACL appropriées. Vérifiez que vos domaine et nom d'utilisateur sont substitués.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  Une fois les listes de contrôle d'accès (ACL) d'URL ajoutées, effectuez les étapes suivantes.  
  
    1.  Générez la solution.  
  
    2.  Définir plusieurs projets de démarrage en cliquant sur la solution et en sélectionnant **définir les projets de démarrage**. Ajouter **Service** et **Client** (dans cet ordre) en tant que plusieurs projets de démarrage.  
  
    3.  Exécutez l'application. La console cliente affiche un workflow qui envoie une commande et reçoit l'ID de bon de commande, puis confirme par la suite la commande. La fenêtre Service affichera les demandes en cours de traitement.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
