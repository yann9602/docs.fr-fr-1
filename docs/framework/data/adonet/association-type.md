---
title: type d'association
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5349889017ea23701a17a92947d9750610a52f59
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="association-type"></a>type d'association
Un *type d’association* (également appelé association) est le bloc de construction fondamental pour décrire les relations dans le modèle EDM (Entity Data Model). Dans un modèle conceptuel, une association représente une relation entre deux [types d’entités](../../../../docs/framework/data/adonet/entity-type.md) (tel que `Customer` et `Order`). Dans une application, une instance d'une association représente une association spécifique (comme une association entre une instance de `Customer` et une instance d'`Order`). Instances d’association sont regroupées logiquement dans un [ensemble d’associations](../../../../docs/framework/data/adonet/association-set.md).  
  
 Une définition d'association contient les informations suivantes :  
  
-   Nom unique. (Requis)  
  
-   Deux [terminaisons d’association](../../../../docs/framework/data/adonet/association-end.md), un pour chaque type d’entité dans la relation. (Requis)  
  
    > [!NOTE]
    >  Une association ne peut pas représenter de relation entre plus de deux types d'entité. Toutefois, une association peut définir une relation réciproque en spécifiant le même type d'entité pour chacune de ses terminaisons d'association.  
  
-   A [contrainte d’intégrité référentielle](../../../../docs/framework/data/adonet/referential-integrity-constraint.md). (facultatif)  
  
 Chaque terminaison d’association doit spécifier un [multiplicité de terminaison d’association](../../../../docs/framework/data/adonet/association-end-multiplicity.md) qui indique le nombre d’instances de type d’entité qui peuvent être à l’extrémité de l’association. La multiplicité de terminaison d'association peut avoir une valeur égale à un (1), zéro ou un (0..1), ou plusieurs (*). Instances de type d’entité à une extrémité d’une association est accessible via [propriétés de navigation](../../../../docs/framework/data/adonet/navigation-property.md) ou les clés étrangères si elles sont exposées sur un type d’entité. Pour plus d’informations, consultez [Entity Data Model : clés étrangères](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
## <a name="example"></a>Exemple  
 Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`. Les terminaisons d'association pour l'association `PublishedBy` sont les types d'entité `Book` et `Publisher`. La multiplicité de la terminaison `Publisher` est un (1) et celle de la terminaison `Book` est plusieurs (*), ce qui indique qu'un éditeur publie de nombreux livres et qu'un livre est publié par un seul éditeur.  
  
 ![Exemple de modèle](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant définit l'association `PublishedBy` présentée dans le diagramme ci-dessus :  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés d’Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
