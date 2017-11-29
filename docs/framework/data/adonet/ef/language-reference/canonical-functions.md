---
title: Fonctions canoniques
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b80eeedc67678d703664eb705408a72b7e4a2274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="canonical-functions"></a>Fonctions canoniques
Cette section décrit les fonctions canoniques qui sont prises en charge par tous les fournisseurs de données et qui peuvent être utilisée par toutes les technologies de requête. Les fonctions canoniques ne peuvent pas être étendues par un fournisseur.  
  
 Ces fonctions canoniques seront traduites en fonctionnalités de source de données correspondantes pour le fournisseur. De ce fait, les appels de fonction peuvent être exprimés sous une forme commune dans toutes les sources de données.  
  
 Ces fonctions canoniques étant indépendantes des sources de données, les types d'arguments et de retour des fonctions canoniques sont définis par rapport aux types du modèle conceptuel. Toutefois, il est possible que certaines sources de données ne puissent pas prendre en charge tous les types du modèle conceptuel.  
  
 Lorsque des fonctions canoniques sont utilisées dans une requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)], la fonction appropriée est appelée au niveau de la source de données.  
  
 Le comportement en cas d'entrée null et les conditions d'erreurs sont explicitement spécifiées pour toutes les fonctions canoniques. Les fournisseurs de magasins doivent respecter ce comportement, mais [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ne l'applique pas de force.  
  
 Pour les scénarios LINQ, les requêtes sur le [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] impliquent le mappage de méthodes CLR aux méthodes dans la source de données sous-jacente. Les méthodes CLR sont mappées aux fonctions canoniques, ce qui garantit qu'un ensemble spécifique de méthodes sera correctement mappé, quelle que soit la source de données.  
  
## <a name="canonical-functions-namespace"></a>Espace de noms des fonctions canoniques  
 L'espace de noms des fonctions canoniques est <xref:System.Data.Metadata.Edm>. L'espace de noms <xref:System.Data.Metadata.Edm> est automatiquement inclus dans toutes les requêtes. Toutefois, si un autre espace de noms est importé et que celui-ci contient une fonction de même nom qu'une fonction canonique (dans l'espace de noms <xref:System.Data.Metadata.Edm>), vous devez spécifier l'espace de noms.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Fonctions canoniques d’agrégation](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 Décrit les fonctions canoniques d'agrégation [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 [Fonctions canoniques mathématiques](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 Décrit les fonctions canoniques mathématiques [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 [Fonctions canoniques de chaîne](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 Décrit les fonctions canoniques de chaîne [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 [Fonctions canoniques de date et d’heure](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 Décrit les fonctions canoniques de date et d'heure [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 [Au niveau du bit des fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 Décrit les fonctions canoniques au niveau du bit [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 [Fonctions spatiales](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 Décrit les fonctions canoniques spatiales [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 [Les autres fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 Décrit les fonctions qui ne sont pas considérées comme des fonctions au niveau du bit, des fonctions de date/heure, des fonctions de chaîne, des fonctions mathématiques ni des fonctions d'agrégation.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Mappage des fonctions de modèle conceptuel canonique à SQL Server](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
 [Fonctions définies par l’utilisateur](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
