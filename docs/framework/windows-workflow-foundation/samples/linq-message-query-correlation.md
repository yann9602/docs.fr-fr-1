---
title: "Corr&#233;lation de requ&#234;te de message LINQ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Corr&#233;lation de requ&#234;te de message LINQ
Cet exemple montre comment effectuer une corrélation basée sur le contenu à l'aide d'une implémentation <xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisée par opposition au <xref:System.ServiceModel.XPathMessageQuery> fourni par le système.  
  
## Démonstrations  
 <xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisé, corrélation basée sur le contenu.  
  
## Discussion  
 Cet exemple montre le mode d'extension à partir de la classe de base <xref:System.ServiceModel.Dispatcher.MessageQuery> pour les besoins de la corrélation.L'implémentation personnalisée, `LinqMessageQuery`, permet aux utilisateurs de fournir un XName à rechercher dans le message à l'aide de XLinq.Les données récupérées par la requête sont utilisées pour former la clé de corrélation afin de distribuer des messages à l'instance de workflow appropriée.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Cet exemple expose un service de workflow à l'aide de points de terminaison HTTP.Pour exécuter cet exemple, des listes de contrôle d'accès \(ACL\) d'URL appropriées doivent être ajoutées \(pour plus d'informations, consultez [Configuration de HTTP et HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)\), en exécutant Visual Studio en tant qu'administrateur ou en exécutant la commande suivante à une invite de commandes avec élévation de privilèges pour ajouter les listes de contrôle d'accès \(ACL\) appropriées.Vérifiez que vos domaine et nom d'utilisateur sont substitués.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  Une fois les listes de contrôle d'accès \(ACL\) d'URL ajoutées, effectuez les étapes suivantes.  
  
    1.  Générez la solution.  
  
    2.  Définissez plusieurs projets de démarrage en cliquant avec le bouton droit sur la solution, puis en sélectionnant **Définir les projets de démarrage**.Ajoutez **Service** et **Client** \(dans cet ordre\) en tant que plusieurs projets de démarrage.  
  
    3.  Exécutez l'application.La console cliente affiche un workflow qui envoie une commande et reçoit l'ID de bon de commande, puis confirme par la suite la commande.La fenêtre Service affichera les demandes en cours de traitement.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`