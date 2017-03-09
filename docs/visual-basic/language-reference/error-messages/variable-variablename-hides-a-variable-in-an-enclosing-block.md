---
title: "Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30616"
  - "bc30616"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30616"
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une variable englobée dans un bloc possède le même nom qu'une autre variable locale.  
  
 **ID d'erreur :** BC30616  
  
### Pour corriger cette erreur  
  
-   Renommez la variable du bloc englobé avec un nom différent de toute autre variable locale.  Par exemple :  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   Cette erreur vient généralement de l'utilisation de `Catch e As Exception` à l'intérieur d'un gestionnaire d'événements.  Si tel est le cas, nommez la variable du bloc `Catch` `ex` plutôt que `e`.  
  
-   Cette erreur est également souvent due à la tentative d'accès à une variable locale déclarée à l'intérieur d'un bloc `Try` dans un bloc `Catch` séparé.  Pour corriger cette erreur, déclarez la variable à l'extérieur de la structure `Try...Catch...Finally`.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Déclaration de variable](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)