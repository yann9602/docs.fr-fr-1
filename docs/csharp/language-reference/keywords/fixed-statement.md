---
title: "fixed, instruction (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
dev_langs:
- CSharp
helpviewer_keywords:
- fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 24
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ba0099b812de1dbcfebe4943c0fe36598f102169
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="fixed-statement-c-reference"></a>fixed, instruction (référence C#)
L’instruction `fixed` empêche le récupérateur de mémoire de déplacer une variable mobile. L’instruction `fixed` est uniquement autorisée dans un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md). `Fixed` peut également être utilisé pour créer des [mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).  
  
 L’instruction `fixed` définit un pointeur vers une variable managée et épingle cette variable pendant l’exécution de l’instruction. Sans `fixed`, les pointeurs de variables managées déplaçables seraient peu utiles puisque le garbage collection pourrait déplacer les variables de manière imprévisible. Le compilateur C# permet seulement d’assigner un pointeur à une variable managée dans une instruction `fixed`.  
  
 [!code-cs[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 Vous pouvez initialiser un pointeur à l’aide d’un tableau, d’une chaîne, d’un tampon de taille fixe ou de l’adresse d’une variable. L’exemple suivant montre l’utilisation des adresses de variables, des tableaux et des chaînes. Pour plus d’informations sur les mémoires tampons de taille fixe, consultez [Mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).  
  
 [!code-cs[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 Vous pouvez initialiser plusieurs pointeurs, tant qu’ils sont tous du même type.  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 Pour initialiser des pointeurs de types différents, imbriquez des instructions `fixed`, comme indiqué dans l’exemple suivant.  
  
 [!code-cs[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 Une fois que le code de l’instruction est exécuté, toutes les variables épinglées sont libérées et soumises au garbage collection. Par conséquent, ne pointez pas vers ces variables en dehors de l’instruction `fixed`.  
  
> [!NOTE]
>  Les pointeurs initialisés dans les instructions fixed ne peuvent pas être modifiés.  
  
 En mode unsafe, vous pouvez allouer de la mémoire sur la pile, où elle n’est pas soumise au garbage collection et n’a donc pas besoin d’être épinglée. Pour plus d’informations, consultez [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).  
  
## <a name="example"></a>Exemple  
 [!code-cs[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
