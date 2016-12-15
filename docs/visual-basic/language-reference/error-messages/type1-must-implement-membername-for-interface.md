---
title: "&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39; | Microsoft Docs"
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
  - "vbc30154"
  - "bc30154"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30154"
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

'\<nomtype\>' doit implémenter '\<nommembre\>' pour l'interface '\<nominterface\>'.La propriété d'implémentation doit avoir des spécificateurs 'ReadOnly'\/'WriteOnly' correspondants.  
  
 Une classe ou une structure déclare implémenter une interface, mais n'implémente pas une procédure, une propriété ou un événement défini par l'interface.  Chaque membre de l'interface doit être implémenté.  
  
 **ID d'erreur :** BC30154  
  
### Pour corriger cette erreur  
  
1.  Déclarez un membre avec les mêmes nom et signature que ceux définis dans l'interface.  Veillez à inclure au moins l'instruction `End Function`, `End Sub` ou `End Property`.  
  
2.  Ajoutez une clause `Implements` à la fin de l'instruction `Function`, `Sub`, `Property` ou `Event`.  Par exemple :  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  Lors de l'implémentation d'une propriété, vérifiez que `ReadOnly` ou `WriteOnly` est utilisé de la même manière que dans la définition d'interface.  
  
4.  Lors de l'implémentation d'une propriété, déclarez les procédures `Get` et `Set` si nécessaire.  
  
## Voir aussi  
 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)