---
title: "Arrays declared as structure members cannot be declared with an initial size | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31043"
  - "bc31043"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31043"
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Arrays declared as structure members cannot be declared with an initial size
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Un tableau dans une structure est déclaré avec une taille initiale.  Vous ne pouvez pas initialiser d'élément de structure. À ce titre, vous ne pouvez pas déclarer une taille de tableau car il s'agit d'une forme d'initialisation.  
  
 **ID d'erreur :** BC31043  
  
### Pour corriger cette erreur  
  
1.  Définissez le tableau dans votre structure en tant que dynamique \(sans taille initiale\).  
  
2.  Si vous avez besoin d'une certaine taille de tableau, vous pouvez redimensionner un tableau dynamique avec [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) pendant l'exécution de votre code.  L'exemple suivant illustre ce comportement.  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## Voir aussi  
 [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [How to: Declare a Structure](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)