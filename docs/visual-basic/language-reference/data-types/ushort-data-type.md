---
title: "UShort Data Type (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ushort"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "literal type characters, US"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "integers, types"
  - "data types [Visual Basic], integral"
  - "UShort data type"
  - "US literal type characters"
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# UShort Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Contient des entiers 16 bits \(2 octets\) non signés dont la valeur est comprise entre 0 et 65 535.  
  
## Notes  
 Utilisez le type de données `UShort` pour contenir les données binaires trop grandes pour `Byte`.  
  
 La valeur par défaut de `UShort` est 0.  
  
## Conseils de programmation  
  
-   **Nombres négatifs.** Dans la mesure où `UShort` est un type non signé, il ne peut représenter un nombre négatif.  Si vous utilisez l'opérateur moins unaire \(`-`\) dans une expression qui correspond au type `UShort`, Visual Basic convertit d'abord l'expression en `Integer`.  
  
-   **Conforme CLS.** Le type de données `UShort` ne faisant pas partie de [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md), le code conforme CLS ne peut pas consommer un composant qui l'utilise.  
  
-   **Extension.** Le type de données `UShort` s'étend à `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`et `Double`.  Ceci signifie que vous pouvez convertir `UShort` en ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caractères de type.** L'ajout des caractères de type littéral `US` à un littéral force ce dernier en un type de données `UShort`.  `UShort` n'a aucun caractère de type identificateur.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.UInt16?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.UInt16>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)