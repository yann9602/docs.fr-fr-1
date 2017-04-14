---
title: "Comment&#160;: installer et configurer des composants d&#39;activation WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "activation HTTP (WCF)"
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Comment&#160;: installer et configurer des composants d&#39;activation WCF
Cette rubrique décrit les étapes requises pour configurer le service d'activation de processus de Windows \(également appelé service WAS\) dans [!INCLUDE[wv](../../../../includes/wv-md.md)] pour héberger des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] qui ne communiquent pas sur des protocoles réseau HTTP.Les sections suivantes définissent les étapes pour cette configuration :  
  
-   Installer \(ou vérifier l'installation\) des composants d'activation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Configurer le service WAS pour prendre en charge un protocole non HTTP.La procédure suivante configure [!INCLUDE[wv](../../../../includes/wv-md.md)] pour l'activation TCP.  
  
 Après avoir installé et avoir configuré le service WAS, consultez [Comment : héberger un service WCF dans WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) pour les procédures permettant de créer un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui expose un point de terminaison non HTTP qui emploie le service WAS.  
  
### Pour installer les composants d'activation non HTTP WCF  
  
1.  Cliquez sur le bouton **Démarrer**, puis sur **Panneau de configuration**.  
  
2.  Cliquez sur **Programmes** et sur **Programmes et fonctionnalités**.  
  
3.  Dans le menu **Tâches**, cliquez sur **Activer ou désactiver des fonctionnalités Windows**.  
  
4.  Recherchez le noeud [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], sélectionnez\-le puis développez\-le.  
  
5.  Sélectionnez la zone **Composants d'activation non\-HTTP WCF** et enregistrez le paramètre.  
  
### Pour configurer le service WAS pour prendre en charge l'activation TCP  
  
1.  Pour assurer la prise en charge de l'activation de net.tcp, le site Web par défaut doit d'abord être lié à un port net.tcp.Vous pouvez utiliser Appcmd.exe installé avec l'ensemble d'outils de gestion [!INCLUDE[iisver](../../../../includes/iisver-md.md)].Dans une fenêtre d'invite de commandes au niveau de l'administrateur, exécutez la commande suivante.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  Cette commande est une ligne unique de texte.Cette commande ajoute une liaison de site net.tcp au site Web par défaut qui écoute sur le port TCP 808, quel que soit le nom d'hôte.  
  
2.  Bien que toutes les applications d'un site partagent la même liaison net.tcp, chacun d'elle peut activer de manière individuelle la prise en charge net.pipe.Afin d'activer net.tcp pour l'application, exécutez la commande suivante à partir d'une invite de commandes au niveau de l'administrateur.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  Cette commande est une ligne unique de texte.Cette commande permet l'accès à l'application \/\<*WCF Application*\> à l'aide de http:\/\/localhost*\/\<WCF Application\>* et net.tcp:\/\/localhost\/*\<WCF Application\>*.  
  
     Supprimez la liaison de site net.tcp que vous avez ajoutée dans le cadre de cet exemple.  
  
     Pour des raisons pratiques, les deux étapes suivantes sont implémentées dans le fichier de commandes RemoveNetTcpSiteBinding.cmd situé dans le répertoire de l'exemple.  
  
    1.  Supprimez le protocole net.tcp de la liste des protocoles activés en exécutant la commande suivante dans une invite de commandes au niveau de l'administrateur.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Cette commande est une ligne unique de texte.  
  
    2.  Supprimez la liaison du site net.tcp en exécutant la commande suivante dans une invite de commandes de niveau élevé :  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  Cette commande est une ligne unique de texte.  
  
### Pour supprimer net.tcp de la liste des protocoles actifs  
  
1.  Pour supprimer net.tcp de la liste des protocoles actifs, exécutez la commande suivante dans une invite de commandes au niveau de l'administrateur.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  Cette commande est une ligne unique de texte.  
  
### Pour supprimer la liaison de site net.tcp  
  
1.  Pour supprimer la liaison de site net.tcp, exécutez la commande suivante dans une fenêtre d'invite de commandes au niveau de l'administrateur.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  Cette commande est une ligne unique de texte.  
  
## Voir aussi  
 [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md)   
 [MSMQ Activation](../../../../docs/framework/wcf/samples/msmq-activation.md)   
 [NamedPipe Activation](../../../../docs/framework/wcf/samples/namedpipe-activation.md)   
 [Fonctionnalités d'hébergement de Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=201276)