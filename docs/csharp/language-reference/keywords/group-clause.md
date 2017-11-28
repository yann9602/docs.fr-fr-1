---
title: "group, clause (Référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a2f67b2c90e1cced92d6fc7d47768b58bf155360
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="group-clause-c-reference"></a>group, clause (Référence C#)
La clause `group` retourne une séquence d’objets <xref:System.Linq.IGrouping%602> qui contient zéro, un ou plusieurs éléments qui correspondent à la valeur de clé du groupe. Par exemple, vous pouvez regrouper une séquence de chaînes en fonction de la première lettre de chaque chaîne. Dans ce cas, la première lettre est la clé, elle a le type [char](../../../csharp/language-reference/keywords/char.md) et elle est stockée dans la propriété `Key` de chaque objet <xref:System.Linq.IGrouping%602>. Le compilateur déduit le type de la clé.  
  
 Vous pouvez terminer une expression de requête avec une clause `group`, comme illustré dans l’exemple suivant :  
  
 [!code-csharp[cscsrefQueryKeywords#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_1.cs)]  
  
 Si vous souhaitez effectuer des opérations de requête supplémentaires sur chaque groupe, vous pouvez spécifier un identificateur temporaire en utilisant le mot clé contextuel [into](../../../csharp/language-reference/keywords/into.md). Quand vous utilisez `into`, vous devez continuer la requête et finalement la terminer avec une instruction `select` ou une autre clause `group`, comme illustré dans l’extrait suivant :  
  
 [!code-csharp[cscsrefQueryKeywords#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_2.cs)]  
  
 Des exemples d’utilisation plus complets de `group` avec et sans `into` sont fournis dans la section Exemple de cette rubrique.  
  
## <a name="enumerating-the-results-of-a-group-query"></a>Énumération des résultats d’une requête de groupe  
 Étant donné que les objets <xref:System.Linq.IGrouping%602> générés par une requête `group` sont essentiellement une liste de listes, vous devez utiliser une boucle [foreach](../../../csharp/language-reference/keywords/foreach-in.md) imbriquée pour accéder aux éléments dans chaque groupe. La boucle externe itère les clés de groupe, et la boucle interne itère chaque élément dans le groupe proprement dit. Un groupe peut avoir une clé mais pas d’éléments. Voici la boucle `foreach` qui exécute la requête dans les exemples de code précédents :  
  
 [!code-csharp[cscsrefQueryKeywords#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_3.cs)]  
  
## <a name="key-types"></a>Types de clés  
 Les clés de groupes peuvent être de tout type, comme une chaîne, un type numérique intégré, ou un type nommé ou un type anonyme défini par l’utilisateur.  
  
### <a name="grouping-by-string"></a>Regroupement par chaîne  
 Les exemples de code précédents utilisaient un `char`. On aurait facilement pu spécifier une clé de chaîne à la place, par exemple le nom de famille complet :  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_4.cs)]  
  
### <a name="grouping-by-bool"></a>Regroupement par valeur booléenne  
 L’exemple suivant illustre l’utilisation d’une valeur booléenne pour une clé afin de répartir les résultats en deux groupes. Notez que la valeur est générée par une sous-expression dans la clause `group`.  
  
 [!code-csharp[cscsrefQueryKeywords#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_5.cs)]  
  
### <a name="grouping-by-numeric-range"></a>Regroupement par plage numérique  
 L’exemple suivant utilise une expression pour créer des clés de groupes numériques qui représentent une plage de centiles. Notez l’utilisation de [let](../../../csharp/language-reference/keywords/let-clause.md) comme emplacement pratique pour stocker un résultat d’appel de méthode, qui vous évite d’avoir à appeler deux fois la méthode dans la clause `group`. Notez également que dans la clause `group`, pour éviter une exception « division par zéro », le code vérifie que l’étudiant n’a pas une moyenne égale à zéro. Pour plus d’informations sur la façon d’utiliser en toute sécurité des méthodes dans des expressions de requête, consultez [Guide pratique pour gérer des exceptions dans des expressions de requête](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).  
  
 [!code-csharp[cscsrefQueryKeywords#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_6.cs)]  
  
### <a name="grouping-by-composite-keys"></a>Regroupement par clés composites  
 Utilisez une clé composite quand vous souhaitez regrouper des éléments en fonction de plusieurs clés. Vous créez une clé composite en utilisant un type anonyme ou un type nommé pour contenir l’élément clé. Dans l’exemple suivant, supposons qu’une classe `Person` a été déclarée avec les membres nommés `surname` et `city`. La clause `group` provoque la création d’un groupe distinct pour chaque ensemble de personnes ayant le même nom de famille et la même ville.  
  
```csharp  
group person by new {name = person.surname, city = person.city};  
```  
  
 Utilisez un type nommé si vous devez passer la variable de requête à une autre méthode. Créez une classe spéciale à l’aide de propriétés implémentées automatiquement pour les clés, puis substituez les méthodes <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A>. Vous pouvez également utiliser un struct, auquel cas vous n’êtes pas obligé de substituer ces méthodes. Pour plus d’informations, consultez [Guide pratique pour implémenter une classe Lightweight avec des propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) et [Guide pratique pour interroger des fichiers dupliqués dans une arborescence de répertoires](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). Cette dernière rubrique contient un exemple de code qui illustre comment utiliser une clé composite avec un type nommé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre le modèle standard pour organiser des données sources en groupes quand aucune logique de requête supplémentaire n’est appliquée aux groupes. Il s’agit alors d’un regroupement sans continuation. Les éléments du tableau de chaînes sont regroupés en fonction de leur première lettre. Le résultat de la requête est un type <xref:System.Linq.IGrouping%602> contenant une propriété `Key` publique de type `char` et une collection <xref:System.Collections.Generic.IEnumerable%601> qui contient chaque élément du regroupement.  
  
 Le résultat d’une clause `group` est une séquence de séquences. Ainsi, pour accéder aux différents éléments de chaque groupe retourné, vous devez utiliser une boucle `foreach` imbriquée à l’intérieur de la boucle qui itère les clés de groupe, comme illustré dans l’exemple suivant.  
  
 [!code-csharp[cscsrefQueryKeywords#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_7.cs)]  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment exécuter une logique supplémentaire sur les groupes après les avoir créés, à l’aide une *continuation* avec `into`. Pour plus d’informations, consultez [into](../../../csharp/language-reference/keywords/into.md). L’exemple suivant interroge chaque groupe pour sélectionner uniquement ceux dont la valeur de clé est une voyelle.  
  
 [!code-csharp[cscsrefQueryKeywords#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_8.cs)]  
  
## <a name="remarks"></a>Remarques  
 Lors de la compilation, les clauses `group` sont traduites en appels à la méthode <xref:System.Linq.Enumerable.GroupBy%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.IGrouping%602>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.Enumerable.ThenBy%2A>  
 <xref:System.Linq.Enumerable.ThenByDescending%2A>  
 [Mots clés de requête (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Comment : créer un groupe imbriqué](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)  
 [Comment : regrouper les résultats d’une requête](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)  
 [Guide pratique pour effectuer une sous-requête sur une opération de regroupement](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
