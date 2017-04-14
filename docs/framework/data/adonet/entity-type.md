---
title: "type d&#39;entit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# type d&#39;entit&#233;
Le *type d'entité* est le bloc de construction fondamental pour la description de la structure des données avec le modèle EDM \(Entity Data Model\).  Dans un modèle conceptuel, un type d'entité représente la structure des concepts de niveau supérieur, comme les clients ou les commandes.  Un type d'entité est un modèle pour les instances de type d'entité.  Chaque modèle contient les informations suivantes :  
  
-   Nom unique.  \(Obligatoire.\)  
  
-   [Clé d'entité](../../../../docs/framework/data/adonet/entity-key.md) définie par une ou plusieurs propriétés.  \(Obligatoire.\)  
  
-   Données sous la forme de [propriétés](../../../../docs/framework/data/adonet/property.md).  \(Facultatif\)  
  
-   [Propriétés de navigation](../../../../docs/framework/data/adonet/navigation-property.md), qui permettent de naviguer d'une [terminaison](../../../../docs/framework/data/adonet/association-end.md) d'une [association](../../../../docs/framework/data/adonet/association-type.md) à l'autre terminaison.  \(facultatif\)  
  
 Dans une application, une instance d'un type d'entité représente un objet spécifique \(tel qu'un client ou une commande spécifique\).  Chaque instance d'un type d'entité doit avoir une [clé d'entité](../../../../docs/framework/data/adonet/entity-key.md) unique dans un [jeu d'entités](../../../../docs/framework/data/adonet/entity-set.md).  
  
 Deux instances de type d'entité sont considérées égales seulement si elles sont du même type et si les valeurs de leurs clés d'entité sont identiques.  
  
## Exemple  
 Le diagramme suivant montre un modèle conceptuel avec trois types d'entité : `Book`, `Publisher` et `Author`.  
  
 ![Exemple de modèle](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 Notez que les propriétés de chaque type d'entité qui composent sa clé d'entité sont signalées par « \(Key\) ».  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine \(DSL\), appelé [CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) \(Conceptual Schema Definition Language\), pour définir des modèles conceptuels.  Le CSDL suivant définit le type d'entité `Book` présenté dans le diagramme ci\-dessus :  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## Voir aussi  
 [Concepts clés d'Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)   
 [facette](../../../../docs/framework/data/adonet/facet.md)