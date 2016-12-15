---
title: "Number of indices exceeds the number of dimensions of the indexed array | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30106"
  - "vbc30106"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30106"
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Number of indices exceeds the number of dimensions of the indexed array
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le nombre d'indices utilisé pour accéder à un élément de tableau doit être exactement identique au rang du tableau, c'est\-à\-dire au nombre de dimensions déclaré pour celui\-ci.  
  
 **ID d'erreur :** BC30106  
  
### Pour corriger cette erreur  
  
-   Supprimez des indices de la référence de tableau jusqu'à ce que le nombre total d'indices soit égal au rang du tableau.  Par exemple :  
  
    ```  
    [Visual Basic]  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## Voir aussi  
 [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)