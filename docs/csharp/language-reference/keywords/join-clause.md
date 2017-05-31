---
title: "join, clause (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- join
- join_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
caps.latest.revision: 29
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 26027418b70d211dcadf6ace58b24927d94e427a
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017

---
# <a name="join-clause-c-reference"></a>join, clause (référence C#)
La clause `join` est utile pour associer des éléments de différentes séquences sources qui n’ont pas de relation directe dans le modèle objet. Le seul impératif est que les éléments de chaque source partagent une valeur dont l’égalité peut être comparée. Par exemple, un distributeur de produits alimentaires peut avoir une liste de fournisseurs d’un certain produit et une liste d’acheteurs. Une clause `join` peut être utilisée par exemple pour créer une liste des fournisseurs et des acheteurs de ce produit qui se trouvent tous dans la même région spécifiée.  
  
 Une clause `join` prend deux séquences sources comme entrée. Les éléments de chaque séquence doivent être ou contenir une propriété qui peut être comparée à une propriété correspondante dans l’autre séquence. La clause `join` utilise le mot clé spécial `equals` pour comparer les clés spécifiées et déterminer si elles sont égales. Toutes les jointures effectuées par la clause `join` sont des équijointures. La forme de la sortie d’une clause `join` dépend du type spécifique de jointure que vous effectuez. Les trois types de jointure les plus courants sont les suivants :  
  
-   Jointure interne  
  
-   Jointure groupée  
  
-   Jointure externe gauche  
  
