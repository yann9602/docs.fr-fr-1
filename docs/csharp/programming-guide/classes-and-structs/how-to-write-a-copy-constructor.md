---
title: "Comment : écrire un constructeur de copie (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f15d8fabc49cbff5515b78a7d2fb6f9e49d0704e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Comment : écrire un constructeur de copie (Guide de programmation C#)
C# ne fournit pas de constructeur de copie pour les objets, mais vous pouvez en écrire un vous-même.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la `Person`[classe](../../../csharp/language-reference/keywords/class.md) définit un constructeur de copie qui prend comme argument une instance de `Person`. Les valeurs des propriétés de l’argument sont assignées aux propriétés de la nouvelle instance de `Person`. Le code contient un autre constructeur de copie qui envoie les propriétés `Name` et `Age` de l’instance que vous voulez copier au constructeur d’instance de la classe.  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ICloneable>  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)
