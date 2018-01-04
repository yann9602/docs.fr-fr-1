---
title: "Corrélation basée sur le contenu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5971636df3393adda96dff779c1533969f67bf57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="content-based-correlation"></a>Corrélation basée sur le contenu
Cet exemple montre comment les activités de messagerie (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> et <xref:System.ServiceModel.Activities.ReceiveReply>) peuvent être utilisées avec plusieurs corrélations basées sur le contenu et une corrélation basée sur le contenu. Dans ce scénario, une corrélation est d'abord initialisée en fonction d'un ID de bon de commande, puis une autre corrélation est créée ultérieurement en fonction de l'ID du client. Cela montre comment une activité <xref:System.ServiceModel.Activities.Receive> peut à la fois suivre une corrélation existante et initialiser une nouvelle corrélation en fonction du même message entrant.  
  
## <a name="demonstrates"></a>Démonstrations  
 Activités de messagerie et corrélation basée sur le contenu  
  
## <a name="discussion"></a>Discussion  
 Cet exemple montre comment utiliser plusieurs corrélations basées sur le contenu.  Dans ce scénario, une corrélation est d'abord initialisée en fonction d'un ID de bon de commande, puis une autre corrélation est créée ultérieurement en fonction de l'ID du client.  Les corrélations sont mises en cascade à l'aide d'une activité <xref:System.ServiceModel.Activities.Receive> qui, à la fois, suit une corrélation existante (PurchaseOrderId) et initialise une nouvelle corrélation (CustomerID) en fonction du même message entrant.  Pour cela, l'activité <xref:System.ServiceModel.Activities.Receive> utilise les propriétés <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> et <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>.  
  
## <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Ouvrez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des autorisations élevées, en cliquant sur le [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icône et en sélectionnant **exécuter en tant qu’administrateur**.  
  
2.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution CascadingCorrelation.sln.  
  
3.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
4.  Pour exécuter le serveur, appuyez sur F5.  
  
5.  Une fois que le service est prêt et qu'il écoute les messages, dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet Client et exécutez-le.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`