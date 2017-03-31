---
title: "Regrouper les résultats d’une requête"
description: "Comment regrouper des résultats."
keywords: .NET, .NET Core, C#
author: stevehoag
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ee1ad2d65fda8a524b42f44f893e0b6f5f81eea5
ms.lasthandoff: 03/13/2017

---
# <a name="group-query-results"></a>Regrouper les résultats d’une requête

Le regroupement est l’une des fonctionnalités les plus puissantes de LINQ. Les exemples suivants montrent comment regrouper des données de différentes manières :  
  
-   Selon une propriété  
  
-   Selon la première lettre d’une propriété de chaîne  
  
-   Selon une plage numérique calculée  
  
-   Selon un prédicat booléen ou une autre expression  
  
-   Selon une clé composée  
  
 En outre, les deux dernières requêtes projettent leurs résultats dans un nouveau type anonyme qui contient uniquement le prénom et le nom de l’étudiant. Pour plus d’informations, consultez [group, clause](../language-reference/keywords/group-clause.md).  
  
## <a name="example"></a>Exemple  
 Tous les exemples de cette rubrique utilisent les classes d’assistance et les sources de données suivantes.  
  
 [!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment regrouper des éléments source en utilisant une propriété de l’élément comme clé de groupe. Dans ce cas, la clé est un `string`, qui correspond au nom de l’étudiant. Il est également possible d’utiliser une sous-chaîne comme clé. L’opération de regroupement utilise le comparateur d’égalité par défaut pour le type.  
  
 Copiez-collez la méthode suivante dans la classe `StudentClass`. Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupBySingleProperty()`.  
  
 [!code-cs[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment regrouper des éléments source en utilisant autre chose qu’une propriété de l’objet comme clé de groupe. Dans cet exemple, la clé est la première lettre du nom de l’étudiant.  
  
 Copiez-collez la méthode suivante dans la classe `StudentClass`. Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupBySubstring()`.  
  
 [!code-cs[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment regrouper des éléments source en utilisant une plage numérique comme clé de groupe. La requête projette ensuite les résultats dans un type anonyme qui contient uniquement le prénom et le nom de l’étudiant, ainsi que la plage de centiles à laquelle appartient l’étudiant. Un type anonyme est utilisé, car il n’est pas nécessaire d’utiliser l’intégralité de l’objet `Student` pour afficher les résultats. `GetPercentile` est une fonction d’assistance qui calcule un centile à partir de la note moyenne obtenue par l’étudiant. La méthode retourne un entier compris entre 0 et 10.  
  
 [!code-cs[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 Copiez-collez la méthode suivante dans la classe `StudentClass`. Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupByRange()`.  
  
 [!code-cs[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment regrouper des éléments source en utilisant une expression de comparaison booléenne. Dans cet exemple, l’expression booléenne teste si la note moyenne d’un étudiant est supérieure à 75. Comme dans les exemples précédents, les résultats sont projetés dans un type anonyme, car il n’est pas nécessaire d’avoir l’élément source complet. Notez que les propriétés du type anonyme deviennent des propriétés du membre `Key` et sont accessibles par nom lorsque la requête est exécutée.  
  
 Copiez-collez la méthode suivante dans la classe `StudentClass`. Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupByBoolean()`.  
  
 [!code-cs[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser un type anonyme pour encapsuler une clé qui contient plusieurs valeurs. Dans cet exemple, la première valeur de clé est la première lettre du nom de l’étudiant. La deuxième valeur de clé est une valeur booléenne qui spécifie si l’étudiant a obtenu une note supérieure à 85 au premier examen. Vous pouvez organiser les groupes selon n’importe quelle propriété de la clé.  
  
 Copiez-collez la méthode suivante dans la classe `StudentClass`. Remplacez l’instruction d’appel de la méthode `Main` par `sc.GroupByCompositeKey()`.  
  
 [!code-cs[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.Enumerable.GroupBy%2A>   
 <xref:System.Linq.IGrouping%602>   
 [Expressions de requête LINQ](index.md)   
 [group, clause](../language-reference/keywords/group-clause.md)   
 [Types anonymes](../programming-guide/classes-and-structs/anonymous-types.md)   
 [Effectuer une sous-requête sur une opération de regroupement](perform-a-subquery-on-a-grouping-operation.md)   
 [Créer un groupe imbriqué](create-a-nested-group.md)   
 [Regroupement de données](../programming-guide/concepts/linq/grouping-data.md)
