---
title: "Entity Data Model&#160;: espaces de noms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Entity Data Model&#160;: espaces de noms
Un espace de noms dans le modèle EDM \(Entity Data Model\) est un conteneur abstrait pour les [types d'entité](../../../../docs/framework/data/adonet/entity-type.md), les [types complexes](../../../../docs/framework/data/adonet/complex-type.md) et les [associations](../../../../docs/framework/data/adonet/association-type.md).  Les espaces de noms dans le modèle EDM sont semblables aux espaces de noms dans un langage de programmation : ils fournissent le contexte pour les objets qu'ils contiennent et offrent un moyen de lever l'ambiguïté entre les objets qui portent le même nom \(mais qui sont contenus dans des espaces de noms différents\).  
  
## Exemple  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine \(DSL\), appelé [CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) \(Conceptual Schema Definition Language\), pour définir des modèles conceptuels.  Le CSDL suivant utilise un espace de noms pour identifier un type défini dans un modèle conceptuel différent.  L'exemple définit un type d'entité \(`Publisher`\) qui a une propriété de type complexe \(`Address`\) importée à partir de l'espace de noms `ExtendedBooksModel`.  Notez que l'élément `Using` indique qu'un espace de noms a été importé.  Notez également que le type de la propriété `Address` est défini à l'aide de son nom qualifié complet \(`ExtendedBooksModel.Address`\), ce qui indique que ce type est défini dans l'espace de noms `ExtendedBooksModel`.  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## Voir aussi  
 [Concepts clés d'Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)