---
title: type complexe
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 389a3be7342005e424c89ff4e430b4a257f2da5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="complex-type"></a>type complexe
A *type complexe* est un modèle pour définir des propriétés riches et structurées sur [types d’entités](../../../../docs/framework/data/adonet/entity-type.md) ou d’autres types complexes. Chaque modèle contient les informations suivantes :  
  
-   Nom unique. (Requis)  
  
    > [!NOTE]
    >  Le nom d'un type complexe ne peut pas être le même qu'un nom de type d'entité dans le même espace de noms.  
  
-   Données sous la forme d’un ou plusieurs [propriétés](../../../../docs/framework/data/adonet/property.md). (Facultatif)  
  
    > [!NOTE]
    >  Une propriété d'un type complexe peut être un autre type complexe.  
  
 Un type complexe est semblable à un type d'entité en ce sens qu'il peut acheminer une charge utile de données sous la forme de propriétés de type primitif ou d'autres types complexes. Toutefois, il existe des différences clés entre les types complexes et les types d'entités :  
  
-   Les types complexes n'ont pas d'identité et, par conséquent, ne peuvent pas exister indépendamment. Les types complexes peuvent uniquement exister en tant que propriétés sur des types d'entités ou d'autres types complexes.  
  
-   Les types complexes ne peuvent pas participer [associations](../../../../docs/framework/data/adonet/association-type.md). Aucune terminaison d’association peut être un type complexe et par conséquent [propriétés de navigation](../../../../docs/framework/data/adonet/navigation-property.md) ne peut pas être définie sur des types complexes.  
  
## <a name="example"></a>Exemple  
 Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant définit un type complexe, Address, avec les propriétés de type primitif `StreetAddress`, `City`, `StateOrProvince`, `Country` et `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Pour définir le type complexe `Address` (ci-dessus) en tant que propriété sur un type d'entité, vous devez déclarer le type de propriété dans la définition de type d'entité. Le CSDL suivant déclare la propriété `Address` en tant que type complexe sur un type d'entité (Publisher) :  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés du modèle de données Entity](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
