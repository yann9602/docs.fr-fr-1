---
title: "Variables locales implicitement typées (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: 23
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
ms.sourcegitcommit: 1aaa231a807ec50b8bcb922bf0dd218ec72d24ff
ms.openlocfilehash: 21180ce100f81e38b327347e548929a47a2e029d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/25/2017

---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Variables locales implicitement typées (Guide de programmation C#)
Les variables locales peuvent être déclarées sans donner de type explicite. Le mot clé `var` indique au compilateur de déduire le type de la variable à partir de l’expression située à droite de l’instruction d’initialisation. Le type déduit peut être un type intégré, un type anonyme, un type défini par l’utilisateur ou un type défini dans la bibliothèque de classes .NET Framework. Pour plus d’informations sur l’initialisation des tableaux avec `var`, consultez [Tableaux implicitement typés](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
 Les exemples suivants montrent différentes manières de déclarer des variables locales avec `var` :  
  
 [!code-cs[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 Il est important de comprendre que le mot clé `var` n’est pas « variant » et qu’il n’indique pas que la variable est peu typée ou à liaison tardive. Cela signifie simplement que le compilateur détermine et assigne le type qui convient le mieux.  
  
 Le mot clé `var` peut être utilisé dans les contextes suivants :  
  
-   Dans des variables locales (variables déclarées dans la portée de la méthode), comme indiqué dans l’exemple précédent.  
  
-   Dans une instruction d’initialisation [for](../../../csharp/language-reference/keywords/for.md)  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   Dans une instruction d’initialisation [foreach](../../../csharp/language-reference/keywords/foreach-in.md)  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   Dans une instruction [using](../../../csharp/language-reference/keywords/using-statement.md)  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 Pour plus d’informations, consultez [Guide pratique pour utiliser des tableaux et des variables locales implicitement typés dans une expression de requête](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).  
  
## <a name="var-and-anonymous-types"></a>Types de variables et types anonymes  
 Dans de nombreux cas, l’utilisation de `var` est facultative et sert uniquement à simplifier la syntaxe. Toutefois, lorsqu’une variable est initialisée avec un type anonyme, vous devez déclarer la variable en tant que `var` si vous savez déjà que vous aurez besoin d’accéder aux propriétés de l’objet. Il s’agit d’un scénario courant avec les expressions de requête [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)]. Pour plus d’informations, consultez [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Du point de vue de votre code source, un type anonyme n’a pas de nom. Par conséquent, si une variable de requête a été initialisée avec `var`, la seule façon d’accéder aux propriétés de la séquence d’objets retournée consiste à utiliser `var` comme type pour la variable d’itération de l’instruction `foreach`.  
  
 [!code-cs[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a>Remarques  
 Les restrictions suivantes s’appliquent aux déclarations de variables implicitement typées :  
  
-   `var` peut être utilisé uniquement lorsqu’une variable locale est déclarée et initialisée dans la même instruction. La variable ne peut pas être initialisée vers la valeur Null, vers un groupe de méthodes ou vers une fonction anonyme.  
  
-   `var` ne peut pas être utilisé dans les champs situés dans la portée de la classe.  
  
-   Les variables déclarées à l’aide de `var` ne peuvent pas être utilisées dans l’expression d’initialisation. En d’autres termes, l’expression `: int i = (i = 20);` est légale, mais l’expression `var i = (i = 20);` génère une erreur de compilation.  
  
-   Il n’est pas possible d’initialiser plusieurs variables implicitement typées dans la même instruction.  
  
-   Si un type nommé `var` se trouve dans la portée, le mot clé `var` est résolu en ce nom de type et n’est pas considéré comme faisant partie d’une déclaration de variable locale implicitement typée.  
  
 `var` peut également être utile avec les expressions de requête dans lesquelles il est difficile de déterminer le type construit exact de la variable de requête. Cela peut se produire avec les opérations de regroupement et de classement.  
  
 Le mot clé `var` peut également être utile lorsque le type de la variable est fastidieux à taper, ou bien lorsqu’il est évident ou lorsqu’il n’aide pas à la lisibilité du code. Par exemple, `var` est utile avec les types génériques imbriqués tels que ceux utilisés avec les opérations de groupe. Dans la requête suivante, le type de la variable de requête est `IEnumerable<IGrouping<string, Student>>`. Tant que les personnes qui doivent gérer votre code comprennent ceci, le typage implicite peut tout à fait être utilisé pour rendre votre code plus concis et simplifier sa gestion.  
  
 [!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 Toutefois, l’utilisation de `var` risque de rendre votre code plus difficile à comprendre pour les autres développeurs. C’est pourquoi, en général, la documentation C# utilise `var` uniquement lorsque cela est nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Tableaux implicitement typés](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)   
 [Guide pratique pour utiliser des tableaux et des variables locales implicitement typés dans une expression de requête](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)   
 [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Initialiseurs d’objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)   
 [for](../../../csharp/language-reference/keywords/for.md)   
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [using, instruction](../../../csharp/language-reference/keywords/using-statement.md)

