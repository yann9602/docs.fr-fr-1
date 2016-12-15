---
title: "How to: Control the Scope of a Variable (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], scope"
  - "declared elements, scope"
  - "visibility, declared elements"
  - "variables [Visual Basic], visibility"
  - "scope, declared elements"
  - "scope, variables"
  - "scope, Visual Basic"
  - "declared elements, visibility"
  - "visibility, variables"
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Control the Scope of a Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Normalement, une variable figure dans la *portée* ou est visible par référence dans l'ensemble de la région dans laquelle vous la déclarez.  Dans certains cas, le *niveau d'accès* de la variable peut influencer sa portée.  
  
 Pour plus d'informations, consultez [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## Portée au niveau du bloc ou de la procédure  
  
#### Pour rendre une variable visible uniquement dans un bloc  
  
-   Placez le [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) de la variable entre les instructions de déclaration de début et de fin de ce bloc, par exemple entre les instructions `For` et `Next` d'une boucle `For`.  
  
     Vous pouvez faire référence à la variable uniquement à partir du bloc.  
  
#### Pour rendre une variable visible uniquement dans une procédure  
  
-   Placez l'instruction `Dim` de la variable à l'intérieur de la procédure, mais à l'extérieur de tout bloc \(tel qu'un bloc `With`...`End With`\).  
  
     Vous pouvez faire référence à la variable uniquement à partir de la procédure, y compris à l'intérieur de tout bloc contenu dans la procédure.  
  
## Portée au niveau du module ou de l'espace de noms  
 Pour des raisons pratiques, le terme *niveau de module* est appliqué indifféremment aux modules, aux classes et aux structures.  Le niveau d'accès d'une variable du niveau du module détermine sa portée.  L'espace de noms qui contient le module, la classe ou la structure influence également la portée.  
  
#### Pour rendre une variable visible dans l'ensemble d'un module, d'une classe ou d'une structure  
  
1.  Placez l'instruction `Dim` de la variable à l'intérieur du module, de la classe ou de la structure, mais à l'extérieur de toute procédure.  
  
2.  Incluez le mot clé [Private](../../../../visual-basic/language-reference/modifiers/private.md) dans l'instruction `Dim`.  
  
3.  Vous pouvez faire référence à la variable de n'importe quel endroit du module, de la classe ou de la structure, mais pas à l'extérieur de ceux\-ci.  
  
#### Pour rendre une variable visible dans l'ensemble d'un espace de noms  
  
1.  Placez l'instruction `Dim` de la variable à l'intérieur du module, de la classe ou de la structure, mais à l'extérieur de toute procédure.  
  
2.  Insérez le mot clé [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) ou [Public](../../../../visual-basic/language-reference/modifiers/public.md) dans l'instruction `Dim`.  
  
3.  Vous pouvez faire référence à la variable de n'importe quel endroit de l'espace de noms qui contient le module, la classe ou la structure.  
  
## Exemple  
 L'exemple suivant déclare une variable au niveau du module et limite sa visibilité au code dans le module.  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 Dans l'exemple précédent, toutes les procédures définies dans le module `demonstrateScope` peuvent faire référence à la variable `String` `strMsg`.  Lors de l'appel de la procédure `usePrivateVariable`, celle\-ci affiche le contenu de la variable chaîne `strMsg` dans une boîte de dialogue.  
  
 Avec la modification suivante apportée à l'exemple ci\-dessus, la variable chaîne `strMsg` peut faire l'objet d'une référence par le code n'importe où dans l'espace de noms de sa déclaration :  
  
```  
Public strMsg As String  
```  
  
## Programmation fiable  
 Plus la portée d'une variable est limitée, moins vous risquez d'y faire référence par erreur à la place d'une autre variable du même nom.  Vous pouvez également réduire les problèmes de correspondance de référence.  
  
## Sécurité .NET Framework  
 Plus la portée d'une variable est limitée, moins vous risquez son utilisation incorrecte par du code malveillant .  
  
## Voir aussi  
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)