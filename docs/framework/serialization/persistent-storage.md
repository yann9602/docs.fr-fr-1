---
title: "Stockage persistant | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sérialisation binaire, stockage persistant"
  - "stockage persistant"
  - "sérialisation, stockage persistant"
ms.assetid: b112c0dd-93e2-4eef-908d-5963f80bab65
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Stockage persistant
Il est souvent nécessaire de stocker la valeur des champs d'un objet sur un disque pour pouvoir récupérer ces données ultérieurement.Bien que cela soit facile à accomplir sans utiliser la sérialisation, cette méthode est souvent fastidieuse et susceptible d'entraîner des erreurs. Elle devient en outre de plus en plus complexe lorsque vous devez suivre une hiérarchie d'objets.Imaginez que vous deviez enregistrer des données au sein d'une grande application d'entreprise qui contient des milliers d'objets et que vous deviez écrire du code pour enregistrer et restaurer des champs et propriétés sur et à partir d'un disque pour chaque objet.La sérialisation offre un mécanisme pratique permettant d'atteindre cet objectif.  
  
 Le Common Language Runtime gère la manière dont les objets sont stockés en mémoire et fournit un mécanisme de sérialisation automatisé à l'aide de la [réflexion](../../../docs/framework/reflection-and-codedom/reflection.md).Lorsqu'un objet est sérialisé, le nom de la classe, l'assembly et tous les membres de données de l'instance de classe sont écrits sur le support de stockage.Les objets stockent souvent des références à d'autres instances dans les variables membres.Lorsque la classe est sérialisée, le moteur de sérialisation effectue un suivi des objets référencés et déjà sérialisés, pour garantir qu'un même objet n'est pas sérialisé plusieurs fois.L'architecture de sérialisation fournie avec le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] gère correctement et de manière automatique des graphiques d'objets et des références circulaires.La seule spécification définie pour les graphiques d'objets est que tous les objets, référencés par objet sérialisé, doivent également être marqués comme [Serializable](frlrfSystemSerializableAttributeClassTopic) \(pour plus d'informations, consultez [Sérialisation de base](../../../docs/framework/serialization/basic-serialization.md)\).Si tel n'est pas le cas, une exception est levée lorsque le sérialiseur tente de sérialiser l'objet non marqué.  
  
 Lorsque la classe sérialisée est désérialisée, elle est recréée et les valeurs de toutes les données membres sont restaurées automatiquement.  
  
## Voir aussi  
 [Concepts de sérialisation](../../../docs/framework/serialization/serialization-concepts.md)   
 [Remote Objects](http://msdn.microsoft.com/fr-fr/515686e6-0a8d-42f7-8188-73abede57c58)   
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)