## <a name="inner-join"></a>Jointure interne  
 L’exemple suivant montre une équijointure interne simple. Cette requête produit une séquence plate de paires « nom de produit / catégorie ». La même chaîne de catégorie apparaît dans plusieurs éléments. Si un élément de `categories` n’a pas de `products` correspondant, cette catégorie n’apparaît pas dans les résultats.  
  
 [!code-cs[cscsrefQueryKeywords#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_1.cs)]  
  
 Pour plus d’informations, consultez [Guide pratique pour effectuer des jointures internes](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md).  
  
## <a name="group-join"></a>Jointure groupée  
 Une clause `join` avec une expression `into` est appelée une jointure groupée.  
  
 [!code-cs[cscsrefQueryKeywords#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_2.cs)]  
  
 Une jointure groupée produit une séquence de résultats hiérarchique, qui associe des éléments de la séquence source de gauche à un ou plusieurs éléments correspondants de la séquence source de droite. Une jointure groupée n’a pas d’équivalent en termes relationnels ; il s’agit en fait d’une séquence de tableaux d’objets.  
  
 Si aucun élément de la séquence source de droite n’est trouvé en correspondance avec un élément de la source de gauche, la clause `join` produit un tableau vide pour cet élément. Par conséquent, la jointure groupée est fondamentalement une équijointure interne, excepté que la séquence de résultats est organisée en groupes.  
  
 Si vous sélectionnez les résultats d’une jointure groupée, vous pouvez accéder aux éléments, mais vous ne pouvez pas identifier leur clé de correspondance. Par conséquent, il est généralement plus utile de sélectionner les résultats de la jointure groupée dans un nouveau type qui a aussi le nom de clé, comme illustré dans l’exemple précédent.  
  
 Bien sûr, vous pouvez aussi utiliser le résultat d’une jointure groupée comme générateur d’une autre sous-requête :  
  
 [!code-cs[cscsrefQueryKeywords#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_3.cs)]  
  
 Pour plus d’informations, consultez [Guide pratique pour effectuer des jointures groupées](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md).  
  
## <a name="left-outer-join"></a>Jointure externe gauche  
 Dans une jointure externe gauche, tous les éléments de la séquence source de gauche sont retournés, même si aucun élément correspondant ne se trouve dans la séquence de droite. Pour effectuer une jointure externe gauche dans [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)], utilisez la méthode `DefaultIfEmpty` en combinaison avec une jointure groupée pour spécifier un élément du côté droit par défaut à créer si un élément de gauche n’a pas de correspondance. Vous pouvez utiliser `null` comme valeur par défaut pour tous les types référence ou vous pouvez spécifier un type par défaut défini par l’utilisateur. L’exemple suivant montre un type par défaut défini par l’utilisateur :  
  
 [!code-cs[cscsrefQueryKeywords#27](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_4.cs)]  
  
 Pour plus d’informations, consultez [Guide pratique pour effectuer des jointures externes gauches](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md).  
  
## <a name="the-equals-operator"></a>Opérateur Égal  
 Une clause `join` effectue une équijointure. En d’autres termes, vous pouvez baser les correspondances seulement sur l’égalité de deux clés. Les autres types de comparaisons, comme « supérieur à » ou « différent de », ne sont pas pris en charge. Pour indiquer clairement que toutes les jointures sont des équijointures, la clause `join` utilise le mot clé `equals` au lieu de l’opérateur `==`. Le mot clé `equals` peut être utilisé seulement dans une clause `join` et diffère de l’opérateur `==` sur un point important. Avec `equals`, la clé gauche consomme la séquence source externe et la clé droite consomme la source interne. La source externe est seulement dans l’étendue du côté gauche de `equals` et la séquence source interne est seulement dans l’étendue du côté droit.  
  
## <a name="non-equijoins"></a>Non-équijointures  
 Vous pouvez effectuer des non-équijointures, des jointures croisées et d’autres opérations de jointure personnalisées en utilisant plusieurs clauses `from` pour introduire indépendamment de nouvelles séquences dans une requête. Pour plus d’informations, consultez [Guide pratique pour effectuer des opérations de jointure personnalisées](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).  
  
## <a name="joins-on-object-collections-vs-relational-tables"></a>Jointures sur des collections d’objets et sur des tables relationnelles  
 Dans une expression de requête [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)], les opérations de jointure sont effectuées sur des collections d’objets. Les collections d’objets ne peuvent pas être « jointes » exactement de la même façon que deux tables relationnelles. Dans [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)], les clauses `join` explicites sont nécessaires seulement quand deux séquences sources ne sont pas liées par une relation. Quand vous travaillez avec [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq_md.md)], les tables avec des clés étrangères sont représentées dans le modèle objet en tant que propriétés de la table principale. Par exemple, dans la base de données Northwind, la table Customer a une relation de clé étrangère avec la table Orders. Quand vous mappez les tables au modèle objet, la classe Customer a une propriété Orders qui contient la collection de commandes associées à ce client. En réalité, la jointure a déjà été effectuée pour vous.  
  
 Pour plus d’informations sur l’interrogation de tables liées dans le contexte de [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq_md.md)], consultez [Procédure : mapper des relations de base de données](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
## <a name="composite-keys"></a>Clés composites  
 Vous pouvez tester l’égalité de plusieurs valeurs en utilisant une clé composite. Pour plus d’informations, consultez [Guide pratique pour effectuer des opérations de jointure à l’aide de clés composites](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md). Vous pouvez aussi utiliser des clés composites dans une clause `group`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant compare les résultats d’une jointure interne, d’une jointure groupée et d’une jointure externe gauche sur les mêmes sources de données en utilisant les mêmes clés de correspondance. Du code supplémentaire est ajouté à ces exemples pour clarifier les résultats dans l’affichage de la console.  
  
 [!code-cs[cscsrefQueryKeywords#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_5.cs)]  
  
## <a name="remarks"></a>Remarques  
 Une clause `join` qui n’est pas suivie de `into` se traduit par l’appel de la méthode <xref:System.Linq.Enumerable.Join%2A>. Une clause `join` qui n’est pas suivie de `into` se traduit par l’appel de la méthode <xref:System.Linq.Enumerable.GroupJoin%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés de requête (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Opérations de jointure](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)   
 [group, clause](../../../csharp/language-reference/keywords/group-clause.md)   
 [Guide pratique pour effectuer des jointures externes gauches](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [Guide pratique pour effectuer des jointures internes](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [Guide pratique pour effectuer des jointures groupées](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [Guide pratique pour classer les résultats d’une clause Join](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)   
 [Guide pratique pour effectuer des opérations de jointure à l’aide de clés composites](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)   
 [Guide pratique pour installer des exemples de bases de données](http://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)
