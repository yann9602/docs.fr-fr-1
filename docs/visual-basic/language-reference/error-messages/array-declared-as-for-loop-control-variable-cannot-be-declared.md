---
title: "Array declared as for loop control variable cannot be declared with an initial size | Microsoft Docs"
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
  - "vbc32039"
  - "bc32039"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32039"
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Array declared as for loop control variable cannot be declared with an initial size
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une boucle `For Each` utilise un tableau comme variable d'itération *élément*, mais initialise ce tableau.  
  
 Les instructions suivantes expliquent comment cette erreur peut être générée :  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 La première instruction `For Each` désigne la méthode d'accès correcte aux éléments de `arrayList`.  La deuxième instruction `For Each` génère cette erreur.  
  
 **ID d'erreur :** BC32039  
  
### Pour corriger cette erreur  
  
-   Supprimez l'initialisation de la déclaration de la variable d'itération *élément*.  
  
## Voir aussi  
 [For...Next, instruction](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Collections](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)