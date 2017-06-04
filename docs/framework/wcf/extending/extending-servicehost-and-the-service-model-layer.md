---
title: "Extension de ServiceHost et de la couche de mod&#232;le de service | Microsoft Docs"
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
  - "extension des modèles de service (WCF)"
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Extension de ServiceHost et de la couche de mod&#232;le de service
La couche de modèle de service est chargée d'extraire des messages entrants des canaux sous\-jacents, de les traduire dans des appels de méthode dans le code d'application et de renvoyer les résultats à l'appelant.Les extensions de modèle de service modifient ou implémentent le comportement et les fonctionnalités d'exécution et de communication qui impliquent des fonctionnalités de répartiteur ou client, des comportements personnalisés, l'interception de messages et de paramètres et d'autres fonctionnalités d'extensibilité.  
  
## Dans cette section  
 [Extension de clients](../../../../docs/framework/wcf/extending/extending-clients.md)  
 Décrit les interfaces qui peuvent intercepter et modifier l'exécution du client, ainsi que les classes dans lesquelles vous pouvez insérer vos extensions personnalisées dans les applications clientes.Par exemple, vous pouvez exécuter la journalisation des messages client personnalisée, exécuter une sérialisation personnalisée des messages, et ainsi de suite.  
  
 [Extension des répartiteurs](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 Décrit les interfaces qui peuvent intercepter et modifier l'exécution d'un service, ainsi que les classes dans lesquelles vous pouvez insérer vos extensions personnalisées dans les applications de service.Par exemple, vous pouvez exécuter la journalisation personnalisée du service, une validation des messages côté service, une répartition personnalisée, et ainsi de suite.  
  
 [Objets extensibles](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 Décrit les cinq objets extensibles et le modèle <xref:System.ServiceModel.IExtensibleObject%601>.Le modèle d'objet extensible est utilisé pour étendre des classes d'exécution existantes à l'aide de nouvelles fonctionnalités ou ajouter un nouvel état à un objet.Les extensions, attachées à l'un des objets extensibles, permettent aux comportements à des étapes très différentes du traitement d'accéder à l'état partagé et aux fonctionnalités attachés à un objet extensible commun qui leur est accessible.  
  
 [Configuration et extension de l'exécution à l'aide de comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 Pour modifier des paramètres ou insérer des extensions dans l'exécution de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous devez utiliser les comportements.WCF inclut des comportements implémentés par le système pour contrôler la limitation, l'instanciation et de nombreux autres aspects des services et des opérations.Cette section décrit comment créer vos propres comportements personnalisés et les rendre disponibles pour les utiliser par programme et à l'aide de fichiers de configuration.  
  
 [Extension de l'hébergement à l'aide de ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 Décrit comment développer <xref:System.ServiceModel.ServiceHostBase?displayProperty=fullName> et <xref:System.ServiceModel.ServiceHost?displayProperty=fullName> et comment utiliser les classes <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=fullName> pour personnaliser l'environnement hôte.  
  
## Référence  
  
## Rubriques connexes