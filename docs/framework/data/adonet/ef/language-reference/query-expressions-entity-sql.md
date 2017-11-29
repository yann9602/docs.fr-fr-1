---
title: "Expressions de requête (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8b30deea78efe275ccaf6beabafb16a84357ba26
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="query-expressions-entity-sql"></a>Expressions de requête (Entity SQL)
Une expression de requête combine un grand nombre d'opérateurs de requête différents dans une syntaxe unique. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]fournit différents types d’expressions, notamment les suivantes : [littéraux](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [paramètres](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [variables](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), opérateurs, [fonctions](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), les opérateurs de jeu et ainsi de suite. Pour plus d’informations, consultez [référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).  
  
## <a name="clauses"></a>Clauses  
 Une expression de requête est constituée d’une série de clauses qui appliquent des opérations successives à une collection d’objets. Elles sont basées sur les mêmes clauses contenues dans la norme d’une instruction SQL select : [sélectionnez](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [où](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [Avoir](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), et [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  
  
## <a name="scope"></a>Portée  
 Les noms définis dans la clause FROM sont introduits dans l'étendue FROM dans l'ordre de leur apparition, de gauche à droite. Dans la liste JOIN, les expressions peuvent faire référence aux noms définis précédemment dans la liste. Les propriétés publiques des éléments identifiés dans la clause FROM ne sont pas ajoutées à l'étendue FROM : elles doivent toujours être référencées par le biais du nom qualifié par un alias. Normalement, toutes les parties de l'expression select sont considérées comme faisant partie de l'étendue FROM.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
