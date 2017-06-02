---
title: "Concepts cl&#233;s d&#39;Entity Data Model | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Concepts cl&#233;s d&#39;Entity Data Model
Le modèle EDM \(Entity Data Model\) utilise trois concepts clés pour décrire la structure des données : le *type d'entité*, le *type d'association* et la *propriété*.  Il s'agit des concepts les plus importants pour décrire la structure des données dans n'importe quelle implémentation du modèle EDM.  
  
## Type d'entité  
 Le [type d'entité](../../../../docs/framework/data/adonet/entity-type.md) est le bloc de construction fondamental pour la description de la structure des données avec le modèle EDM.  Dans un modèle conceptuel, les types d'entité sont construits à partir de [propriétés](../../../../docs/framework/data/adonet/property.md) et décrivent la structure des concepts de niveau supérieur, comme les clients et les commandes dans une application de gestion.  De la même manière qu'une définition de classe dans un logiciel est un modèle pour les instances de la classe, un type d'entité est un modèle pour les entités.  Une entité représente un objet spécifique \(tel qu'un client ou une commande spécifique\).  Chaque entité doit avoir une [clé d'entité](../../../../docs/framework/data/adonet/entity-key.md) unique dans un [jeu d'entités](../../../../docs/framework/data/adonet/entity-set.md).  Un jeu d'entités est une collection d'instances d'un type d'entité spécifique.  Les jeux d'entités \(et les [ensembles d'associations](../../../../docs/framework/data/adonet/association-set.md)\) sont regroupés logiquement dans un [conteneur d'entités](../../../../docs/framework/data/adonet/entity-container.md).  
  
 Les types d'entité prennent en charge l'héritage ; autrement dit, un type d'entité peut être dérivé d'un autre.  Pour plus d'informations, consultez [Entity Data Model : héritage](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).  
  
## Type d'association  
 Un [type d'association](../../../../docs/framework/data/adonet/association-type.md) \(ou association\) est le bloc de construction fondamental pour la description des relations dans le modèle EDM.  Dans un modèle conceptuel, une association représente une relation entre deux types d'entité \(tels que Customer et Order\).  Chaque association possède deux [terminaisons d'association](../../../../docs/framework/data/adonet/association-end.md) qui spécifient les types d'entité impliqués dans l'association.  Chaque terminaison d'association spécifie également une [multiplicité de terminaison d'association](../../../../docs/framework/data/adonet/association-end-multiplicity.md) qui indique le nombre d'entités pouvant figurer à cette terminaison de l'association.  La multiplicité de terminaison d'association peut avoir une valeur égale à un \(1\), zéro ou un \(0..1\), ou plusieurs \(\*\).  Il est possible d'accéder aux entités au niveau de la terminaison d'une association via les [propriétés de navigation](../../../../docs/framework/data/adonet/navigation-property.md) ou via les clés étrangères si elles sont exposées sur un type d'entité.  Pour plus d'informations, consultez [propriété de clé étrangère](../../../../docs/framework/data/adonet/foreign-key-property.md).  
  
 Dans une application, une instance d'une association représente une association spécifique \(par exemple une association entre une instance de Customer et des instances d'Order\).  Les instances d'association sont regroupées logiquement dans un [ensemble d'associations](../../../../docs/framework/data/adonet/association-set.md).  Les ensembles d'associations \(et les [jeux d'entités](../../../../docs/framework/data/adonet/entity-set.md)\) sont regroupés logiquement dans un [conteneur d'entités](../../../../docs/framework/data/adonet/entity-container.md).  
  
## Propriété  
 Les [types d'entité](../../../../docs/framework/data/adonet/entity-type.md) contiennent des [propriétés](../../../../docs/framework/data/adonet/property.md) qui définissent leur structure et leurs caractéristiques.  Par exemple, un type d'entité Customer peut avoir des propriétés telles que CustomerId, Name et Address.  
  
 Les propriétés dans un modèle conceptuel sont analogues à celles définies sur une classe dans un logiciel.  De même que les propriétés sur une classe définissent la forme de la classe et acheminent des informations sur les objets, les propriétés dans un modèle conceptuel définissent la forme d'un type d'entité et acheminent des informations sur les instances de type d'entité.  
  
 Une propriété peut contenir des données de type primitif \(comme une chaîne, un entier ou une valeur booléenne\) ou des données structurées \(comme un type complexe\).  Pour plus d'informations, consultez [Entity Data Model : types de données primitifs](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).  
  
## Représentations d'un modèle conceptuel  
 Un *modèle conceptuel* est une représentation spécifique de la structure de certaines données sous la forme d'entités et de relations.  Un diagramme est une façon de représenter un modèle conceptuel.  Le diagramme suivant représente un modèle conceptuel avec trois types d'entité \(`Book`, `Publisher` et `Author`\) et deux associations \(`PublishedBy` et `WrittenBy`\) :  
  
 ![Modèle avec propriétés de navigation](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 Toutefois, cette représentation présente des défauts en matière de transmission de détails sur le modèle.  Par exemple, les informations sur le type de propriété et le jeu d'entités ne sont pas représentées sur le diagramme.  La richesse d'un modèle conceptuel peut être transmise plus clairement dans un langage spécifique à un domaine \(DSL\).  [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage DSL basé sur XML appelé [CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) \(*Conceptual Schema Definition Language*\) pour définir des modèles conceptuels.  Voici la définition CSDL du modèle conceptuel dans le diagramme ci\-dessus :  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## Voir aussi  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)