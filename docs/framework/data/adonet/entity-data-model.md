---
title: Entity Data Model
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 69b72a824e6f9468c9b3d86073243d506382e766
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-data-model"></a>Entity Data Model
Le modèle EDM (Entity Data Model) est un jeu de concepts qui décrivent la structure des données, indépendamment de la forme sous laquelle elles sont stockées. Inspiré du modèle entité-relation décrit par Peter Chen en 1976, le modèle EDM le complète et étend ses utilisations traditionnelles.  
  
 Le modèle EDM aborde les difficultés qui se présentent lors du stockage de données sous plusieurs formes. Par exemple, prenons une entreprise qui stocke des données dans des bases de données relationnelles, des fichiers texte, des fichiers XML, des feuilles de calcul et des rapports. Cette diversité pose des problèmes importants en termes de modélisation des données, de conception d'application et d'accès aux données. Lors de la conception d'une application orientée données, l'écriture de code efficace et gérable sans nuire à l'efficacité de l'accès aux données, du stockage et de l'évolutivité relève du défi. Lorsque les données ont une structure relationnelle, l'accès aux données, le stockage et l'évolutivité sont très efficaces, mais l'écriture de code efficace et gérable devient plus difficile. Lorsque les données ont une structure objet, la tendance est inversée : l'écriture de code efficace et gérable vient au détriment de l'efficacité de l'accès aux données, du stockage et de l'évolutivité. Même s'il est possible de trouver un juste équilibre entre ces deux aspects, de nouvelles difficultés se présentent lorsque des données passent d'une forme à une autre. Le modèle Entity Data Model aborde ces difficultés en décrivant la structure des données en termes d'entités et de relations qui sont indépendantes de tout schéma de stockage. La forme sous laquelle les données sont stockées n'a alors plus aucune incidence sur la conception et le développement de l'application. Par ailleurs, comme les entités et les relations décrivent la structure des données telles qu'elles sont utilisées dans une application (et non la forme sous laquelle elles sont stockées), elles peuvent évoluer parallèlement à une application.  
  
 Un `conceptual model` est une représentation spécifique de la structure des données sous forme d'entités et de relations. Il est en général défini dans un langage spécifique à un domaine (DSL) qui implémente les concepts du modèle EDM. [Langage de définition de schéma conceptuel (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) est un exemple d’un langage spécifique à un domaine. Les entités et les relations décrites dans un modèle conceptuel peuvent être considérées comme des abstractions d'objets et d'associations dans une application. Cela permet aux développeurs de se concentrer sur le modèle conceptuel sans se soucier du schéma de stockage, et d'écrire du code en favorisant son efficacité et sa maintenabilité. Pendant ce temps, les concepteurs de schémas de stockage peuvent se concentrer sur l'efficacité de l'accès aux données, du stockage et de l'évolutivité.  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques de cette section décrivent les concepts du modèle EDM. Tout langage DSL qui implémente le modèle EDM doit inclure les concepts décrits ici. Notez que la [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise le langage CSDL pour définir des modèles conceptuels. Pour plus d’informations, consultez [spécification CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).  
  
 [Concepts clés du modèle de données Entity](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [Entity Data Model : espaces de noms](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [Entity Data Model : Types de données primitifs](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [Entity Data Model : héritage](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [terminaison d’association](../../../../docs/framework/data/adonet/association-end.md)  
  
 [multiplicité de terminaison d’association](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [ensemble d’associations](../../../../docs/framework/data/adonet/association-set.md)  
  
 [ensemble d’associations](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [type d’association](../../../../docs/framework/data/adonet/association-type.md)  
  
 [type complexe](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [conteneur d’entités](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [clé d’entité](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [jeu d’entités](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [type d’entité](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [facet](../../../../docs/framework/data/adonet/facet.md)  
  
 [propriété de clé étrangère](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [fonction déclarée par modèle](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [fonction définie par modèle](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [propriété de navigation](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [propriété](../../../../docs/framework/data/adonet/property.md)  
  
 [contrainte d’intégrité référentielle](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Outils ADO.NET Entity Data Model](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [vue d’ensemble du fichier .edmx](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Spécification CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
