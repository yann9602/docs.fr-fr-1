---
title: "orderby, clause (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- orderby
- orderby_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ec9507e4c1d9691d90d47cdbb20fdb22fc281d24
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="orderby-clause-c-reference"></a>orderby, clause (Référence C#)
Dans une expression de requête, la clause `orderby` a pour effet de trier la séquence ou la sous-séquence (groupe) retournée par ordre croissant ou décroissant. Il est possible de spécifier plusieurs clés de façon à effectuer une ou plusieurs opérations de tri secondaire. Le tri est effectué par le comparateur par défaut du type de l’élément. L'ordre de tri par défaut est le tri croissant. Vous pouvez aussi spécifier un comparateur personnalisé. Cependant, sa disponibilité est soumise à l’utilisation d’une syntaxe fondée sur une méthode. Pour plus d’informations, consultez [Tri des données](http://msdn.microsoft.com/library/6d76e2d7-b418-49b5-ac78-2bcd61169c48).  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la première requête trie les mots par ordre alphabétique à partir de A, tandis que la deuxième requête trie les mêmes mots par ordre décroissant. (Le mot clé `ascending` est la valeur de tri par défaut et peut être omis.)  
  
 [!code-cs[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant effectue un tri principal sur les noms des étudiants, puis un tri secondaire sur leurs prénoms.  
  
 [!code-cs[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]  
  
## <a name="remarks"></a>Remarques  
 Au moment de la compilation, la clause `orderby` est traduite en appel à la méthode <xref:System.Linq.Enumerable.OrderBy%2A>. Les différentes clés présentes dans la clause `orderby` sont traduites en appels à la méthode <xref:System.Linq.Enumerable.ThenBy%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Mots clés de requête (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [group, clause](../../../csharp/language-reference/keywords/group-clause.md)   
 [Bien démarrer avec LINQ en C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

