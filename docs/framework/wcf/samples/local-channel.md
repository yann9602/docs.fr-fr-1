---
title: "Local Channel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Local Channel
Local Channel est un canal du transport [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilisé pour la communication dans un même domaine d'application.  Cela peut être utile pour les scénarios où le client et le service s'exécutent dans le même domaine d'application et où la charge liée à la pile de canaux WCF classique \(sérialisation et désérialisation de messages\) doit être évitée.  
  
## Démonstrations  
 Local Channel  
  
## Discussion  
 Cet exemple est composé de deux fichiers projet :  
  
-   **LocalChannel** Représentation sous forme de programme du canal local dans le domaine d'application actuel.  Dans ce projet, le composant expéditeur place le message dans une file d'attente en mémoire et le composant récepteur retire le message de la file d'attente pour le recevoir.  
  
-   **ClientAndService** Ce projet héberge un service dans une application console, puis exécute un client pour appeler le service depuis le même domaine d'application.  
  
 Le canal local est conçu pour ignorer la pile de canaux et le processus de sérialisation afin de gagner en vitesse.  Le canal de transport local est implémenté à l'aide d'une file d'attente pour transporter les appels de service du client au service et pour retourner la valeur au client.  Au lieu de sérialiser des paramètres et des valeurs de retour, l'exemple copie les objets.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Générez et exécutez la solution LocalChannel.  
  
2.  L'hôte du service démarre et le client appelle le service en utilisant le canal local.  Une fenêtre de console apparaît pour afficher le résultat de l'appel de service.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`