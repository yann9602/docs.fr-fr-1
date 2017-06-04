---
title: "terminaison d&#39;ensemble d&#39;associations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# terminaison d&#39;ensemble d&#39;associations
Une *terminaison d'ensemble d'associations* identifie le [type d'entité](../../../../docs/framework/data/adonet/entity-type.md) et le [jeu d'entités](../../../../docs/framework/data/adonet/entity-set.md) au niveau de la terminaison d'un [ensemble d'associations](../../../../docs/framework/data/adonet/association-set.md).  Les terminaisons d'ensemble d'associations sont définies dans le cadre d'un ensemble d'associations ; un ensemble d'associations doit avoir exactement deux terminaisons d'ensemble d'associations.  
  
 Une définition de terminaison d'ensemble d'associations contient les informations suivantes :  
  
-   Un des types d'entité impliqués dans l'ensemble d'associations.  \(Requis\)  
  
-   Jeu d'entités pour le type d'entité impliqué dans l'ensemble d'associations.  \(Requis\)  
  
## Exemple  
 Le diagramme suivant montre un modèle conceptuel avec deux associations : `WrittenBy` et `PublishedBy`.  
  
 ![Exemple de modèle](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Le diagramme suivant montre un ensemble d'associations \(`PublishedBy`\) et deux jeux d'entités \(`Books` et `Publishers`\) selon le modèle conceptuel présenté ci\-dessus.  Les terminaisons d'ensemble d'associations sont les jeux d'entités `Books` et `Publishers`.  Bi dans le jeu d'entités `Books` représente une instance du type d'entité `Book` au moment de l'exécution.  De même, Pj représente une instance `Publisher` dans le jeu d'entités `Publishers`.  BiPj représente une instance de l'association `PublishedBy` dans l'ensemble d'associations `PublishedBy`.  
  
 ![Exemple de jeux d'entités](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage DSL, appelé [CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) \(Conceptual Schema Definition Language\), pour définir des modèles conceptuels.  Le CSDL suivant définit un conteneur d'entités avec un ensemble d'associations pour chaque association dans le diagramme ci\-dessus.  Notez que les terminaisons d'ensemble d'associations sont définies dans le cadre de chaque définition d'ensemble d'associations.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## Voir aussi  
 [Concepts clés d'Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)