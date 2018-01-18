---
title: jeu d'associations
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fa977f69951184629f4e9555f524f074a09ce96a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="association-set"></a>jeu d'associations
Un *ensemble d’associations* est un conteneur logique pour [association](../../../../docs/framework/data/adonet/association-type.md) instances du même type. Un ensemble d'associations n'est pas une construction de modélisation des données ; autrement dit, il ne décrit ni la structure de données ni les relations. Au lieu de cela, un ensemble d'associations fournit une construction pour un environnement d'hébergement ou de stockage (tel que le Common Language Runtime ou une base de données SQL Server) pour regrouper des instances d'association afin qu'elles puissent être mappées à un magasin de données.  
  
 Un ensemble d’associations est défini dans un [conteneur d’entités](../../../../docs/framework/data/adonet/entity-container.md), qui est un regroupement logique de [jeux d’entités](../../../../docs/framework/data/adonet/entity-set.md) et ensembles d’associations.  
  
 Une définition d'ensemble d'associations contient les informations suivantes :  
  
-   Nom de l'ensemble d'associations. (Requis)  
  
-   Association dont l'ensemble d'associations contient des instances. (Requis)  
  
-   Deux [terminaisons d’ensemble d’associations](../../../../docs/framework/data/adonet/association-set-end.md).  
  
## <a name="example"></a>Exemple  
 Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`. Bien que les informations sur les ensembles d'associations ne soient pas transmises au diagramme, le diagramme suivant montre un exemple d'ensembles d'associations et de jeux d'entités basés sur ce modèle.  
  
 ![Exemple de modèle](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 L'exemple suivant montre un ensemble d'associations (`PublishedBy`) et deux jeux d'entités (`Books` et `Publishers`) basés sur le modèle conceptuel présenté ci-dessus. BI dans le `Books` jeu d’entités représente une instance de la `Book` type d’entité en cours d’exécution. De même, Pj représente un `Publisher` d’instance dans le `Publishers` jeu d’entités. BiPj représente une instance de la `PublishedBy` association dans le `PublishedBy` ensemble d’associations.  
  
 ![Définit l’exemple](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant définit un conteneur d'entités avec un ensemble d'associations pour chaque association dans le diagramme ci-dessus. Notez que le nom et l'association pour chaque ensemble d'associations sont définis à l'aide d'attributs XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 Il est possible de définir plusieurs ensembles d’associations par association, tant qu’aucune deux ensembles d’associations une [ensemble d’associations](../../../../docs/framework/data/adonet/association-set-end.md). Le CSDL suivant définit un conteneur d'entités avec deux ensembles d'associations pour l'association `WrittenBy`. Notez que plusieurs jeux d'entités ont été définis pour les types d'entité `Book` et `Author`, et qu'aucun ensemble d'associations ne partage une terminaison d'ensemble d'associations.  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts clés d’Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [propriété de clé étrangère](../../../../docs/framework/data/adonet/foreign-key-property.md)
