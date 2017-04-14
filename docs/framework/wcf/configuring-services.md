---
title: "Configuration des services | Microsoft Docs"
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
  - "configuration [WCF]"
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# Configuration des services
Une fois que vous avez conçu et implémenté votre contrat de service, vous êtes prêt à configurer votre service.  C'est à ce stade que vous définissez et personnalisez la manière dont votre service est exposé aux clients, notamment l'adresse de son emplacement, l'encodage du transport et du message qu'il utilise pour envoyer et recevoir des messages, et le type de sécurité qu'il nécessite.  
  
 La configuration utilisée dans ce scénario comprend toutes les méthodes, de manière impérative dans le code ou à l'aide d'un fichier de configuration, permettant de définir et de personnaliser les divers aspects d'un service, tels que la spécification de ses adresses de point de terminaison, les transports utilisés et ses méthodes de sécurité.  Dans la pratique, l'écriture de la configuration est une partie importante de la programmation des applications [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
## Dans cette section  
 [Configuration simplifiée](../../../docs/framework/wcf/simplified-configuration.md)  
 Depuis [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est fourni avec un nouveau modèle de configuration par défaut qui simplifie les spécifications de configuration de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  Si vous ne fournissez aucune configuration [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour un service particulier, le runtime configure automatiquement votre service à l'aide des liaisons, des comportements et des points de terminaison par défaut.  
  
 [Configuration des services à l'aide de fichiers de configuration](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 Un service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] est configurable à l'aide de la technologie de configuration [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  Le plus souvent, les éléments XML sont ajoutés au fichier Web.config pour un site IIS \(Internet Information Services\) qui héberge un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  Les éléments vous permettent de modifier des détails, tels que les adresses de point de terminaison \(les adresses réelles qui communiquent avec le service\), à partir de chaque ordinateur individuel.  
  
 [Liaisons](../../../docs/framework/wcf/bindings.md)  
 De plus, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] inclut plusieurs configurations fournies par le système courantes sous la forme de liaisons qui vous permettent de sélectionner rapidement les fonctionnalités les plus simples permettant à un client et à un service de communiquer, en particulier les transports, la sécurité et les encodages de message utilisés.  
  
 [points de terminaison](../../../docs/framework/wcf/endpoints.md)  
 Toute communication avec un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] se produit par l'intermédiaire des *points de terminaison* du service.  Les points de terminaison contiennent le contrat, les informations de configuration spécifiées dans les liaisons, et les adresses qui indiquent où rechercher le service ou comment obtenir des informations sur le service.  
  
 [Sécurisation de services](../../../docs/framework/wcf/securing-services.md)  
 À l'aide de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et des mécanismes de sécurité existants, vous pouvez implémenter la confidentialité, l'intégrité, l'authentification et l'autorisation dans tout service.  Vous pouvez aussi auditer les succès et les défaillances de la sécurité.  
  
 [Création de services pouvant interagir avec le profil Basic Profile 1.1 de WS\-I](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 Les spécifications pour déployer un service interopérable avec les services et les clients sur n'importe quelle autre plateforme ou système d'exploitation sont définies dans la spécification WS\-I Basic Profile 1.1.  
  
## Référence  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## Rubriques connexes  
 [Cycle de vie de la programmation de base](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [Conception et implémentation de services](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [Hébergement de services](../../../docs/framework/wcf/hosting-services.md)  
  
 [Génération de clients](../../../docs/framework/wcf/building-clients.md)  
  
 [Introduction à l'extensibilité](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [Administration et diagnostics](../../../docs/framework/wcf/diagnostics/index.md)  
  
## Voir aussi  
 [Programmation WCF de base](../../../docs/framework/wcf/basic-wcf-programming.md)   
 [Vue d'ensemble conceptuelle](../../../docs/framework/wcf/conceptual-overview.md)   
 [Informations détaillées sur les fonctionnalités de WCF](../../../docs/framework/wcf/feature-details/index.md)