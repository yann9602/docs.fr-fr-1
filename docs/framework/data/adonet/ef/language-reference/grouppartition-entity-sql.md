---
title: GROUPPARTITION (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8807564cb9acf8c50aed43ee11441ebdfbbcea78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (Entity SQL)
Retourne une collection de valeurs d'argument projetées en dehors de la partition de groupe actuelle à laquelle l'agrégat est associé. L'agrégat `GroupPartition` est un agrégat basé sur les groupes et n'a aucune forme basée sur les collections.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="remarks"></a>Notes  
 La requête suivante produit une liste de produits et une collection de quantités de ligne de commande pour chaque produit :  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 Les deux requêtes suivantes sont sémantiquement égales :  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 L'opérateur `GROUPPARTITION` peut être utilisé conjointement à des fonctions d'agrégation définies par l'utilisateur.  
  
 `GROUPPARTITION` est un opérateur d'agrégation spécial qui maintient une référence au jeu de données d'entrée groupé. Cette référence peut être utilisée n'importe où dans la requête où GROUP BY est dans la portée. Par exemple :  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Avec un GROUP BY régulier, les résultats du regroupement sont masqués. Vous pouvez utiliser les résultats uniquement dans une fonction d'agrégation. Pour voir les résultats du regroupement, vous devez mettre en corrélation les résultats du regroupement et le jeu de données d'entrée à l'aide d'une sous-requête. Les deux requêtes suivantes sont équivalentes :  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Comme le montre l'exemple, l'opérateur d'agrégation GROUPPARTITION simplifie l'obtention d'une référence au jeu de données d'entrée après le regroupement.  
  
 L'opérateur GROUPPARTITION peut spécifier toute expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dans l'entrée de l'opérateur lorsque vous utilisez le paramètre `expression` .  
  
 Par exemple, toutes les expressions d'entrée suivantes de la partition de groupe sont valides :  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous montre comment utiliser la clause GROUPPARTITION avec la clause GROUP BY. La clause GROUP BY regroupe les entités `SalesOrderHeader` par leur élément `Contact`. La clause GROUPPARTITION projette alors la propriété `TotalDue` pour chaque groupe, ce qui génère une collection de valeurs décimales.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
