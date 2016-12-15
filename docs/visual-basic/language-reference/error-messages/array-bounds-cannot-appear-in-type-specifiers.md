---
title: "Array bounds cannot appear in type specifiers | Microsoft Docs"
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
  - "vbc30638"
  - "bc30638"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30638"
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Array bounds cannot appear in type specifiers
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les tailles de tableau ne peuvent pas être déclarées comme partie d'un spécificateur de type de données.  
  
 **ID d'erreur :** BC30638  
  
### Pour corriger cette erreur  
  
-   Spécifiez la taille du tableau immédiatement après le nom de variable au lieu de la placer après le type, comme le montre l'exemple suivant.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   Définissez un tableau et initialisez\-le avec le nombre d'éléments souhaité, comme le montre l'exemple suivant.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## Voir aussi  
 [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)