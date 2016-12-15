---
title: "ULong Data Type (Visual Basic) | Microsoft Docs"
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
  - "vb.ulong"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "integers, types"
  - "data types [Visual Basic], integral"
  - "literal type characters, UL"
  - "ULong data type"
  - "UL literal type characters"
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ULong Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Contient des entiers 64 bits \(8 octets\) non signés dont la valeur est comprise entre 0 et 18 446 744 073 709 551 615 \(plus que 1,84 fois 10 ^ 19\).  
  
## Notes  
 Utilisez le type de données `ULong` pour stocker les données binaires trop grandes pour `UInteger` ou les plus grandes valeurs entières non signées possibles.  
  
 La valeur par défaut de `ULong` est 0.  
  
## Conseils de programmation  
  
-   **Nombres négatifs.** Dans la mesure où `ULong` est un type non signé, il ne peut représenter un nombre négatif.  Si vous utilisez l'opérateur moins unaire \(`-`\) dans une expression qui correspond au type `ULong`, Visual Basic convertit d'abord l'expression en `Decimal`.  
  
-   **Conforme CLS.** Le type de données `ULong` ne faisant pas partie de [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md), le code conforme CLS ne peut pas consommer un composant qui l'utilise.  
  
-   **Considérations sur l'interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n'oubliez pas que les types tels que `ulong` peuvent avoir une largeur des données différente \(32 bits\) dans d'autres environnements.  Si vous passez un argument de 32 bits à un tel composant, déclarez\-le comme type de données `UInteger` et non comme `ULong` dans votre code managé Visual Basic .NET.  
  
     En outre, l'Automatisation ne prend pas en charge les nombres entiers 64 bits sur Windows 95, Windows 98, Windows ME ou Windows 2000.  Vous ne pouvez pas passer d'argument `ULong` Visual Basic à un composant Automation sur ces plateformes.  
  
-   **Extension.** Le type de données `ULong` s'étend à `Decimal`, `Single` et `Double`.  Ceci signifie que vous pouvez convertir `ULong` en ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caractères de type.** L'ajout des caractères de type littéral `UL` à un littéral force ce dernier en un type de données `ULong`.  `ULong` n'a aucun caractère de type identificateur.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.UInt64?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.UInt64>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)