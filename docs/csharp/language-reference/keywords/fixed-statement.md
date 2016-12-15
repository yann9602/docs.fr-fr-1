---
title: "fixed, instruction (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "fixed_CSharpKeyword"
  - "fixed"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "fixed (mot clé C#)"
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# fixed, instruction (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'instruction `fixed` empêche le Garbage Collector de déplacer une variable mobile.  L'instruction `fixed` est autorisée uniquement dans un contexte [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  `Fixed` peut également être utilisé pour créer des [mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).  
  
 L'instruction `fixed` place un pointeur vers une variable managée et met cette variable en attente pendant l'exécution de l'instruction.  Sans `fixed`, les pointeurs sur des variables managées seraient de peu d'utilité puisque le recyclage pourrait déplacer les variables de manière imprévisible.  Le compilateur C\# vous permet seulement d'affecter un pointeur à une variable managée dans une instruction `fixed`.  
  
 [!code-cs[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 Vous pouvez initialiser un pointeur à l'aide d'un tableau, d'une chaîne, d'une mémoire tampon de taille fixe, ou de l'adresse d'une variable.  L'exemple suivant illustre l'utilisation d'adresses, de tableaux et de chaînes variables.  Pour plus d'informations sur les mémoires tampon de taille fixe, consultez [Mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).  
  
 [!code-cs[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 Vous pouvez initialiser plusieurs pointeurs, à condition qu'ils soient du même type.  
  
```  
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```  
  
 Pour initialiser des pointeurs de types différents, imbriquez simplement les instructions `fixed`, comme illustré dans l'exemple suivant.  
  
 [!code-cs[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 Après l'exécution du code contenu dans l'instruction, toutes les variables épinglées sont mises hors attente et soumises au recyclage.  Aussi, ne pointez pas sur ces variables hors de l'instruction `fixed`.  
  
> [!NOTE]
>  Les pointeurs initialisés dans des instructions fixed ne peuvent être modifiés.  
  
 En mode unsafe, vous pouvez allouer de la mémoire à la pile dans laquelle elle n'est pas soumise au recyclage, et la mise en attente n'est donc pas nécessaire.  Pour plus d'informations, consultez [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).  
  
## Exemple  
 [!code-cs[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)