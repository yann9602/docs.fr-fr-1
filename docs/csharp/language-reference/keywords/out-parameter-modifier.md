---
title: "out, modificateur de param&#232;tre (R&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "out (paramètres C#)"
  - "paramètres (C#), out"
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 9
---
# out, modificateur de param&#232;tre (R&#233;f&#233;rence C#)
Le mot clé `out` fait en sorte que les arguments soient passés par référence.  Il est semblable au mot clé [ref](../../../csharp/language-reference/keywords/ref.md), mais `ref` nécessite que la variable soit initialisée avant d'être passée.  Pour utiliser un paramètre `out`, la définition de méthode et la méthode d'appel doivent toutes deux utiliser le mot clé `out` explicitement.  Par exemple :  
  
 [!code-cs[csrefKeywordsMethodParams#1](../../../csharp/language-reference/keywords/codesnippet/csharp/out-parameter-modifier_1.cs)]  
  
 Bien que les variables passées en tant qu'arguments `out` n'aient pas besoin d'être initialisées avant d'être passées, la méthode appelée est requise pour assigner une valeur avant le retour de la méthode.  
  
 Bien que les mots clés `ref` et `out` entraînent des comportements différents au moment de l'exécution, ils ne sont pas considérés comme faisant partie de la signature de méthode au moment de la compilation.  Par conséquent, les méthodes ne peuvent pas être surchargées si une méthode prend un argument `ref` et que l'autre prend un argument `out`.  Par conséquent, l'exemple de code suivant ne procèdera pas à la compilation :  
  
 [!code-cs[csrefKeywordsMethodParams#2](../../../csharp/language-reference/keywords/codesnippet/csharp/out-parameter-modifier_2.cs)]  
  
 Toutefois, la surcharge peut survenir si une méthode prend un argument `ref` ou `out` et si l'autre n'utilise ni l'un ni l'autre, comme suit :  
  
 [!code-cs[csrefKeywordsMethodParams#3](../../../csharp/language-reference/keywords/codesnippet/csharp/out-parameter-modifier_3.cs)]  
  
 Les propriétés ne sont pas des variables et par conséquent ne peuvent pas être passées en tant que paramètres `out`.  
  
 Pour plus d'informations sur le passage de tableaux, consultez [Passage de tableaux à l'aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Vous ne pouvez pas utiliser les mots clés d' `ref` et d' `out` pour les types suivants de méthodes :  
  
-   Méthodes Async, que vous définissez à l'aide de le modificateur d' [async](../../../csharp/language-reference/keywords/async.md) .  
  
-   Méthodes d'itérateur, qui incluent une instruction de [retour yield](../../../csharp/language-reference/keywords/yield.md) ou d' `yield break` .  
  
## Exemple  
 Déclarer une méthode `out` est utile si vous voulez qu'une méthode retourne plusieurs valeurs.  Cet exemple utilise `out` pour retourner trois variables avec un seul appel de méthode.  Notez que le troisième argument est assigné à la valeur Null.  Cela permet aux méthodes de retourner éventuellement des valeurs.  
  
 [!code-cs[csrefKeywordsMethodParams#4](../../../csharp/language-reference/keywords/codesnippet/csharp/out-parameter-modifier_4.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Paramètres de méthodes](../../../csharp/language-reference/keywords/method-parameters.md)