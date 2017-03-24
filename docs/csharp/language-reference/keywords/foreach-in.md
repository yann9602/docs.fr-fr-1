---
title: "foreach, in (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "foreach"
  - "foreach_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "foreach (mot clé C#)"
  - "foreach (instruction C#)"
  - "in (mot clé C#)"
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# foreach, in (r&#233;f&#233;rence C#)
L'instruction `foreach` répète un groupe d'instructions incorporées pour chaque élément d'un tableau ou d'une collection d'objets qui implémente l'interface <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>.  L'instruction `foreach` sert à itérer au sein de la collection pour obtenir les informations souhaitées, mais elle ne peut pas être utilisée pour ajouter ou supprimer des éléments dans la collection source, ceci afin d'éviter des effets secondaires imprévisibles.  Si vous devez ajouter ou supprimer des éléments dans la collection source, utilisez une boucle [for](../../../csharp/language-reference/keywords/for.md).  
  
 Les instructions incorporées continuent à être exécutées pour chaque élément dans le tableau ou la collection.  Une fois l'itération terminée pour tous les éléments de la collection, le contrôle est transféré à l'instruction suivante après le bloc `foreach`.  
  
 À n'importe quel point du bloc `foreach`, vous pouvez interrompre la boucle à l'aide du mot clé [break](../../../csharp/language-reference/keywords/break.md) ou passer directement à l'itération suivante de la boucle en utilisant le mot clé [continue](../../../csharp/language-reference/keywords/continue.md).  
  
 Une boucle `foreach` peut également être quittée à l'aide des instructions [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).  
  
 Pour plus d'informations sur le mot clé `foreach` et les exemples de code, consultez les rubriques suivantes :  
  
 [Utilisation de foreach avec des tableaux](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
 [Comment : accéder à une classe de collection à l'aide de foreach](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  
  
## Exemple  
 L'exemple de code suivant illustre trois exemples :  
  
-   boucle `foreach` typique qui affiche le contenu d'un tableau d'entiers  
  
-   une boucle [for](../../../csharp/language-reference/keywords/for.md) avec le même effet  
  
-   une boucle `foreach` qui comptabilise les éléments du tableau  
  
 [!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/foreach-in_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Instructions d'itération](../../../csharp/language-reference/keywords/iteration-statements.md)   
 [for](../../../csharp/language-reference/keywords/for.md)