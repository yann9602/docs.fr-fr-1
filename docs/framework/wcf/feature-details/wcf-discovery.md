---
title: Discovery WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0c9b083180870e451816b54dddc10068ca7ec5db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-discovery"></a>Discovery WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournit la prise en charge pour permettre aux services d'être détectables pendant l'exécution d'une façon interopérable à l'aide du protocole WS-Discovery. Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent annoncer leur disponibilité au réseau par un message de multidiffusion ou à un serveur proxy de découverte. Les applications clientes peuvent rechercher sur le réseau ou dans un serveur proxy de découverte des services qui répondent à un jeu de critères. Les rubriques de cette section donnent une vue d’ensemble et décrivent en détail le modèle de programmation pour cette fonctionnalité.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble de la découverte WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 Donne une vue d'ensemble de la prise en charge de WS-Discovery offerte par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Modèle objet de découverte WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)  
 Décrit les classes du modèle objet et l'extensibilité de la prise en charge de WS-Discovery.  
  
 [Comment : ajouter par programmation la fonctionnalité de découverte pour un Service WCF et un Client](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 Indique comment rendre un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] détectable.  
  
 [Implémentation d’un Proxy de découverte](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 Décrit les étapes nécessaires pour implémenter un proxy de découverte, un service détectable qui s'enregistre avec le proxy de découverte et un client qui utilise le proxy de découverte pour rechercher le service détectable.  
  
 [Contrôle de version de découverte](../../../../docs/framework/wcf/feature-details/discovery-versioning.md)  
 Donne une vue d’ensemble d’une implémentation prototype de nouvelles fonctionnalités de découverte. Elle donne également une vue d'ensemble de la manière de sélectionner la version de découverte à utiliser.  
  
 [Configuration de la découverte dans un fichier de Configuration](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)  
 Indique comment configurer la découverte dans la configuration.  
  
 [Utilisation du canal Client de découverte](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 Indique comment utiliser un canal client de découverte lors de l'écriture d'une application cliente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].
