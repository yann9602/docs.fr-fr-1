---
title: "Points de terminaison Windows Communication Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "points de terminaison (WCF)"
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Points de terminaison Windows Communication Foundation
Toute communication avec un service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] se produit par l'intermédiaire des *points de terminaison* du service.  Les points de terminaison fournissent au client l'accès aux fonctionnalités offertes par un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 Pour obtenir une vue d'ensemble de la création d'un point de terminaison, consultez [Vue d'ensemble de la création de points de terminaison](../../../docs/framework/wcf/endpoint-creation-overview.md).  Chaque point de terminaison contient :  
  
-   Une adresse qui indique où rechercher le point de terminaison.  
  
-   Une liaison qui spécifie comment un client peut communiquer avec le point de terminaison.  
  
-   Un contrat qui identifie les méthodes disponibles.  
  
 Pour obtenir une description de la manière dont les parties individuelles d'un point de terminaison sont spécifiées, consultez :  
  
-   [Spécification d'une adresse de point de terminaison](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
-   [Utilisation de liaisons pour configurer des services et des clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
-   [Conception et implémentation de services](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## Dans cette section  
 [Vue d'ensemble de la création de points de terminaison](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 Décrit la structure d'un point de terminaison et explique comment définir un point de terminaison dans la configuration et dans le code, ainsi que la manière d'utiliser les points de terminaison par défaut, les liaisons et les comportements fournis par le runtime.  
  
 [Spécification d'une adresse de point de terminaison](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 Décrit comment la communication avec un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a lieu par l'intermédiaire des points de terminaison.  
  
 [Comment : créer un point de terminaison de service dans la configuration.](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 Montre comment créer un point de terminaison de service dans la configuration.  
  
 [Comment : créer un point de terminaison de service dans le code](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 Montre comment créer un point de terminaison de service dans le code.  
  
 [Publication de points de terminaison de métadonnées](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 Montre comment publier des métadonnées en publiant des points de terminaison de métadonnées dans la configuration et dans le code.  
  
## Référence  
 <xref:System.ServiceModel.EndpointAddress>  
  
## Rubriques connexes  
 [Cycle de vie de la programmation de base](../../../docs/framework/wcf/basic-programming-lifecycle.md)