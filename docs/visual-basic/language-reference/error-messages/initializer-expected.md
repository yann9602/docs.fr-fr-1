---
title: "Initializer expected | Microsoft Docs"
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
  - "vbc30996"
  - "bc30996"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30996"
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Initializer expected
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous avez essayé de déclarer une instance d'une classe en utilisant un initialiseur d'objet dans lequel la liste d'initialisation est vide, comme indiqué dans l'exemple suivant.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 Au moins un champ ou une propriété doit être initialisé dans la liste d'initialiseurs, comme indiqué dans l'exemple suivant.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **ID d'erreur :** BC30996  
  
### Pour corriger cette erreur  
  
1.  Initialisez au moins un champ ou une propriété dans l'initialiseur ou n'utilisez pas d'initialiseur d'objet.  
  
## Voir aussi  
 [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)