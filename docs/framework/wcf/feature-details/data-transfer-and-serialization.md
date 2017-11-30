---
title: "Transfert de données et sérialisation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41357c9a039414ac692bac69337b2963d5c6b341
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="data-transfer-and-serialization"></a>Transfert de données et sérialisation
Dans un système connecté, les services et les clients se reposent sur l’échange de données pour accomplir une tâche. En tant que développeur d'un service ou d'un client, vous devez aussi comprendre comment [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] gère les données et la sérialisation des données pour créer des applications qui sont efficaces et d'une maintenance simple.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 Décrit les concepts de base du transfert de données dans les services.  
  
 [À l’aide de contrats de données](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 Définit les contrats de données et la méthode utilisée pour les créer et les utiliser.  
  
 [Sérialiseur de contrat de données](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 Décrit comment accomplir la sérialisation des données avec la classe <xref:System.Runtime.Serialization.DataContractSerializer> ou une extension de la classe <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
 [À l’aide de la classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 Décrit comment et pourquoi utiliser la classe <xref:System.Xml.Serialization.XmlSerializer>, une alternative à la classe <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 [À l’aide de contrats de Message](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 Décrit comment les contrats de message autorisent un contrôle pointu sur les messages SOAP.  
  
 [À l’aide de la classe de Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 Décrit comment utiliser les fonctionnalités de la classe Message.  
  
 [Le filtrage](../../../../docs/framework/wcf/feature-details/filtering.md)  
 Décrit le filtrage qui permet le pré-traitement d'un message selon différents critères.  
  
 [Données volumineuses et diffusion en continu](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 Décrit comment envoyer un grand bloc de données, tel qu'un fichier binaire.  
  
 [Considérations sur la sécurité des données](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 Décrit des éléments à connaître lors de la programmation du transfert de données et de la sérialisation.  
  
 [Présentation de l’architecture de transfert de données](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 Décrit une présentation de la conception totale du transfert de données dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="reference"></a>Référence  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Extension des encodeurs et sérialiseurs](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Bonnes pratiques : gestion des versions des contrats de données](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Gestion des versions des services](../../../../docs/framework/wcf/service-versioning.md)
