---
title: "&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39; | Microsoft Docs"
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
  - "vbc30149"
  - "bc30149"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30149"
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une classe ou une structure déclare implémenter une interface, mais n'implémente pas une procédure définie par l'interface.  Chaque membre de l'interface doit être implémenté.  
  
 **ID d'erreur :** BC30149  
  
### Pour corriger cette erreur  
  
1.  Déclarez une procédure avec les mêmes nom et signature que ceux définis dans l'interface.  Veillez à inclure au moins l'instruction `End Function` ou `End Sub`.  
  
2.  Ajoutez une clause `Implements` à la fin de l'instruction `Function` ou `Sub`.  Par exemple :  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## Voir aussi  
 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)