---
title: "Comment : utiliser des pointeurs pour copier un tableau d'octets (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 375cab76063e4c77515d6b05b42f2d97ff3efc44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Comment : utiliser des pointeurs pour copier un tableau d'octets (Guide de programmation C#)
L’exemple suivant utilise des pointeurs pour copier des octets d’un tableau à un autre.  
  
 Cet exemple utilise le mot clé [unsafe](../../../csharp/language-reference/keywords/unsafe.md), qui vous permet d’utiliser des pointeurs dans la méthode `Copy`. L’instruction [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) permet de déclarer des pointeurs vers les tableaux source et de destination. Elle *épingle* l’emplacement des tableaux source et de destination en mémoire pour qu’ils ne soient pas déplacés par l’opération de garbage collection. Les blocs de mémoire des tableaux sont libérés quand le bloc `fixed` est effectué. Comme la méthode `Copy` dans cet exemple utilise le mot clé `unsafe`, elle doit être compilée avec l’option de compilateur **/unsafe**. Pour définir l’option dans Visual Studio, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Propriétés**. Sous l’onglet **Générer**, sélectionnez **Autoriser le code unsafe**.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [/unsafe (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)  
 [Nettoyage de la mémoire](../../../standard/garbage-collection/index.md)
