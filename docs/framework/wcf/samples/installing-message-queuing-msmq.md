---
title: "Installation de Message Queuing (MSMQ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Installation de Message Queuing (MSMQ)
Les procédures suivantes indiquent comment installer Message Queuing 4.0 et Message Queuing 3.0.  
  
> [!NOTE]
>  Message Queuing 4.0 n'est pas disponible dans [!INCLUDE[wxp](../../../../includes/wxp-md.md)] et [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
#### Pour installer Message Queuing 4.0 sur Windows Server 2008 ou Windows Server 2008 R2  
  
1.  Dans le Gestionnaire de serveur, cliquez sur **Fonctionnalités**.  
  
2.  Dans le volet droit, sous **Résumé des fonctionnalités**, cliquez sur **Ajouter des fonctionnalités**.  
  
3.  Dans la fenêtre résultante, développez **Message Queuing**.  
  
4.  Développez **Services Message Queuing**.  
  
5.  Cliquez sur **Intégration des services de domaine Active Directory** \(pour les ordinateurs liés à un domaine\), puis cliquez sur **Prise en charge HTTP**.  
  
6.  Cliquez sur **Suivant**,puis sur **Installer**.  
  
#### Pour installer Message Queuing 4.0 sur Windows 7 ou Windows Vista  
  
1.  Ouvrez le **Panneau de configuration**.  
  
2.  Cliquez sur **Programmes**, puis dans **Programmes et fonctionnalités**, cliquez sur **Activer ou désactiver des fonctionnalités Windows**.  
  
3.  Développez Microsoft Message Queue Server \(MSMQ\), développez le noyau du serveur MSMQ \(Microsoft Message Queue\), puis activez les cases à cocher des composants Message Queuing à installer :  
  
    -   Intégration des services de domaine Active Directory MSMQ \(pour les ordinateurs liés à un domaine\).  
  
    -   Prise en charge HTTP MSMQ.  
  
4.  Cliquez sur **OK**.  
  
5.  Si vous êtes invité à redémarrer l'ordinateur, cliquez sur **OK** pour terminer l'installation.  
  
#### Pour installer Message Queuing 3.0 sur Windows XP et Windows Server 2003  
  
1.  Ouvrez le **Panneau de configuration**.  
  
2.  Cliquez sur **Ajout\/Suppression de programmes** puis cliquez sur **Ajouter des composants Windows**.  
  
3.  Sélectionnez Message Queuing et cliquez sur **Détails**.  
  
    > [!NOTE]
    >  Si vous exécutez [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], sélectionnez Serveur d'applications pour accéder à Message Queuing.  
  
4.  Vérifiez que l'option Prise en charge HTTP MSMQ est activée dans la page de détails.  
  
5.  Cliquez sur **OK** pour fermer la page de détails, puis cliquez sur **Suivant**.Terminez l'installation.  
  
6.  Si vous êtes invité à redémarrer l'ordinateur, cliquez sur **OK** pour terminer l'installation.  
  
## Voir aussi  
 [Instructions d'installation](../../../../docs/framework/wcf/samples/set-up-instructions.md)