---
title: "Gestion avancée des erreurs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77034a1948b7fc6dd383c9bdb5456917c6082687
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="advanced-error-handling"></a>Gestion avancée des erreurs
Cet exemple illustre le service de routage [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Le service de routage est un composant [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui facilite l'inclusion d'un routeur basé sur le contenu dans votre application. Cet exemple montre comment le service de routage récupère intelligemment suite à des erreurs, en utilisant des transactions et d'autres concepts de messagerie plus complexes, comme la multidiffusion.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a>Détails de l'exemple  
 Dans cet exemple, le service de routage est configuré de façon à lire un message d'une file d'attente MSMQ et à envoyer ce message en multidiffusion à deux listes de files d'attente. Une liste est utilisée pour les files d'attente de service et une autre est utilisée pour les files d'attente d'enregistrement.  
  
 Étant donné que, par défaut, la liaison MSMQ que doit utiliser le service de routage prend en charge l'utilisation de transactions, le service de routage vérifie que le message est transactionnel et qu'il est reçu par au moins une file d'attente de chaque liste avant de signaler à la file d'attente à trafic entrant (`InQ`) que le message a été routé avec succès. Par conséquent, s'il arrive que les deux files d'attente de service ou les deux files d'attente d'enregistrement soient indisponibles, le service de routage signale que le message n'a pas pu être routé et la file d'attente à trafic entrant doit entreprendre une action. Cette action consiste à déplacer le message vers la file d'attente système de lettres mortes.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  > [!IMPORTANT]
    >  Installez MSMQ avant d'exécuter cet exemple. Si MSMQ n'est pas installé, un message d'exception est retourné lors de l'exécution de l'exemple. Vous trouverez des instructions d’installation de MSMQ à [l’installation de Message Queuing (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).  
  
     À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez AdvancedErrorHandling.sln.  
  
2.  Appuyez sur **F5** ou **CTRL + MAJ + B** dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
    1.  Si vous générez l'application avec CTRL+MAJ+B, vous devez démarrer l'application située dans ./RoutingService/bin/debug/RoutingService.exe.  
  
3.  Dans la fenêtre de console, appuyez sur ENTRÉE pour arrêter le client.  
  
4.  Le client retourne différentes statistiques sur les files d'attente dans chaque cas.  
  
    1.  Voici la sortie retournée pour le cas 1 (aucun échec).  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  Voici la sortie retournée pour le cas 3 (échecs des files d'attente du service principal et d'enregistrement).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  Voici la sortie retournée pour le cas 4 (échecs de la file d'attente du service principal et des files d'attente d'enregistrement principale et secondaire).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  Voici la sortie retournée pour le cas 2 (échec de la file d'attente du service principal).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Configurable au moyen d'un code ou d'un fichier App.config  
 L'exemple est fourni en étant configuré de façon à utiliser un fichier App.config pour définir le comportement du routeur. Vous pouvez également renommer le fichier RoutingService\App.config afin qu'il ne soit pas reconnu et remplacer la valeur du champ `configDriven` dans RoutingService\Program.cs par `false` pour utiliser la configuration définie dans le code. Quelle que soit la méthode employée, le comportement de routeur obtenu est le même.  
  
### <a name="scenario"></a>Scénario  
 Cet exemple montre que le service de routage peut gérer des fonctions de messagerie avancées, telles que les transactions et le contexte de réception, et qu'il peut utiliser ces fonctions pour gérer correctement des scénarios d'erreurs.  
  
### <a name="real-world-scenario"></a>Scénario réel  
 Contoso souhaite utiliser des réceptions transactionnelles via le service de routage pour faire en sorte que tous les services concernés reçoivent les informations même dans des conditions d'erreur. La société souhaite en outre que les erreurs soient gérées correctement et automatiquement, et que les échecs soient signalés en cas de non remise de messages malgré l'utilisation d'une logique de gestion des erreurs. À cette fin, elle configure le service de routage de sorte qu’il bascule vers des points de terminaison spécifiques comme prévu et qu’il gère les situations d’erreur, ce qui comprend la création, l’achèvement, ainsi que la restauration/l’abandon de transactions/contextes de réception selon les besoins.  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)
