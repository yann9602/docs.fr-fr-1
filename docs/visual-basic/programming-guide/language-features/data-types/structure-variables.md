---
title: Variables de structure (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef42c44de84caffde909eb2b3e9361016a6abb97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="structure-variables-visual-basic"></a>Variables de structure (Visual Basic)
Une fois que vous avez créé une structure, vous pouvez déclarer des variables au niveau de la procédure et au niveau du module en tant que type. Par exemple, vous pouvez créer une structure qui enregistre les informations concernant un système informatique. Cela est illustré par l'exemple suivant.  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 Vous pouvez désormais déclarer des variables de ce type. L’exemple suivant illustre cela.  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  Dans les classes et les modules, les structures déclarées à l’aide de la [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) par défaut d’un accès public. Si vous envisagez une structure soit privée, assurez-vous que vous devez la déclarer à l’aide de la [privé](../../../../visual-basic/language-reference/modifiers/private.md) (mot clé).  
  
## <a name="access-to-structure-values"></a>Accès aux valeurs de la Structure  
 Pour assigner et récupérer des valeurs dans les éléments d’une variable de structure, vous utilisez la même syntaxe que vous utilisez pour définir et obtenir les propriétés sur un objet. Vous placez l’opérateur d’accès au membre (`.`) entre le nom de variable de structure et le nom de l’élément. L’exemple suivant accède à des éléments des variables déclarées précédemment comme type `systemInfo`.  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>Assignation de Variables de Structure  
 Vous pouvez également affecter une variable à un autre si les deux sont du même type de structure. Cette opération copie tous les éléments d’une structure aux éléments correspondants dans l’autre. L’exemple suivant illustre cela.  
  
```  
yourSystem = mySystem  
```  
  
 Si un élément de structure est un type référence, comme un `String`, `Object`, ou tableau, le pointeur vers les données est copié. Dans l’exemple précédent, si `systemInfo` avait inclus une variable objet, puis l’exemple précédent aurait copié le pointeur à partir de `mySystem` à `yourSystem`, et une modification de données de l’objet via une structure seraient en vigueur lors de l’accès par l’autre structure.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Guide pratique : déclarer une structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Structures et autres éléments de programmation](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Structures et classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Structure (instruction)](../../../../visual-basic/language-reference/statements/structure-statement.md)
