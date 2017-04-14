---
title: "Introduction &#224; l&#39;extensibilit&#233; | Microsoft Docs"
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
  - "extensibilité (WCF)"
  - "WCF [WCF], extensibilité"
  - "Windows Communication Foundation [WCF], extensibilité"
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Introduction &#224; l&#39;extensibilit&#233;
Le modèle d'application [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] est conçu pour répondre en grande partie aux spécifications de communication de toute application distribuée.  Néanmoins, il existe des situations qui ne sont pas prises en charge par le modèle d'application par défaut et les implémentations fournies par le système.  Le modèle d'extensibilité de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est destiné à prendre en charge des scénarios personnalisés en vous permettant de modifier le comportement du système à tout niveau, et même de remplacer le modèle d'application dans son intégralité.  Cette rubrique présente les différentes zones d'extension et fournit des informations détaillées sur chacune d'elles.  
  
## Zones à étendre  
 Vous pouvez étendre les zones suivantes :  
  
-   Le runtime de l'application.  Cela permet d'étendre la distribution et le traitement des messages pour l'application.  Dans ce cadre, vous pouvez également étendre le système de sécurité, le système de métadonnées, le système de sérialisation, ainsi que les liaisons et éléments de liaison qui connectent l'application au système de canaux sous\-jacent.  
  
-   Le canal et le runtime du canal.  Cela permet d'étendre le système qui fonctionne au niveau du message, en fournissant la prise en charge du protocole, du transport et de l'encodage.  
  
-   Le runtime de l'hôte.  Cela permet d'étendre la relation du domaine de l'application d'hébergement avec le runtime du canal de l'application.  
  
### Extension du runtime de l'application  
 Dans les applications [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], les messages destinés à un canal correspondant doivent être distingués des messages destinés à l'application elle\-même.  Les messages de canaux prennent en charge des fonctionnalités relatives aux canaux, comme l'établissement d'une conversation sécurisée ou d'une session fiable.  Ces messages ne sont pas disponibles pour le runtime de l'application. Ils sont traités avant que la couche Application ne soit impliquée.  
  
 Les messages d'application contiennent des données destinées à une opération de client ou de service que vous ou votre client a créée.  Ces messages sont disponibles pour le système d'extension de niveau application sous la forme de message ou d'objet, en fonction de vos besoins.  
  
 Tous les messages passent par le système de canaux. Seuls les messages d'application sont passés entre le système de canaux et l'application.  Pour créer de nouvelles fonctionnalités de niveau canal, vous devez étendre le système de canaux.  Pour créer de nouvelles fonctionnalités de niveau application, vous devez étendre le runtime du service ou du client \(respectivement, répartiteurs et fabrications de canaux\).  [!INCLUDE[crabout](../../../includes/crabout-md.md)] l'extension du runtime de l'application, consultez [Extension de ServiceHost et de la couche de modèle de service](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### Extension de la sécurité  
 Pour créer des mécanismes de sécurité personnalisés comme des jetons et des informations d'identification, vous devez étendre le système de sécurité.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Extension de la sécurité](../../../docs/framework/wcf/extending/extending-security.md).  
  
#### Extension des métadonnées  
 Pour exposer vos métadonnées différemment de ce qui est prévu par défaut, vous devez étendre le système de métadonnées.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Extension du système de métadonnées](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
#### Extension de la sérialisation  
 Pour créer des encodeurs personnalisés, proposer des substituts de données ou pour tout autre travail impliquant la personnalisation des données transférées, vous devez étendre le système de sérialisation.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Extension des encodeurs et des sérialiseurs](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).  
  
#### Extension de liaisons  
 Pour associer des canaux de transport ou de protocole à la couche Application, vous devez étendre le système de liaison.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Extension de liaisons](../../../docs/framework/wcf/extending/extending-bindings.md).  
  
### Extension du système de canaux  
 Pour créer des canaux qui prennent en charge des fonctionnalités de transport ou de protocole personnalisées, consultez [Extension de la couche du canal](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
### Extension du système d'hébergement de service  
 Pour modifier le modèle d'application à l'échelle du service, vous devez étendre la classe <xref:System.ServiceModel.ServiceHostBase?displayProperty=fullName>.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Extension de ServiceHost et de la couche de modèle de service](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Pour modifier la relation entre le domaine de l'application d'hébergement et l'hôte de service, vous devez étendre la classe <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=fullName>.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Extension de l'hébergement à l'aide de ServiceHostFactory](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).  
  
## Voir aussi  
 [Extension de WCF](../../../docs/framework/wcf/extending/extending-wcf.md)