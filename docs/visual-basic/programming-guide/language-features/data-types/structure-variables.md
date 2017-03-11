---
title: "Structure Variables (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "structures, variables"
  - "structures, structure variables"
  - "variables [Visual Basic], structure variables"
  - "structure variables"
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Structure Variables (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une fois que vous avez créé une structure, vous pouvez déclarer des variables du niveau procédure ou du niveau module avec ce type.  Par exemple, vous pouvez créer une structure qui enregistre des informations à propos d'un ordinateur.  C'est ce qu'illustre l'exemple suivant.  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 Vous pouvez désormais déclarer des variables de ce type.  L'exemple suivant illustre ce comportement.  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  Dans les classes et les modules, les structures déclarées à l'aide de [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) ont par défaut un accès public.  Si vous souhaitez qu'une structure soit privée, veillez à la déclarer à l'aide du mot clé [Private](../../../../visual-basic/language-reference/modifiers/private.md).  
  
## Accès aux valeurs des structures  
 Pour assigner et extraire des valeurs à partir des éléments d'une variable de structure, vous utilisez la même syntaxe que pour définir et récupérer les propriétés d'un objet.  Placez l'opérateur d'accès aux membres \(`.`\) entre le nom de la variable de structure et le nom de l'élément.  L'exemple suivant accède à des éléments des variables déclarées précédemment comme type `systemInfo`.  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## Assigner des variables de structure  
 Vous pouvez également assigner une variable à une autre si toutes deux ont le même type structure.  Cette opération copie tous les éléments d'une structure dans les éléments correspondants d'une autre.  L'exemple suivant illustre ce comportement.  
  
```  
yourSystem = mySystem  
```  
  
 Si un élément de structure est un type référence \(par exemple, `String`, `Object` ou un tableau\), le pointeur vers les données est copié.  Dans l'exemple précédent, si `systemInfo` avait inclus une variable d'objet, l'exemple précédent aurait copié le pointeur à partir de `mySystem` dans `yourSystem`, et une modification vers les données de l'objet serait appliquée par l'intermédiaire d'une structure lors de son accès par l'autre structure.  
  
## Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)