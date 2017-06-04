---
title: "type complexe | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# type complexe
Un *type complexe* est un modèle permettant de définir des propriétés riches et structurées sur des [types d'entités](../../../../docs/framework/data/adonet/entity-type.md) ou d'autres types complexes.  Chaque modèle contient les informations suivantes :  
  
-   Nom unique.  \(Requis\)  
  
    > [!NOTE]
    >  Le nom d'un type complexe ne peut pas être le même qu'un nom de type d'entité dans le même espace de noms.  
  
-   Données sous la forme d'une ou plusieurs [propriétés](../../../../docs/framework/data/adonet/property.md).  \(Facultatif\)  
  
    > [!NOTE]
    >  Une propriété d'un type complexe peut être un autre type complexe.  
  
 Un type complexe est semblable à un type d'entité en ce sens qu'il peut acheminer une charge utile de données sous la forme de propriétés de type primitif ou d'autres types complexes.  Toutefois, il existe des différences clés entre les types complexes et les types d'entités :  
  
-   Les types complexes n'ont pas d'identité et, par conséquent, ne peuvent pas exister indépendamment.  Les types complexes peuvent uniquement exister en tant que propriétés sur des types d'entités ou d'autres types complexes.  
  
-   Les types complexes ne peuvent pas participer à des [associations](../../../../docs/framework/data/adonet/association-type.md).  Aucune terminaison d'une association ne peut être un type complexe ; par conséquent, les [propriétés de navigation](../../../../docs/framework/data/adonet/navigation-property.md) ne peuvent pas être définies sur des types complexes.  
  
## Exemple  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine \(DSL\), appelé [CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) \(Conceptual Schema Definition Language\), pour définir des modèles conceptuels.  Le CSDL suivant définit un type complexe, Address, avec les propriétés de type primitif `StreetAddress`, `City`, `StateOrProvince`, `Country` et `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Pour définir le type complexe `Address` \(ci\-dessus\) en tant que propriété sur un type d'entité, vous devez déclarer le type de propriété dans la définition de type d'entité.  Le CSDL suivant déclare la propriété `Address` en tant que type complexe sur un type d'entité \(Publisher\) :  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## Voir aussi  
 [Concepts clés d'Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)