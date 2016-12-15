---
title: "Variables locales implicitement typ&#233;es (Guide de programmation&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "variables locales implicitement typées (C#)"
  - "var (C#)"
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Variables locales implicitement typ&#233;es (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les variables locales peuvent se voir attribuer un « type » déduit de `var` au lieu d'un type explicite.  Le mot clé `var` demande au compilateur de déduire le type de la variable de l'expression à droite de l'instruction d'initialisation.  Le type déduit peut être un type intégré, un type anonyme, un type défini par l'utilisateur ou un type défini dans la bibliothèque de classes .NET Framework.  Pour plus d'informations sur l'initialisation de tableaux avec `var`, consultez [Tableaux implicitement typés](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
 Les exemples suivants présentent différentes directions dans lesquelles les variables locales peuvent être déclarées avec `var` :  
  
 [!code-cs[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 Il est important de comprendre que le mot clé `var` ne signifie pas « Variant » et n'indique pas que la variable est peu typée ou à liaison tardive.  Il signifie juste que le compilateur détermine et assigne le type le plus approprié.  
  
 Le mot clé `var` peut être utilisé dans les contextes suivants :  
  
-   Sur les variables locales \(les variables déclarées à la portée de la méthode\) comme indiqué dans l'exemple précédent.  
  
-   Dans une instruction d'initialisation [for](../../../csharp/language-reference/keywords/for.md).  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   Dans une instruction d'initialisation [foreach](../../../csharp/language-reference/keywords/foreach-in.md).  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   Dans une [instruction using](../../../csharp/language-reference/keywords/using-statement.md)  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 Pour plus d'informations, consultez [Comment : utiliser des tableaux et des variables locales implicitement typés dans une expression de requête](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).  
  
## Types var et anonymes  
 Dans de nombreux cas, l'utilisation de `var` est facultative et simplement plus pratique en termes de syntaxe.  Toutefois, lorsqu'une variable est initialisée avec un type anonyme, vous devez déclarer la variable comme `var` si vous devez accéder aux propriétés de l'objet à un point ultérieur.  C'est un scénario courant dans les expressions de requête [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)].  Pour plus d'informations, consultez [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Du point de vue de votre code source, un type anonyme n'a aucun nom.  Par conséquent, si une variable de requête a été initialisée avec `var`, la seule manière d'accéder aux propriétés dans la séquence d'objets retournée consiste à utiliser `var` comme type de la variable d'itération dans l'instruction `foreach`.  
  
 [!code-cs[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## Notes  
 Les restrictions suivantes s'appliquent aux déclarations de variable implicitement typées :  
  
-   `var` peut être utilisé uniquement lorsqu'une variable locale est déclarée et initialisée dans la même instruction ; la variable ne peut pas être initialisée à la valeur Null, ni à un groupe de méthodes ou une fonction anonyme.  
  
-   `var` ne peut pas être utilisé sur les champs à la portée de classe.  
  
-   Les variables déclarées en utilisant `var` ne peuvent pas être utilisées dans l'expression d'initialisation.  En d'autres termes, l'expression `: int i = (i = 20);` est autorisée, mais cette expression génère une erreur de compilation : `var i = (i = 20);`  
  
-   Plusieurs variables implicitement typées ne peuvent pas être initialisées dans la même instruction.  
  
-   Si un type nommé `var` est dans la portée, le mot clé `var` sera résolu à ce nom de type et ne sera pas traité comme faisant partie d'une déclaration de variable locale implicitement typée.  
  
 `var` peut également s'avérer utile avec les expressions de requête dans lesquelles le type construit exact de la variable de requête est difficile à déterminer.  Cela peut se produire avec les opérations de regroupement et de classement.  
  
 Le mot clé `var` peut également être utile lorsque le type spécifique de la variable est fastidieux à taper au clavier, qu'il est évident ou qu'il n'augmente pas la lisibilité du code.  Les types génériques imbriqués comme ceux utilisés avec les opérations de groupe sont un exemple où `var` est utile de cette manière.  Dans la requête suivante, le type de la variable de requête est `IEnumerable<IGrouping<string, Student>>`.  Tant que vous et ceux qui doivent conserver votre code comprenez ceci, l'utilisation des types implicites pour des raisons de commodité et de concision ne pose aucun problème.  
  
 [!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 Toutefois, l'utilisation de `var` présente au moins l'éventualité que votre code soit plus difficile à comprendre pour d'autres développeurs.  Pour cette raison, la documentation C\# utilise généralement `var` uniquement lorsqu'il est requis.  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Tableaux implicitement typés](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)   
 [Comment : utiliser des tableaux et des variables locales implicitement typés dans une expression de requête](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)   
 [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Initialiseurs d'objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [for](../../../csharp/language-reference/keywords/for.md)   
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [using, instruction](../../../csharp/language-reference/keywords/using-statement.md)