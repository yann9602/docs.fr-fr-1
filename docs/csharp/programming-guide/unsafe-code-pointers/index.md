---
title: "Pointeurs et code unsafe (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "sécurité [C#], sécurité de type"
  - "langage C#, code unsafe"
  - "sécurité de type [C#]"
  - "unsafe, mot clé [C#]"
  - "code unsafe [C#]"
  - "langage C#, pointeurs"
  - "pointeurs [C#], à propos des pointeurs"
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Pointeurs et code unsafe (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Pour maintenir la sécurité et la fiabilité des types, par défaut, C\# ne prend pas en charge d'opérations arithmétiques sur les pointeurs.  Toutefois, à l'aide du mot clé [unsafe](../../../csharp/language-reference/keywords/unsafe.md), vous pouvez définir un contexte unsafe dans lequel des pointeurs peuvent être utilisés.  Pour plus d'informations sur les pointeurs, consultez la rubrique [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).  
  
> [!NOTE]
>  Dans le Common Language Runtime \(CLR\), le code unsafe est connu sous le nom de code non vérifiable.  Le code unsafe en C\# n'est pas toujours dangereux ; c'est simplement du code dont le CLR ne peut pas vérifier la sécurité.  Par conséquent, le CLR n'exécute du code unsafe que s'il se trouve dans un assembly d'un niveau de confiance suffisant.  Si vous utilisez du code unsafe, il est de votre responsabilité de garantir qu'il n'entraîne pas de problèmes de sécurité ou d'erreurs de pointeur.  
  
## Vue d'ensemble du code unsafe  
 Le code unsafe a les propriétés suivantes :  
  
-   Les méthodes, types et blocs de code peuvent être définis comme unsafe.  
  
-   Dans certains cas, le code unsafe augmente les performances d'une application lorsqu'il supprime les contrôles de limites d'index de tableau.  
  
-   Le code unsafe est requis lorsque vous appelez des fonctions natives nécessitant des pointeurs.  
  
-   L'utilisation d'un code unsafe introduit des risques de sécurité et de stabilité.  
  
-   Pour que le code unsafe en C\#  puisse être compilé, l'application doit être compilée avec [\/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  
  
## Rubriques connexes  
 Pour plus d'informations, consultez :  
  
-   [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [Mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [Comment : utiliser des pointeurs pour copier un tableau d'octets](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)