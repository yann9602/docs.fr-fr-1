---
title: terminaison d'association
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ffa768f50b3a80c22b4c84cffaf42897193a7d9f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="association-end"></a>terminaison d'association
Un *end d’association* identifie les [type d’entité](../../../../docs/framework/data/adonet/entity-type.md) à une extrémité d’une [association](../../../../docs/framework/data/adonet/association-type.md) et le numéro d’entité de type des instances qui peuvent exister à cette fin d’une association. Les terminaisons d'association sont définies dans le cadre d'une association ; une association doit avoir exactement deux terminaisons d'association. [Propriétés de navigation](../../../../docs/framework/data/adonet/navigation-property.md) permettent de naviguer à partir d’une terminaison d’association à l’autre.  
  
 Une définition de terminaison d'association contient les informations suivantes :  
  
-   Un des types d'entité impliqués dans l'association. (Requis)  
  
    > [!NOTE]
    >  Pour une association donnée, le type d'entité spécifié pour chaque terminaison d'association peut être le même. Ceci crée une association automatique.  
  
-   Un [multiplicité de terminaison d’association](../../../../docs/framework/data/adonet/association-end-multiplicity.md) qui indique le nombre d’instances de type d’entité qui peuvent être à l’extrémité de l’association. La multiplicité de terminaison d'association peut avoir une valeur égale à un (1), zéro ou un (0..1), ou plusieurs (*).  
  
-   Nom de la terminaison de l'association. (facultatif)  
  
-   Informations sur les opérations effectuées sur la terminaison d'association, telles que CASCADE sur DELETE. (facultatif)  
  
## <a name="example"></a>Exemple  
 Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`. Les terminaisons d'association pour l'association `PublishedBy` sont les types d'entité `Book` et `Publisher`. La multiplicité de la terminaison `Publisher` est un (1) et celle de la terminaison `Book` est plusieurs (*), ce qui indique qu'un éditeur publie de nombreux livres et qu'un livre est publié par un seul éditeur.  
  
 ![Exemple de modèle](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant définit l'association `PublishedBy` présentée dans le diagramme ci-dessus. Notez que le type, le nom et la multiplicité de chaque terminaison d'association sont spécifiés par des attributs XML (`Type`, `Role` et `Multiplicity`, respectivement). Des informations facultatives sur les opérations effectuées sur une terminaison sont spécifiées dans un élément XML (`OnDelete`). Dans ce cas, si un éditeur est supprimé, tous les livres associés le sont aussi.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés d’Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
