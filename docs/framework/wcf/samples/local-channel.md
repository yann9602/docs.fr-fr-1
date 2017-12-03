---
title: Local Channel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5bf10b872d484f8b4b40de7c332f80280e2ac912
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="local-channel"></a>Local Channel
Local Channel est un canal du transport [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilisé pour la communication dans un même domaine d'application. Cela peut être utile pour les scénarios où le client et le service s’exécutent dans le même domaine d’application et où la charge liée à la pile de canaux WCF classique (sérialisation et désérialisation de messages) doit être évitée.  
  
## <a name="demonstrates"></a>Démonstrations  
 Local Channel  
  
## <a name="discussion"></a>Discussion  
 Cet exemple est composé de deux fichiers projet :  
  
-   **LocalChannel**: la représentation par programme du canal local dans le domaine d’application actuel. Dans ce projet, le composant expéditeur place le message dans une file d'attente en mémoire et le composant récepteur retire le message de la file d'attente pour le recevoir.  
  
-   **ClientAndService**: ce projet héberge un service dans une application console, puis l’exécute un client pour appeler le service à partir du même domaine d’application.  
  
 Le canal local est conçu pour ignorer la pile de canaux et le processus de sérialisation afin de gagner en vitesse. Le canal de transport local est implémenté à l'aide d'une file d'attente pour transporter les appels de service du client au service et pour retourner la valeur au client. Au lieu de sérialiser des paramètres et des valeurs de retour, l'exemple copie les objets.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Générez et exécutez la solution LocalChannel.  
  
2.  L'hôte du service démarre et le client appelle le service en utilisant le canal local. Une fenêtre de console apparaît pour afficher le résultat de l'appel de service.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
