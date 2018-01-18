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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 09d4d1e6d2e69d805c316f60e6d6e91d094e68cb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="66771-102">GROUPPARTITION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="66771-102">GROUPPARTITION (Entity SQL)</span></span>
<span data-ttu-id="66771-103">Retourne une collection de valeurs d'argument projetées en dehors de la partition de groupe actuelle à laquelle l'agrégat est associé.</span><span class="sxs-lookup"><span data-stu-id="66771-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="66771-104">L'agrégat `GroupPartition` est un agrégat basé sur les groupes et n'a aucune forme basée sur les collections.</span><span class="sxs-lookup"><span data-stu-id="66771-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66771-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66771-105">Syntax</span></span>  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="66771-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="66771-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="66771-107">Toute expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="66771-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66771-108">Notes</span><span class="sxs-lookup"><span data-stu-id="66771-108">Remarks</span></span>  
 <span data-ttu-id="66771-109">La requête suivante produit une liste de produits et une collection de quantités de ligne de commande pour chaque produit :</span><span class="sxs-lookup"><span data-stu-id="66771-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="66771-110">Les deux requêtes suivantes sont sémantiquement égales :</span><span class="sxs-lookup"><span data-stu-id="66771-110">The following two queries are semantically equal:</span></span>  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="66771-111">L'opérateur `GROUPPARTITION` peut être utilisé conjointement à des fonctions d'agrégation définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="66771-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
 <span data-ttu-id="66771-112">`GROUPPARTITION` est un opérateur d'agrégation spécial qui maintient une référence au jeu de données d'entrée groupé.</span><span class="sxs-lookup"><span data-stu-id="66771-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="66771-113">Cette référence peut être utilisée n'importe où dans la requête où GROUP BY est dans la portée.</span><span class="sxs-lookup"><span data-stu-id="66771-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="66771-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="66771-114">For example,</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="66771-115">Avec un GROUP BY régulier, les résultats du regroupement sont masqués.</span><span class="sxs-lookup"><span data-stu-id="66771-115">With a regular GROUP BY, the results of the grouping are hidden.</span></span> <span data-ttu-id="66771-116">Vous pouvez utiliser les résultats uniquement dans une fonction d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="66771-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="66771-117">Pour voir les résultats du regroupement, vous devez mettre en corrélation les résultats du regroupement et le jeu de données d'entrée à l'aide d'une sous-requête.</span><span class="sxs-lookup"><span data-stu-id="66771-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="66771-118">Les deux requêtes suivantes sont équivalentes :</span><span class="sxs-lookup"><span data-stu-id="66771-118">The following two queries are equivalent:</span></span>  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="66771-119">Comme le montre l'exemple, l'opérateur d'agrégation GROUPPARTITION simplifie l'obtention d'une référence au jeu de données d'entrée après le regroupement.</span><span class="sxs-lookup"><span data-stu-id="66771-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="66771-120">L'opérateur GROUPPARTITION peut spécifier toute expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dans l'entrée de l'opérateur lorsque vous utilisez le paramètre `expression` .</span><span class="sxs-lookup"><span data-stu-id="66771-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="66771-121">Par exemple, toutes les expressions d'entrée suivantes de la partition de groupe sont valides :</span><span class="sxs-lookup"><span data-stu-id="66771-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="66771-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="66771-122">Example</span></span>  
 <span data-ttu-id="66771-123">L'exemple ci-dessous montre comment utiliser la clause GROUPPARTITION avec la clause GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="66771-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="66771-124">La clause GROUP BY regroupe les entités `SalesOrderHeader` par leur élément `Contact`.</span><span class="sxs-lookup"><span data-stu-id="66771-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="66771-125">La clause GROUPPARTITION projette alors la propriété `TotalDue` pour chaque groupe, ce qui génère une collection de valeurs décimales.</span><span class="sxs-lookup"><span data-stu-id="66771-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
