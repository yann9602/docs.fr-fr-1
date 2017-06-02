---
title: "contrainte d&#39;int&#233;grit&#233; r&#233;f&#233;rentielle | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# contrainte d&#39;int&#233;grit&#233; r&#233;f&#233;rentielle
Une *contrainte d'intégrité référentielle* dans le modèle EDM \(Entity Data Model\) est semblable à une contrainte d'intégrité référentielle dans une base de données relationnelle.  De la même manière qu'une ou plusieurs colonnes d'une table de base de données peuvent référencer la clé primaire d'une autre table, une ou plusieurs [propriétés](../../../../docs/framework/data/adonet/property.md) d'un [type d'entité](../../../../docs/framework/data/adonet/entity-type.md) peuvent référencer la [clé d'entité](../../../../docs/framework/data/adonet/entity-key.md) d'un autre type d'entité.  Le type d'entité référencé est appelé *terminaison principale* de la contrainte.  Le type d'entité qui référence la terminaison principale est appelé *terminaison dépendante* de la contrainte.  
  
 Une contrainte d'intégrité référentielle est définie dans le cadre d'une [association](../../../../docs/framework/data/adonet/association-type.md) entre deux types d'entité.  La définition d'une contrainte d'intégrité référentielle spécifie les informations suivantes :  
  
-   Terminaison principale de la contrainte.  \(Type d'entité dont la clé d'entité est référencée par la terminaison dépendante.\)  
  
-   Clé d'entité de la terminaison principale.  
  
-   Terminaison dépendante de la contrainte.  \(Type d'entité dont une ou plusieurs propriétés référencent la clé d'entité de la terminaison principale.\)  
  
-   Propriété ou propriétés de référence de la terminaison dépendante.  
  
 Les contraintes d'intégrité référentielle dans le modèle EDM ont pour objectif de vérifier que des associations valides existent toujours.  Pour plus d'informations, consultez [propriété de clé étrangère](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## Exemple  
 Le diagramme suivant montre un modèle conceptuel avec deux associations : `WrittenBy` et `PublishedBy`.  Le type d'entité `Book` a une propriété, `PublisherId`, qui référence la clé d'entité du type d'entité `Publisher` lorsque vous définissez une contrainte d'intégrité référentielle sur l'association `PublishedBy`.  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine \(DSL\), appelé [CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) \(Conceptual Schema Definition Language\), pour définir des modèles conceptuels.  Le CSDL suivant définit une contrainte d'intégrité référentielle sur l'association `PublishedBy` présentée dans le modèle conceptuel ci\-dessus.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## Voir aussi  
 [Concepts clés d'Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)