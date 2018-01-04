---
title: "Agilité de chiffrement dans sécurité WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7d99ada67255d0ced8bbabc2ab6fc645e6ba9e35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cryptographic-agility-in-wcf-security"></a>Agilité de chiffrement dans sécurité WCF
Cet exemple montre comment effectuer des spécifications dans un algorithme standard ou personnalisé afin de fournir une implémentation de chiffrement agile dans un client et un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Cet exemple est composé des projets suivants :  
  
 Service  
 Il s’agit d’un auto-hébergé [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service qui implémente le `ICalculator` d’interface et sécurise le point de terminaison à l’aide de la <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> avec la session sécurisée et la session fiable désactivée. Le service définit une classe `SecurityAlgorithmSuite` personnalisée pour spécifier les algorithmes de chiffrement à utiliser pour la sécurité du message.  
  
 Client  
 Client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui accède au service après une authentification réussie. Il appelle les opérations exposées par l'interface `ICalculator` et implémentées par le service. Le client définit également la même classe `SecurityAlgorithmSuite` personnalisée pour spécifier les algorithmes de chiffrement à utiliser pour la sécurité du message.  
  
### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Ouvrez la solution CryptoAgility.sln dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
3.  Ouvrez [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] , accédez au répertoire \WCF\Basic\Security\CryptoAgility\Service\bin et exécutez le fichier service.exe avec des privilèges d’administrateur en cliquant sur service.exe et en sélectionnant **exécuter en tant qu’administrateur**.  
  
4.  Accédez au répertoire \WCF\Basic\Security\CryptoAgility\Client\bin et exécutez le fichier client.exe normalement.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité](../../../../docs/framework/wcf/feature-details/security.md)
