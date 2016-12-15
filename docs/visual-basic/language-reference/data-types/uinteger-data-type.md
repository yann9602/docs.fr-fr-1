---
title: "UInteger Data Type | Microsoft Docs"
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
  - "vb.uinteger"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "UInteger data type"
  - "literal type characters, UI"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "integers, types"
  - "UI literal type characters"
  - "data types [Visual Basic], integral"
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# UInteger Data Type
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Contient des entiers 32 bits \(4 octets\) non signés dont la valeur est comprise entre 0 et 4 294 967 295.  
  
## Notes  
 Le type de données `UInteger` fournit la plus grande valeur non signée dans la largeur des données la plus efficace.  
  
 La valeur par défaut de `UInteger` est 0.  
  
## Conseils de programmation  
 Les types de données `UInteger` et `Integer` fournissent une performance optimale sur un processeur de 32 bits, car les plus petits types entiers \(`UShort`, `Short`, `Byte` et `SByte`\), bien qu'ils requièrent moins de bits, sont plus longs à charger, à stocker et à extraire.  
  
-   **Nombres négatifs.** Dans la mesure où `UInteger` est un type non signé, il ne peut représenter un nombre négatif.  Si vous utilisez l'opérateur moins unaire \(`-`\) dans une expression qui correspond au type `UInteger`, Visual Basic convertit d'abord l'expression en `Long`.  
  
-   **Conforme CLS.** Le type de données `UInteger` ne faisant pas partie de [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md), le code conforme CLS ne peut pas consommer un composant qui l'utilise.  
  
-   **Considérations sur l'interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n'oubliez pas que les types tels que `uint` peuvent avoir une largeur des données différente \(16 bits\) dans d'autres environnements.  Si vous passez un argument de 16 bits à un tel composant, déclarez\-le comme type de données `UShort` et non comme `UInteger` dans votre code managé Visual Basic .NET.  
  
-   **Extension.** Le type de données `UInteger` s'étend à `Long`, `ULong`, `Decimal`, `Single` et `Double`.  Ceci signifie que vous pouvez convertir `UInteger` en ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caractères de type.** L'ajout des caractères de type littéral `UI` à un littéral force ce dernier en un type de données `UInteger`.  `UInteger` n'a aucun caractère de type identificateur.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.UInt32?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.UInt32>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)