---
title: "Définitions de type (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b890a56daeab1c3a0fbb8c95ec29a81cb7689e9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="type-definitions-entity-sql"></a>Définitions de type (Entity SQL)
Une définition de type est utilisée dans l'instruction de déclaration d'une fonction incluse [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="remarks"></a>Remarques  
 L’instruction de déclaration pour une fonction inline se compose de la [fonction](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) mot clé suivi par l’identificateur représentant le nom de fonction (par exemple, « MyAvg ») suivi d’une liste de définition des paramètres entre parenthèses (pour exemple, « dues Collection(Decimal)").  
  
 La liste de définitions de paramètres est composée de zéro, une ou plusieurs définitions de paramètres. Chaque définition de paramètre se compose d'un identificateur (le nom du paramètre de la fonction, par exemple, « dues ») suivi d'une définition de type (par exemple, « Collection(Decimal) »).  
  
 Les définitions de type peuvent correspondre :  
  
-   au type de l'identificateur (par exemple, « Int32 » ou « AdventureWorks.Order ») ;  
  
-   au mot clé `COLLECTION` suivi par une autre définition de type entre parenthèses (par exemple, « Collection(AdventureWorks.Order) ») ;  
  
-   au mot clé ROW suivi par une liste de définitions de propriétés entre parenthèses (par exemple, « Ligne (x AdventureWorks.Order) »). Définitions de propriétés ont un format tel que «`identifier type_definition`, `identifier type_definition`,... ».  
  
-   au mot clé REF suivi par le type de l'identificateur entre parenthèses (par exemple, « Ref(AdventureWorks.Order) »). L'opérateur de définition de type REF a besoin d'un type d'entité comme argument. Vous ne pouvez pas spécifier un type primitif comme argument.  
  
 Vous pouvez également imbriquer des définitions de type (par exemple, « Collection(Row(x Ref(AdventureWorks.Order))) »).  
  
 Les options de définition de type sont :  
  
-   `IdentifierName supported_type` ou  
  
-   `IdentifierName` COLLECTION(`type_definition`) ou  
  
-   `IdentifierName` ROW(`property_definition`) ou  
  
-   `IdentifierName` REF(`supported_entity_type`).  
  
 L'option de définition de propriété est `IdentifierName type_definition`.  
  
 Les types pris en charge sont tous les types figurant dans l'espace de noms actuel. Ils incluent à la fois les types primitifs et les types d'entités.  
  
 Les types d'entités pris en charge font référence uniquement aux types d'entités dans l'espace de noms actuel. Ils n'incluent pas les types primitifs.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant correspond à une définition de type simple.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 L'exemple suivant correspond à une définition de type COLLECTION.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 L'exemple suivant correspond à une définition de type ROW.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 L'exemple suivant correspond à une définition de type REF.  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
