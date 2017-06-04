---
title: "Exemple Workflow Discovery | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Exemple Workflow Discovery
Cet exemple montre comment rendre un service de workflow détectable et comment créer une activité de code personnalisée qui recherche un service particulier.  
  
## Démonstrations  
 Activité de recherche de découverte et utilisation de workflow  
  
## Discussion  
 Dans la première partie de l'exemple, un service de workflow est rendu détectable à l'aide de la configuration.La configuration peut également être utilisée pour appliquer convenablement le service avec des métadonnées personnalisées \(telles que des portées\).Sur le client, l'exemple utilise une activité de code personnalisée, qui utilise la découverte pour rechercher un service correspondant à un contrat particulier.L'activité de code produit un URI, utilisé ultérieurement par une activité d'envoi.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Cet exemple utilise des points de terminaison HTTP, qui doivent avoir des listes de contrôle d'accès \(ACL\) d'URL appropriés pour fonctionner \(pour plus d'informations, consultez [Configuration de HTTP et HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)\).L'exécution de la commande suivante à partir d'une invite de commandes avec élévation de privilèges doit ajouter les ACL appropriées.Substituez vos domaine et nom d'utilisateur aux arguments suivants si votre interpréteur de commandes ne comprend pas le format variable.  
  
     **netsh http add urlacl url\=http:\/\/\+:8000\/ user\=%DOMAIN%\\%UserName%**  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`