---
title: "Contr&#244;le de l&#39;auto-lancement de l&#39;h&#244;te de service WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WcfOptions"
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Contr&#244;le de l&#39;auto-lancement de l&#39;h&#244;te de service WCF
Vous pouvez contrôler la fonction d'auto\-lancement de l'hôte du service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] \(WcfSvcHost.exe\) pour un projet de bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] lorsque vous déboguez un autre projet dans la même solution [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] contenant plusieurs projets.  
  
 Pour ce faire, cliquez avec le bouton droit sur le projet de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] dans l'**Explorateur de solutions**, sélectionnez **Propriétés**, puis cliquez sur l'onglet **Options WCF**.La case à cocher **Démarrer l'hôte de service WCF lors du débogage d'un autre projet dans la même solution** est activée par défaut.Vous pouvez la désélectionner afin que l'hôte du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] de ce projet spécifique ne démarre pas lorsqu'un autre projet est débogué dans la même solution.  
  
 Ce comportement n'affecte pas le débogage F5 ni les fonctionnalités d'ajout d'une référence de service pour ce projet.  
  
 Cette option est disponible dans le cadre des projets suivants :  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Projet de la bibliothèque du service  
  
-   Projet de la bibliothèque du service du workflow séquentiel  
  
-   Projet de la bibliothèque du service de workflow d'ordinateur d'état  
  
-   Projet de la bibliothèque du service de syndication  
  
## Voir aussi  
 [Hôte de service WCF \(WcfSvcHost.exe\)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)