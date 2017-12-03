---
title: "Délai durable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0e679b91bd342ed5105fba7b916a8ed0070d0da
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="durable-delay"></a>Délai durable
Cet exemple montre comment utiliser un délai durable, qui est un délai rendant le workflow persistant sur un périphérique durable pendant le délai. L'exemple de workflow contient deux messages sur la console qui sont séparés par un délai. Lorsque le délai est déclenché, le workflow est déchargé, et attend 5 secondes dans le magasin d'instances de workflow avant d'être rechargé en mémoire.  
  
## <a name="workflow-details"></a>Détails du workflow  
 L'hôte du service de workflow héberge le workflow et gère les instances de workflow en les chargeant et en les déchargeant. Pour démarrer une instance de la définition de workflow, l'exemple définit un proxy qui envoie un message à l'activité <xref:System.ServiceModel.Activities.Receive> dans le workflow. La propriété <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> a la valeur `true`, ce qui lui permet de créer une nouvelle instance du workflow une fois qu'il reçoit un message.  
  
 La liste suivante décrit en détail la configuration par l'hôte du service de workflow pendant l'initialisation.  
  
1.  Crée un hôte de service avec une adresse (http://localhost:8080/Client).  
  
2.  Crée un point de terminaison dans l'hôte de service pour permettre la communication avec l'activité <xref:System.ServiceModel.Activities.Receive> à l'intérieur du workflow.  
  
3.  Configure un magasin d'instances SQL.  
  
4.  Ajoute un comportement de déchargement d'instance qui spécifie les conditions dans lesquelles l'hôte du service de workflow doit décharger une instance de workflow vers le magasin de persistance SQL. Pour cet exemple, il décharge l'instance immédiatement après le passage du workflow à l'état inactif (lorsque le délai est déclenché).  
  
5.  Crée le proxy qui envoie un message à l'activité <xref:System.ServiceModel.Activities.Receive> dans le workflow.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Configurez la base de données de persistance.  
  
    1.  Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Accédez à la [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] active (C:\Windows\Microsoft.NET\Framework\v4. X\\).  
  
    3.  Modifiez le fichier WorkflowManagementService.exe.config et ajoutez la chaîne de connexion suivante à l'intérieur de l'élément <`database`>.  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  Accédez au répertoire DurableDelay\CS.  
  
    5.  Exécutez Setup.cmd.  
  
2.  Exécutez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] à l’aide d’autorisations élevées en cliquant sur le [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icône et en sélectionnant **exécuter en tant qu’administrateur**.  
  
3.  Ouvrez le fichier solution Delay.sln.  
  
4.  Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
5.  Appuyez sur CTRL+F5 pour exécuter la solution.  
  
#### <a name="to-uninstall-this-sample"></a>Pour désinstaller cet exemple  
  
1.  Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Accédez au répertoire DurableDelay\CS.  
  
3.  Exécutez Cleanup.cmd.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`