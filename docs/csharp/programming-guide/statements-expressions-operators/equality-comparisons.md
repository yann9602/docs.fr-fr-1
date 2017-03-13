---
title: "Comparaisons d&#39;&#233;galit&#233; (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "égalité des objets (C#)"
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# Comparaisons d&#39;&#233;galit&#233; (Guide de programmation&#160;C#)
Il est parfois nécessaire de comparer deux valeurs pour déterminer si elles sont égales.  Dans certains cas, vous testez *l'égalité des valeurs*, également appelée *équivalence* ; ce concept signifie que les valeurs contenues dans les deux variables sont égales.  Dans d'autres cas, vous devez déterminer si deux variables font référence au même objet sous\-jacent en mémoire.  Ce type d'égalité est appelé *égalité des références* ou *identité*.  Cette rubrique décrit ces deux types d'égalités et comporte des liens vers d'autres rubriques fournissant des informations complémentaires.  
  
## Égalité des références  
 L'égalité des références signifie que deux références d'objet renvoient au même objet sous\-jacent.  Cette situation peut résulter d'une assignation simple, comme illustré dans l'exemple suivant.  
  
 [!code-cs[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]  
  
 Dans ce code, deux objets sont créés, mais après l'instruction d'assignation, les deux références renvoient au même objet.  Par conséquent, les objets présentent une égalité des références.  Utilisez la méthode <xref:System.Object.ReferenceEquals%2A> pour déterminer si deux références renvoient au même objet.  
  
 Le concept d'égalité des références s'applique uniquement aux types référence.  Les objets de type valeur ne peuvent pas présenter d'égalité des références car lorsqu'une instance d'un type valeur est assignée à une variable, une copie de la valeur est créée.  Par conséquent, deux structures unboxed ne peuvent jamais faire référence au même emplacement en mémoire.  En outre, si vous utilisez <xref:System.Object.ReferenceEquals%2A> pour comparer deux types valeur, le résultat sera toujours `false`, même si les valeurs contenues dans les objets sont toutes identiques.  Cela est dû au fait que chaque variable est convertie \(boxed\) en une instance d'objet séparée.  Pour plus d'informations, consultez [Comment : tester l'égalité des références \(Identité\)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).  
  
## Égalité des valeurs  
 L'égalité des valeurs signifie que deux objets contiennent la ou les mêmes valeurs.  Pour les types valeur primitifs comme [int](../../../csharp/language-reference/keywords/int.md) ou [bool](../../../csharp/language-reference/keywords/bool.md), les tests d'égalité des valeurs sont des opérations simples.  Vous pouvez utiliser l'opérateur [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md), comme indiqué dans l'exemple suivant.  
  
```c#  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 Pour la plupart des autres types, les tests d'égalité des valeurs sont plus complexes car ils requièrent que vous compreniez comment le type définit cette notion.  Pour les classes et structures qui comportent plusieurs champs ou propriétés, l'égalité des valeurs est souvent définie pour indiquer que l'ensemble des champs ou propriétés ont la même valeur.  Par exemple, deux objets `Point` peuvent être définis comme équivalents si pointA.X est égal à pointB.X et pointA.Y est égal à pointB.Y.  
  
 Toutefois, il n'est pas nécessaire que l'équivalence soit basée sur tous les champs d'un type.  Elle peut être basée sur un sous\-ensemble.  Lorsque vous comparez des types dont vous n'êtes pas propriétaire, veillez à bien comprendre comment l'équivalence est définie pour ce type.  Pour plus d'informations sur la définition de l'égalité des valeurs dans vos propres classes et structures, consultez [Comment : définir une égalité de valeurs pour un type](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).  
  
### Égalité des valeurs pour les valeurs à virgule flottante  
 Les comparaisons d'égalité des valeurs à virgule flottante \([double](../../../csharp/language-reference/keywords/double.md) et [float](../../../csharp/language-reference/keywords/float.md)\) sont problématiques en raison de l'imprécision des calculs en virgule flottante sur les ordinateurs binaires.  Pour plus d'informations, consultez les notes de la rubrique <xref:System.Double?displayProperty=fullName>.  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : tester l'égalité des références \(Identité\)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|Explique comment déterminer si deux variables présentent une égalité des références.|  
|[Comment : définir une égalité de valeurs pour un type](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|Indique comment fournir une définition personnalisée de l'égalité des valeurs pour un type.|  
|[Guide de programmation C\#](../../../csharp/programming-guide/index.md)|Fournit des liens vers des informations détaillées relatives aux fonctionnalités importantes du langage C\#, ainsi qu'aux fonctionnalités disponibles en C\# via le .NET Framework.|  
|[Types](../../../csharp/programming-guide/types/index.md)|Fournit des informations relatives au système de type C\# et des liens vers des informations complémentaires.|  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)