---
title: "out (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2017-03-01"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "out_CSharpKeyword"
  - "out"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "out (C#)"
  - "out (mot clé C#)"
ms.assetid: 7e911a0c-3f98-4536-87be-d539b7536ca8
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# out (r&#233;f&#233;rence C#)
Vous pouvez utiliser le mot clé contextuel `out` dans deux contextes \(chacun est un lien vers des informations détaillées\), en tant que [modificateur de paramètre](../../../csharp/language-reference/keywords/out-parameter-modifier.md) ou dans les [déclarations de paramètre de type générique](../../../csharp/language-reference/keywords/out-generic-modifier.md) des interfaces et des délégués.  Cette rubrique décrit le modificateur de paramètre, mais vous pouvez consulter[cette autre rubrique](../../../csharp/language-reference/keywords/out-generic-modifier.md) pour plus d'informations sur les déclarations de paramètre de type générique.  
  
 Le mot clé `out` entraîne le passage des arguments par référence.  La situation est similaire à celle du mot clé [ref](../../../csharp/language-reference/keywords/ref.md), à ceci près que `ref` nécessite que la variable soit initialisée avant d'être transmise.  Pour utiliser un paramètre `out`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `out`.  Par exemple :  
  
 [!code-cs[csrefKeywordsMethodParams#1](../../../csharp/language-reference/keywords/codesnippet/csharp/out_1.cs)]  
  
 Bien que les variables passées en tant qu'arguments `out` ne doivent pas être initialisées avant d'être passées, la méthode appelée doit assigner une valeur avant le retour de la méthode.  
  
 Bien que les mots clés `ref` et `out` entraînent un comportement différent lors de l'exécution, ils ne sont pas considérés comme partie de la signature de la méthode au moment de la compilation.  Par conséquent, les méthodes ne peuvent pas être surchargées si la seule différence est que l'une d'elles accepte un argument`ref` et l'autre un argument `out`.  Le code suivant, par exemple, ne se compilera pas :  
  
 [!code-cs[csrefKeywordsMethodParams#2](../../../csharp/language-reference/keywords/codesnippet/csharp/out_2.cs)]  
  
 Cependant, la surcharge peut avoir lieu si une méthode accepte un argument `ref` ou `out` et que l'autre n'utilise aucune des deux, comme suit :  
  
 [!code-cs[csrefKeywordsMethodParams#3](../../../csharp/language-reference/keywords/codesnippet/csharp/out_3.cs)]  
  
 Les propriétés ne sont pas des variables et, par conséquent, ne peuvent pas être passées en tant que paramètres `out`.  
  
 Pour plus d'informations sur le passage de tableaux, consultez [Passage de tableaux à l'aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Vous ne pouvez pas utiliser les mots clés `ref` et `out` pour les types de méthodes suivants :  
  
-   méthodes Async, que vous définissez à l'aide du modificateur [async](../../../csharp/language-reference/keywords/async.md) ;  
  
-   méthodes Iterator, qui incluent une instruction [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.  
  
## Exemple  
 La déclaration d'une méthode `out` est utile lorsque vous souhaitez qu'une méthode retourne plusieurs valeurs.  L'exemple suivant utilise `out` pour retourner trois variables avec un seul appel de méthode.  Notez que le troisième argument reçoit la valeur null.  Cela permet aux méthodes de retourner des valeurs le cas échéant.  
  
 [!code-cs[csrefKeywordsMethodParams#4](../../../csharp/language-reference/keywords/codesnippet/csharp/out_4.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)