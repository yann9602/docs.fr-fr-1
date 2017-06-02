---
title: "propri&#233;t&#233; de cl&#233; &#233;trang&#232;re | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# propri&#233;t&#233; de cl&#233; &#233;trang&#232;re
Une *propriété de clé étrangère* dans le modèle EDM \(Entity Data Model\) est une [propriété](../../../../docs/framework/data/adonet/property.md) de type primitif \(ou un jeu de propriétés de type primitif\) sur un [type d'entité](../../../../docs/framework/data/adonet/entity-type.md) qui contient la [clé d'entité](../../../../docs/framework/data/adonet/entity-key.md) d'un autre type d'entité.  
  
 Une propriété de clé étrangère est analogue à une colonne clé étrangère dans une base de données relationnelle.  De la même manière que les colonnes clés étrangères sont utilisées dans une base de données relationnelle pour créer des relations entre les lignes dans des tables, les propriétés de clé étrangère dans un modèle conceptuel sont utilisées pour établir des [associations](../../../../docs/framework/data/adonet/association-type.md) entre les types d'entité.  Une [contrainte d'intégrité référentielle](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) est utilisée pour définir une association entre deux types d'entité lorsque l'un des types a une propriété de clé étrangère.  
  
## Exemple  
 Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`.  Le type d'entité `Book` a une propriété, `PublisherId`, qui référence la clé d'entité du type d'entité `Publisher` lorsque vous définissez une contrainte d'intégrité référentielle sur l'association `PublishedBy`.  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine \(DSL\), appelé [CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) \(Conceptual Schema Definition Language\), pour définir des modèles conceptuels.  Le CSDL suivant utilise la propriété de clé étrangère `PublisherId` pour définir une contrainte d'intégrité référentielle sur l'association `PublishedBy` présentée dans le modèle conceptuel ci\-dessus.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## Voir aussi  
 [Concepts clés d'Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)