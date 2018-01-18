---
title: "Sémantique de comparaison (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c6d22b72e05e6293a7fd3bcf7ddfba6e116e441f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="comparison-semantics-entity-sql"></a>Sémantique de comparaison (Entity SQL)
L'exécution des opérateurs [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivants implique une comparaison d'instances de type :  
  
## <a name="explicit-comparison"></a>Comparaison explicite  
 Opérations d'égalité :  
  
-   =  
  
-   !=  
  
 Opérations de classement :  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 Opérations relatives à la possibilité de valeurs NULL :  
  
-   IS NULL  
  
-   IS NOT NULL  
  
## <a name="explicit-distinction"></a>Distinction explicite  
 Distinction d'égalité :  
  
-   DISTINCT  
  
-   GROUP BY  
  
 Distinction de classement :  
  
-   ORDER BY  
  
## <a name="implicit-distinction"></a>Distinction implicite  
 Opérations et prédicats de définition (égalité) :  
  
-   UNION  
  
-   INTERSECT  
  
-   EXCEPT  
  
-   SET  
  
-   OVERLAPS  
  
 Prédicats d'élément (égalité) :  
  
-   IN  
  
## <a name="supported-combinations"></a>Combinaisons prises en charge  
 Le tableau suivant répertorie toutes les combinaisons prises en charge des opérateurs de comparaison pour chaque type :  
  
|**Type**|**=**<br /><br /> **!=**|**GROUP BY**<br /><br /> **DISTINCT**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**<   <=**<br /><br /> **>   >=**|**ORDER BY**|**A LA VALEUR NULL**<br /><br /> **N’EST PAS NULL**|  
|-|-|-|-|-|-|-|-|  
|Type d'entité|Ref<sup>1</sup>|Toutes les propriétés<sup>2</sup>|Toutes les propriétés<sup>2</sup>|Toutes les propriétés<sup>2</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Ref<sup>1</sup>|  
|Type complexe|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|Ligne|Toutes les propriétés<sup>4</sup>|Toutes les propriétés<sup>4</sup>|Toutes les propriétés<sup>4</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Toutes les propriétés<sup>4</sup>|Throw<sup>3</sup>|  
|Type primitif|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|  
|Multiset|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
|Ref|Oui<sup>5</sup>|Oui<sup>5</sup>|Oui<sup>5</sup>|Oui<sup>5</sup>|Throw|Throw|Oui<sup>5</sup>|  
|Association<br /><br /> type|Throw<sup>3</sup>|Throw|Throw|Throw|Throw<sup>3</sup>|Throw<sup>3</sup>|Throw<sup>3</sup>|  
  
 <sup>1</sup>les références des instances du type d’entité donnée sont comparées implicitement, comme indiqué dans l’exemple suivant :  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Une instance d'entité ne peut pas être comparée à une référence explicite. Lors d'une telle tentative, une exception est levée. Par exemple, la requête suivante lève une exception :  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>propriétés de types complexes sont aplanies avant d’être envoyées au magasin, afin de pouvoir être comparées (tant que toutes leurs propriétés peuvent être comparées). Consultez également <sup>4.</sup>  
  
 <sup>3</sup>exécution d’Entity Framework détecte le cas non pris en charge et lève une exception explicite sans engager le fournisseur/magasin.  
  
 <sup>4</sup>une tentative est faite pour comparer toutes les propriétés. Si une propriété est d'un type non comparable, tel que text, ntext ou image, une exception de serveur peut être levée.  
  
 <sup>5</sup>tous les éléments individuels des références sont comparés (Cela inclut le nom de jeu d’entités et de toutes les propriétés de clé du type d’entité).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble d’Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
