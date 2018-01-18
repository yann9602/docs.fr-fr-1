---
title: "Propriété de clé étrangère"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 044be77cbbd8b5ad16cfbd5bbf1fdde984a060d5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="foreign-key-property"></a>Propriété de clé étrangère
A *propriété de clé étrangère* dans le modèle EDM (Entity Data Model) est un type primitif [propriété](../../../../docs/framework/data/adonet/property.md) (ou un ensemble de propriétés de type primitif) sur un [type d’entité](../../../../docs/framework/data/adonet/entity-type.md) qui contient le [clé d’entité](../../../../docs/framework/data/adonet/entity-key.md) d’un autre type d’entité.  
  
 Une propriété de clé étrangère est analogue à une colonne clé étrangère dans une base de données relationnelle. De la même façon que les colonnes clés étrangères sont utilisés dans une base de données relationnelle pour créer des relations entre les lignes des tables, des propriétés de clé étrangère dans un modèle conceptuel sont utilisées pour établir [associations](../../../../docs/framework/data/adonet/association-type.md) entre types d’entité. A [contrainte d’intégrité référentielle](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) est utilisé pour définir une association entre deux types d’entité lorsqu’un des types possède une propriété de clé étrangère.  
  
## <a name="example"></a>Exemple  
 Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`. Le type d'entité `Book` a une propriété, `PublisherId`, qui référence la clé d'entité du type d'entité `Publisher` lorsque vous définissez une contrainte d'intégrité référentielle sur l'association `PublishedBy`.  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant utilise la propriété de clé étrangère `PublisherId` pour définir une contrainte d'intégrité référentielle sur l'association `PublishedBy` présentée dans le modèle conceptuel ci-dessus.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés d’Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
