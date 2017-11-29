---
title: "Exemples de requêtes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e7d7a0a1f641603887675ed0c1faebd5c06b273
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="query-examples"></a>Exemples de requêtes
Cette section fournit des exemples [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] et C# de requêtes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] standard. Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] peuvent rechercher de nombreux autres exemples dans un exemple de solution disponible dans la section Exemples. Pour plus d’informations, consultez [exemples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).  
  
> [!IMPORTANT]
>  *base de données* est souvent utilisée dans les exemples de code dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation. *base de données* est supposé pour être une instance d’un *Northwind* (classe), qui hérite de <xref:System.Data.Linq.DataContext>.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Requêtes d’agrégation](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 Explique comment utiliser <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, etc.  
  
 [Retourner le premier élément dans une séquence](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.First%2A>.  
  
 [Retourner ou ignorer des éléments dans une séquence](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Take%2A> et de <xref:System.Linq.Enumerable.Skip%2A>.  
  
 [Trier les éléments d’une séquence](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.OrderBy%2A>.  
  
 [Regrouper des éléments dans une séquence](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.GroupBy%2A>.  
  
 [Éliminer des éléments en double d’une séquence](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Distinct%2A>.  
  
 [Déterminer si certains ou tous les éléments d’une séquence satisfont à une Condition](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.All%2A> et de <xref:System.Linq.Enumerable.Any%2A>.  
  
 [Concaténer deux séquences](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Concat%2A>.  
  
 [Retourner la différence définie entre deux séquences](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Except%2A>.  
  
 [Retourner l’Intersection définie de deux séquences](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Intersect%2A>.  
  
 [Retourner l’Union définie de deux séquences](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.Union%2A>.  
  
 [Convertir une séquence en un tableau](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.ToArray%2A>.  
  
 [Convertir une séquence d’une liste générique](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.ToList%2A>.  
  
 [Convertir un Type en IEnumerable générique](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 Fournit des exemples d'utilisation de <xref:System.Linq.Enumerable.AsEnumerable%2A>.  
  
 [Formuler des jointures et des requêtes entre les produits](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 Fournit des exemples d'utilisation de la navigation de clé étrangère dans les clauses `from`, `where` et `select`.  
  
 [Formuler des Projections](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 Fournit des exemples de combinaison `select` avec d’autres fonctionnalités (par exemple, *types anonymes*) pour former des projections de requête.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Vue d’ensemble des opérateurs de requête standard](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 Explique le concept d'opérateurs de requête standard.  
  
 [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 Explique comment [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilise des concepts qui s'appliquent aux requêtes.  
  
 [Guide de programmation](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 Fournit un portail vers des rubriques qui expliquent des concepts de programmation en rapport avec [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].
