---
title: "stackalloc (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
dev_langs:
- CSharp
helpviewer_keywords:
- stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 27
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 53d61cfdcf4d356a28881c57ad923017c2b479ae
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="stackalloc-c-reference"></a>stackalloc (référence C#)
Le mot clé `stackalloc` est utilisé dans un contexte de code unsafe pour allouer un bloc de mémoire sur la pile.  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a>Notes  
 Le mot clé est valide uniquement dans les initialiseurs de variable locale. Le code suivant génère des erreurs de compilation.  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 Des types pointeur étant impliqués, `stackalloc` requiert un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md). Pour plus d’informations, consultez [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 `stackalloc` est similaire à [_alloca](/cpp/c-runtime-library/reference/alloca) dans la bibliothèque Runtime C.  
  
 L’exemple suivant calcule et affiche les 20 premiers nombres de la suite de Fibonacci. Chaque nombre est la somme des deux nombres précédents. Dans le code, un bloc de mémoire de taille suffisante pour contenir 20 éléments de type `int` est alloué sur la pile, et non sur le tas. L’adresse du bloc est stockée dans le pointeur `fib`. Cette mémoire n’est pas soumise au garbage collection et n’est donc pas tenue d’être épinglée (en utilisant [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)). La durée de vie du bloc de mémoire est limitée à la durée de vie de la méthode qui le définit. Vous ne pouvez pas libérer la mémoire avant le retour de la méthode.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a>Sécurité  
 Le code unsafe est moins sûr que les alternatives safe. Toutefois, l’utilisation de `stackalloc` active automatiquement les fonctionnalités de détection des dépassements de mémoire tampon dans le Common Language Runtime (CLR). Si un dépassement de mémoire tampon est détecté, le processus est terminé aussi rapidement que possible pour réduire les risques d’exécution de code malveillant.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)

