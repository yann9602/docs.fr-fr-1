---
title: Exemple de point de terminaison de gestion de workflow
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e516d41a9f9736877fb3974774ddaf4b3bddb198
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-management-endpoint-sample"></a>Exemple de point de terminaison de gestion de workflow
Cet exemple montre comment un point de terminaison de contrôle de workflow peut être utilisé pour créer et exécuter des workflows à la fois localement et à distance. Il montre comment héberger un point de terminaison de contrôle et écrire des clients qui appellent le point de terminaison de contrôle pour créer et exécuter l'instance d'un workflow. Le workflow n'est pas un service.  
  
 Du côté service de l'exemple ,un workflow est hébergé avec WorkflowServiceHost et un WorkflowControlEndpoint est ajouté afin que les clients puissent exécuter des opérations de contrôle (Suspendre, Démarrer, etc.). Un CreationEndpoint défini par l'utilisateur est également ajouté pour permettre la création du workflow. Le service utilise ensuite ces points de terminaison pour démarrer le workflow dans un état suspendu, puis pour reprendre le workflow. Le client exécute les mêmes opérations mais à partir du code client. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]reportez-vous à ces interfaces, [point de terminaison de contrôle de flux de travail](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) et [Comment : héberger un workflow sans service dans IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Exécutez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des privilèges d'administrateur.  
  
2.  Ouvrez la solution ManagementEndpoint.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Pour générer la solution, appuyez sur CTRL + MAJ + B ou sélectionnez **générer la Solution** à partir de la **générer** menu.  
  
4.  Démarrez l'application ManagementEndpoint.exe.  
  
5.  Démarrez l'application Client.exe.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`