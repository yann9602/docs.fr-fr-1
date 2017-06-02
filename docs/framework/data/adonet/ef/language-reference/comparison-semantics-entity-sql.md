---
title: "S&#233;mantique de comparaison (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# S&#233;mantique de comparaison (Entity SQL)
L'exécution des opérateurs [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivants implique une comparaison d'instances de type :  
  
## Comparaison explicite  
 Opérations d'égalité :  
  
-   \=  
  
-   \!\=  
  
 Opérations de classement :  
  
-   \<  
  
-   \<\=  
  
-   \>  
  
-   \>\=  
  
 Opérations relatives à la possibilité de valeurs NULL :  
  
-   IS NULL  
  
-   IS NOT NULL  
  
## Distinction explicite  
 Distinction d'égalité :  
  
-   DISTINCT  
  
-   GROUP BY  
  
 Distinction de classement :  
  
-   ORDER BY  
  
## Distinction implicite  
 Opérations et prédicats de définition \(égalité\) :  
  
-   UNION  
  
-   INTERSECT  
  
-   EXCEPT  
  
-   SET  
  
-   OVERLAPS  
  
 Prédicats d'élément \(égalité\) :  
  
-   IN  
  
## Combinaisons prises en charge  
 Le tableau suivant répertorie toutes les combinaisons prises en charge des opérateurs de comparaison pour chaque type :  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|**Type**|**\=**<br /><br /> **\!\=**|**GROUP BY**<br /><br /> **DISTINCT**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**\<   \<\=**<br /><br /> **\>   \>\=**|**ORDER BY**|**IS NULL**<br /><br /> **IS NOT NULL**|  
|Type d'entité|Ref<sup>1</sup>|Toutes les propriétés<sup>2</sup>|Toutes les propriétés<sup>2</sup>|Toutes les propriétés<sup>2</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|Ref<sup>1</sup>|  
|Type complexe|Levée<sup>3</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|  
|Ligne|Toutes les propriétés<sup>4</sup>|Toutes les propriétés<sup>4</sup>|Toutes les propriétés<sup>4</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|Toutes les propriétés<sup>4</sup>|Levée<sup>3</sup>|  
|Type primitif|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|Spécifique au fournisseur|  
|Multiset|Levée<sup>3</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|  
|Ref|Oui <sup>5</sup>|Oui <sup>5</sup>|Oui <sup>5</sup>|Oui <sup>5</sup>|Throw|Throw|Oui <sup>5</sup>|  
|Association<br /><br /> type|Levée<sup>3</sup>|Throw|Throw|Throw|Levée<sup>3</sup>|Levée<sup>3</sup>|Levée<sup>3</sup>|  
  
 <sup>1</sup>Les références des instances de type d'entité données sont comparées implicitement, comme l'illustre l'exemple suivant :  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 Une instance d'entité ne peut pas être comparée à une référence explicite.  Lors d'une telle tentative, une exception est levée.  Par exemple, la requête suivante lève une exception :  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>Les propriétés de types complexes sont aplanies avant d'être envoyées au magasin, afin de pouvoir être comparées \(tant que toutes leurs propriétés peuvent être comparées\).  Voir aussi <sup>4</sup>.  
  
 <sup>3</sup>L'exécution d'Entity Framework détecte le cas non pris en charge et lève une exception explicite sans engager le fournisseur\/magasin.  
  
 <sup>4</sup>Une tentative est faite pour comparer toutes les propriétés.  Si une propriété est d'un type non comparable, tel que text, ntext ou image, une exception de serveur peut être levée.  
  
 <sup>5</sup>Tous les éléments individuels des références sont comparés \(cela inclut le nom du jeu d'entités et toutes les propriétés clés du type d'entité\).  
  
## Voir aussi  
 [Vue d'ensemble d'Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)