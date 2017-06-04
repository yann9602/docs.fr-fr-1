---
title: "Agilit&#233; de chiffrement dans s&#233;curit&#233; WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# Agilit&#233; de chiffrement dans s&#233;curit&#233; WCF
Cet exemple montre comment effectuer des spécifications dans un algorithme standard ou personnalisé afin de fournir une implémentation de chiffrement agile dans un client et un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  Cet exemple est composé des projets suivants :  
  
 Service  
 Service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] auto\-hébergé qui implémente l'interface `ICalculator` et sécurise le point de terminaison à l'aide du <xref:System.ServiceModel.WsHttpBinding> avec la session sécurisée et la session fiable désactivées.  Le service définit une classe `SecurityAlgorithmSuite` personnalisée pour spécifier les algorithmes de chiffrement à utiliser pour la sécurité du message.  
  
 Client  
 Client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui accède au service après une authentification réussie.  Il appelle les opérations exposées par l'interface `ICalculator` et implémentées par le service.  Le client définit également la même classe `SecurityAlgorithmSuite` personnalisée pour spécifier les algorithmes de chiffrement à utiliser pour la sécurité du message.  
  
### Pour utiliser cet exemple  
  
1.  Ouvrez la solution CryptoAgility.sln dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Appuyez sur Ctrl\+Maj\+B pour générer la solution.  
  
3.  Ouvrez l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], accédez au répertoire \\WCF\\Basic\\Security\\CryptoAgility\\Service\\bin et exécutez le fichier service.exe avec des privilèges d'administrateur en cliquant avec le bouton droit sur service.exe et en sélectionnant **Exécuter en tant qu'administrateur**.  
  
4.  Accédez au répertoire \\WCF\\Basic\\Security\\CryptoAgility\\Client\\bin et exécutez le fichier client.exe normalement.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, accédez à la page des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## Voir aussi  
 [Sécurité](../../../../docs/framework/wcf/feature-details/security.md)