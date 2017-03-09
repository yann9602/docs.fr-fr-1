---
title: "Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30424"
  - "bc30424"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30424"
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous avez essayé de déclarer une constante en tant que classe, structure ou type tableau, ou en tant que paramètre de type défini par un type générique conteneur.  
  
 Les constantes doivent être de type intrinsèque \(`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong` ou `UShort`\) ou de type `Enum` basé sur l'un des types intégraux.  
  
 **ID d'erreur :** BC30424  
  
### Pour corriger cette erreur  
  
1.  Déclarez la constante en tant que type intrinsèque ou `Enum`.  
  
2.  Une constante peut aussi être une valeur spéciale, telle que `True`, `False` ou `Nothing`.  Le compilateur considère que ces valeurs prédéfinies sont du type intrinsèque approprié.  
  
## Voir aussi  
 [Constants and Enumerations](../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Types de données](../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)