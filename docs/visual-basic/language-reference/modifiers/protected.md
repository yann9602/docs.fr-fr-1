---
title: Protected (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0cc7a0cb626a9ec8e2a0e47abc02e5268aed56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)
Spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de leur propre classe ou d’une classe dérivée.  
  
## <a name="remarks"></a>Remarques  
 Parfois, un élément de programmation déclaré dans une classe contient des données sensibles ou du code restreint et vous souhaitez limiter l’accès à l’élément. Toutefois, si la classe peut être héritée et que vous prévoyez une hiérarchie de classes dérivées, il peut être nécessaire pour ces classes dérivées accéder aux données ou au code. Dans ce cas, vous souhaitez que l’élément doit être accessible à la fois à partir de la classe de base et de toutes les classes dérivées. Pour limiter l’accès à un élément de cette manière, vous pouvez déclarer avec `Protected`.  
  
## <a name="rules"></a>Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser `Protected` uniquement au niveau de la classe. Cela signifie que le contexte de déclaration pour un `Protected` élément doit être une classe et ne peut pas être un fichier source, espace de noms, interface, un module, structure ou procédure.  
  
-   **Modificateurs combinés.** Vous pouvez utiliser la `Protected` modificateur avec la [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modificateur dans la même déclaration. Cette combinaison rend les éléments déclarés accessibles à partir de n’importe où dans le même assembly, de leur propre classe et de classes dérivées. Vous pouvez spécifier `Protected Friend` uniquement sur les membres de classes.  
  
## <a name="behavior"></a>Comportement  
  
-   **Niveau d’accès.** Tout le code dans une classe peut accéder à ses éléments. Le code dans n’importe quelle classe qui dérive d’une classe de base peut accéder à tous les `Protected` les éléments de la classe de base. Cela est vrai pour toutes les générations de dérivation. Cela signifie qu’une classe peut accéder `Protected` les éléments de la classe de base de la classe de base et ainsi de suite.  
  
     L’accès protégé n’est pas un sur-ensemble ou un sous-ensemble de l’accès ami.  
  
-   **Modificateurs d’accès.** Les mots clés qui spécifient le niveau d’accès sont appelés *les modificateurs d’accès*. Pour obtenir une comparaison des modificateurs d’accès, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Le modificateur `Protected` peut être utilisé dans les contextes suivants :  
  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate (instruction)](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum (instruction)](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
