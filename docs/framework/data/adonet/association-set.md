---
title: "ensemble d&#39;associations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ensemble d&#39;associations
Un *ensemble d'associations* est un conteneur logique pour les instances d'[association](../../../../docs/framework/data/adonet/association-type.md) du même type.  Un ensemble d'associations n'est pas une construction de modélisation des données ; autrement dit, il ne décrit ni la structure de données ni les relations.  Au lieu de cela, un ensemble d'associations fournit une construction pour un environnement d'hébergement ou de stockage \(tel que le Common Language Runtime ou une base de données SQL Server\) pour regrouper des instances d'association afin qu'elles puissent être mappées à un magasin de données.  
  
 Un ensemble d'associations est défini dans un [conteneur d'entités](../../../../docs/framework/data/adonet/entity-container.md), qui est un regroupement logique de [jeux d'entités](../../../../docs/framework/data/adonet/entity-set.md) et d'ensembles d'associations.  
  
 Une définition d'ensemble d'associations contient les informations suivantes :  
  
-   Nom de l'ensemble d'associations.  \(Requis\)  
  
-   Association dont l'ensemble d'associations contient des instances.  \(Requis\)  
  
-   Deux [terminaisons d'ensemble d'associations](../../../../docs/framework/data/adonet/association-set-end.md).  
  
## Exemple  
 Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`.  Bien que les informations sur les ensembles d'associations ne soient pas transmises au diagramme, le diagramme suivant montre un exemple d'ensembles d'associations et de jeux d'entités basés sur ce modèle.  
  
 ![Exemple de modèle](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 L'exemple suivant montre un ensemble d'associations \(`PublishedBy`\) et deux jeux d'entités \(`Books` et `Publishers`\) basés sur le modèle conceptuel présenté ci\-dessus.  Bi dans le jeu d'entités `Books` représente une instance du type d'entité `Book` au moment de l'exécution.  De même, Pj représente une instance `Publisher` dans le jeu d'entités `Publishers`.  BiPj représente une instance de l'association `PublishedBy` dans l'ensemble d'associations `PublishedBy`.  
  
 ![Exemple de jeux d'entités](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine \(DSL\), appelé [CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) \(Conceptual Schema Definition Language\), pour définir des modèles conceptuels.  Le CSDL suivant définit un conteneur d'entités avec un ensemble d'associations pour chaque association dans le diagramme ci\-dessus.  Notez que le nom et l'association pour chaque ensemble d'associations sont définis à l'aide d'attributs XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Il est possible de définir plusieurs ensembles d'associations par association, à condition qu'une [terminaison d'ensemble d'associations](../../../../docs/framework/data/adonet/association-set-end.md) ne soit pas partagée par deux ensembles d'associations.  Le CSDL suivant définit un conteneur d'entités avec deux ensembles d'associations pour l'association `WrittenBy`.  Notez que plusieurs jeux d'entités ont été définis pour les types d'entité `Author` et `Book`, et qu'aucun ensemble d'associations ne partage une terminaison d'ensemble d'associations.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## Voir aussi  
 [Concepts clés d'Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)   
 [propriété de clé étrangère](../../../../docs/framework/data/adonet/foreign-key-property.md)