---
title: "Comment : utiliser des pointeurs pour copier un tableau d'octets (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: 21
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
ms.openlocfilehash: 808a74f75e4dcbcec47735d98063138e2c7456e5
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Comment : utiliser des pointeurs pour copier un tableau d'octets (Guide de programmation C#)
L’exemple suivant utilise des pointeurs pour copier des octets d’un tableau à un autre.  
  
 Cet exemple utilise le mot clé [unsafe](../../../csharp/language-reference/keywords/unsafe.md), qui vous permet d’utiliser des pointeurs dans la méthode `Copy`. L’instruction [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) permet de déclarer des pointeurs vers les tableaux source et de destination. Elle *épingle* l’emplacement des tableaux source et de destination en mémoire pour qu’ils ne soient pas déplacés par l’opération de garbage collection. Les blocs de mémoire des tableaux sont libérés quand le bloc `fixed` est effectué. Comme la méthode `Copy` dans cet exemple utilise le mot clé `unsafe`, elle doit être compilée avec l’option de compilateur **/unsafe**. Pour définir l’option dans Visual Studio, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Propriétés**. Sous l’onglet **Générer**, sélectionnez **Autoriser le code unsafe**.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-cs[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [-unsafe (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)   
 [Nettoyage de la mémoire](../../../standard/garbage-collection/index.md)

