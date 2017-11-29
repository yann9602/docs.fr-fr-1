---
title: "contrainte d'intégrité référentielle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 10e469838073b4cf1faba1704b88b47f30b8b3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="referential-integrity-constraint"></a>contrainte d'intégrité référentielle
A *contrainte d’intégrité référentielle* dans le modèle EDM (Entity Data Model) est similaire à une contrainte d’intégrité référentielle dans une base de données relationnelle. De la même façon qu’une colonne (ou les colonnes) à partir d’une table de base de données peuvent faire référence à la clé primaire d’une autre table, un [propriété](../../../../docs/framework/data/adonet/property.md) (ou propriétés) d’un [type d’entité](../../../../docs/framework/data/adonet/entity-type.md) peut faire référence à la [clé d’entité ](../../../../docs/framework/data/adonet/entity-key.md) d’un autre type d’entité. Le type d’entité référencé est appelé le *fin principal* de la contrainte. Le type d’entité qui fait référence à la terminaison principale est appelé le *terminaison dépendante* de la contrainte.  
  
 Une contrainte d’intégrité référentielle est définie en tant que partie d’un [association](../../../../docs/framework/data/adonet/association-type.md) entre deux types d’entité. La définition d'une contrainte d'intégrité référentielle spécifie les informations suivantes :  
  
-   Terminaison principale de la contrainte. (Type d'entité dont la clé d'entité est référencée par la terminaison dépendante.)  
  
-   Clé d'entité de la terminaison principale.  
  
-   Terminaison dépendante de la contrainte. (Type d'entité dont une ou plusieurs propriétés référencent la clé d'entité de la terminaison principale.)  
  
-   Propriété ou propriétés de référence de la terminaison dépendante.  
  
 Les contraintes d'intégrité référentielle dans le modèle EDM ont pour objectif de vérifier que des associations valides existent toujours. Pour plus d’informations, consultez [propriété de clé étrangère](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Exemple  
 Le diagramme suivant montre un modèle conceptuel avec deux associations : `WrittenBy` et `PublishedBy`. Le type d'entité `Book` a une propriété, `PublisherId`, qui référence la clé d'entité du type d'entité `Publisher` lorsque vous définissez une contrainte d'intégrité référentielle sur l'association `PublishedBy`.  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant définit une contrainte d'intégrité référentielle sur l'association `PublishedBy` présentée dans le modèle conceptuel ci-dessus.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés du modèle de données Entity](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
