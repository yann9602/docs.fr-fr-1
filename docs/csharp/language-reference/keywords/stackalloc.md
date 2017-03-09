---
title: "stackalloc (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "stackalloc_CSharpKeyword"
  - "stackalloc"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "stackalloc (mot clé C#)"
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 27
---
# stackalloc (r&#233;f&#233;rence C#)
Le mot clé `stackalloc` est utilisé dans un contexte de code unsafe pour allouer un bloc de mémoire sur la pile.  
  
```  
int* block = stackalloc int[100];  
```  
  
## Notes  
 Le mot clé est valide uniquement dans les initialiseurs de variable locale.  Le code suivant génère des erreurs de compilation.  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 Des types pointeur étant impliqués, `stackalloc` requiert un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  Pour plus d'informations, consultez [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 `stackalloc` est similaire à [\_alloca](/visual-cpp/c-runtime-library/reference/alloca) dans la bibliothèque Runtime C.  
  
 L'exemple suivant calcule et affiche les 20 premiers numéros dans la séquence de Fibonacci.  Chaque numéro est la somme des deux nombres précédents.  Dans le code, un bloc de mémoire d'une taille suffisante pour contenir 20 éléments de type `int` est alloué sur la pile, et non sur le tas.  L'adresse du bloc est stockée dans le pointeur `fib`.  Cette mémoire ne fait pas l'objet de garbage collection et ne doit donc pas être épinglée \(par le biais de [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)\).  La durée de vie du bloc de mémoire est limitée à la durée de vie de la méthode qui le définit.  Vous ne pouvez pas libérer la mémoire avant le retour de la méthode.  
  
## Exemple  
 [!code-cs[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#15)]  
  
## Sécurité  
 Le code unsafe est moins sûr que les alternatives safe.  Toutefois, l'utilisation de `stackalloc` active automatiquement les fonctionnalités de détection de dépassement de mémoire tampon dans le common language runtime \(CLR\).  Si un dépassement de mémoire tampon est détecté, le processus est terminé aussi rapidement que possible, afin de réduire les risques d'exécution de code malveillant.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)