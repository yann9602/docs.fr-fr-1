---
title: "Canaux WCF prenant en charge ReceiveContext | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Canaux WCF prenant en charge ReceiveContext
Cet exemple montre l'utilité de canaux WCF prenant en charge <xref:System.ServiceModel.Channels.ReceiveContext>.  L'exemple implémente un service pour rechercher le produit de deux nombres à l'aide d'un canal NetMSMQ.  
  
 La classe <xref:System.ServiceModel.Channels.ReceiveContext> permet à une application de décider s'il faut accéder au message ou le laisser dans la file d'attente pour un traitement supplémentaire, même une fois le contenu du message inspecté.  Dans cet exemple, un client envoie des entiers aléatoires à une file d'attente transactionnelle.  Le service `ProductCalculator` reçoit les messages et en inspecte le contenu, en l'occurrence, des entiers, afin de déterminer si le produit peut être calculé.  Si l'opération réalisée par le service ne calcule pas le produit, le message est remis en file d'attente et peut à nouveau être reçu par le service qui écoute la file d'attente.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer :  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, accédez à la page des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant :  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### Pour utiliser cet exemple  
  
1.  Vérifiez que Microsoft Message Queuing \(MSMQ\) est installé.  
  
    1.  Pour installer MSMQ sur [!INCLUDE[lserver](../../../../includes/lserver-md.md)] :  
  
        1.  Dans le **Gestionnaire de serveur**, cliquez sur **Fonctionnalités**.  
  
        2.  Dans le volet droit, sous **Résumé des fonctionnalités**, cliquez sur **Ajouter des fonctionnalités**.  
  
        3.  Dans la fenêtre résultante, développez **Message Queuing**.  
  
        4.  Développez **Services Message Queuing**.  
  
        5.  Cliquez sur **Intégration des services de domaine Active Directory** \(pour les ordinateurs liés à un domaine\), puis cliquez sur **Prise en charge HTTP**.  
  
        6.  Cliquez sur **Suivant**, puis sur **Installer**.  
  
    2.  Pour installer MSMQ sur [!INCLUDE[wv](../../../../includes/wv-md.md)] :  
  
        1.  Ouvrez le **Panneau de configuration**.  
  
        2.  Cliquez sur **Programmes**, puis dans **Programmes et fonctionnalités**, cliquez sur **Activer ou désactiver des fonctionnalités Windows**.  
  
        3.  Développez **Microsoft Message Queue Server \(MSMQ\)**, développez **Noyau du serveur MSMQ \(Microsoft Message Queue\)**, puis activez les cases à cocher des composants Message Queuing à installer :  
  
            -   Serveur Message Queuing  
  
            -   Intégration des services de domaine Active Directory MSMQ \(pour les ordinateurs liés à un domaine\).  
  
            -   Prise en charge HTTP MSMQ  
  
        4.  Cliquez sur **OK**.  
  
        5.  Si vous êtes invité à redémarrer l'ordinateur, cliquez sur **OK** pour terminer l'installation.  
  
2.  Assurez\-vous que [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] est installé sur l'ordinateur.  
  
3.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution ReceiveContextProductGenerator.sln.  
  
4.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
5.  Pour exécuter la solution, appuyez sur Ctrl\+F5.