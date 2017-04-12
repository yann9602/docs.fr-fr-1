---
title: "Gérer des valeurs Null dans des expressions de requête"
description: "Comment gérer des valeurs Null dans des expressions de requête."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 14b64bf8d3590f4f7dc3d1b00cb50d0bc421d9bc
ms.lasthandoff: 03/13/2017

---
# <a name="handle-null-values-in-query-expressions"></a>Gérer des valeurs Null dans des expressions de requête

Cet exemple montre comment gérer d’éventuelles valeurs Null dans des collections sources. Une collection d’objets comme un <xref:System.Collections.Generic.IEnumerable%601> peut contenir des éléments dont la valeur est [null](../language-reference/keywords/null.md). Si une collection source est Null, ou contient un élément dont la valeur est Null, alors que votre requête ne gère pas les valeurs Null, une exception <xref:System.NullReferenceException> sera levée lorsque vous exécuterez la requête.  
  
## <a name="example"></a>Exemple

 Vous pouvez écrire du code en prévention pour éviter une exception de référence Null, comme indiqué dans l’exemple suivant :  
  
 [!code-cs[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 Dans l’exemple précédent, la clause `where` exclut tous les éléments Null de la séquence de catégories. Cette technique est indépendante de la vérification de valeur Null de la clause join. Dans cet exemple, l’expression conditionnelle avec une valeur Null fonctionne, car `Products.CategoryID` est de type `int?`, qui est le raccourci de `Nullable<int>`.  
  
## <a name="example"></a>Exemple

 Dans une clause join, si seulement l’une des clés de comparaison est un type valeur Nullable, vous pouvez caster l’autre clé en type Nullable dans l’expression de requête. Dans l’exemple suivant, supposons que `EmployeeID` soit une colonne qui contienne des valeurs de type `int?` :  
  
 [!code-cs[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Nullable%601>   
 [Expressions de requête LINQ](index.md)   
 [Types Nullable](../programming-guide/nullable-types/index.md)
