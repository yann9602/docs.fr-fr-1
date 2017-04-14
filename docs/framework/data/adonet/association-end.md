---
title: "terminaison d&#39;association | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# terminaison d&#39;association
Une *terminaison d'association* identifie le [type d'entité](../../../../docs/framework/data/adonet/entity-type.md) sur une terminaison d'une [association](../../../../docs/framework/data/adonet/association-type.md) et le nombre d'instances de type d'entité pouvant exister à cette terminaison d'une association.  Les terminaisons d'association sont définies dans le cadre d'une association ; une association doit avoir exactement deux terminaisons d'association.  Les [propriétés de navigation](../../../../docs/framework/data/adonet/navigation-property.md) permettent la navigation d'une terminaison d'association à l'autre.  
  
 Une définition de terminaison d'association contient les informations suivantes :  
  
-   Un des types d'entité impliqués dans l'association.  \(Requis\)  
  
    > [!NOTE]
    >  Pour une association donnée, le type d'entité spécifié pour chaque terminaison d'association peut être le même.  Ceci crée une association automatique.  
  
-   [Multiplicité de terminaison d'association](../../../../docs/framework/data/adonet/association-end-multiplicity.md), qui indique le nombre d'instances de type d'entité pouvant figurer à une terminaison de l'association.  La multiplicité de terminaison d'association peut avoir une valeur égale à un \(1\), zéro ou un \(0..1\), ou plusieurs \(\*\).  
  
-   Nom de la terminaison de l'association.  \(facultatif\)  
  
-   Informations sur les opérations effectuées sur la terminaison d'association, telles que CASCADE sur DELETE.  \(facultatif\)  
  
## Exemple  
 Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`.  Les terminaisons d'association pour l'association `PublishedBy` sont les types d'entité `Book` et `Publisher`.  La multiplicité de la terminaison `Publisher` est un \(1\) et celle de la terminaison `Book` est plusieurs \(\*\), ce qui indique qu'un éditeur publie de nombreux livres et qu'un livre est publié par un seul éditeur.  
  
 ![Exemple de modèle](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework utilise un langage spécifique à un domaine \(DSL\), appelé [CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) \(Conceptual Schema Definition Language\), pour définir des modèles conceptuels.  Le CSDL suivant définit l'association `PublishedBy` présentée dans le diagramme ci\-dessus.  Notez que le type, le nom et la multiplicité de chaque terminaison d'association sont spécifiés par des attributs XML \(`Type`, `Role` et `Multiplicity`, respectivement\).  Des informations facultatives sur les opérations effectuées sur une terminaison sont spécifiées dans un élément XML \(`OnDelete`\).  Dans ce cas, si un éditeur est supprimé, tous les livres associés le sont aussi.  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## Voir aussi  
 [Concepts clés d'Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)