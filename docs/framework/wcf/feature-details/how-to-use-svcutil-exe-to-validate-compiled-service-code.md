---
title: "Comment&#160;: utiliser Svcutil.exe pour valider le code de service compil&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Comment&#160;: utiliser Svcutil.exe pour valider le code de service compil&#233;
Vous pouvez utiliser [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour détecter les erreurs dans les configurations et les implémentations de service sans héberger le service.  
  
### Pour valider un service  
  
1.  Compilez votre service dans un fichier exécutable et un ou plusieurs assemblys dépendants.  
  
2.  Ouvrez une invite de commandes du Kit de développement SDK.  
  
3.  À l'invite de commandes, lancez l'outil Svcutil.exe à l'aide du format suivant.  Pour plus d'informations sur les différents paramètres, consultez la section de validation de service de la rubrique [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     Vous devez utiliser l'option `/serviceName` pour indiquer le nom de configuration du service que vous souhaitez valider.  
  
     L'argument `assemblyPath` spécifie le chemin d'accès au fichier exécutable du service et un ou plusieurs assemblys qui contiennent les types de services à valider.  L'assembly exécutable doit avoir un fichier de configuration associé pour fournir la configuration du service.  Vous pouvez utiliser des caractères génériques de ligne de commande standard pour fournir plusieurs assemblys.  
  
## Exemple  
 La commande suivante illustre le service myServiceName implémenté dans le fichier exécutable myServiceHost.exe.  Le fichier de configuration pour le service \(myServiceHost.exe.config\) est chargé automatiquement.  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## Voir aussi  
 [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)