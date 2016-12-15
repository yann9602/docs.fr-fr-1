---
title: "Types (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "types de données (C#), système de type"
  - "types (C#)"
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Types (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le système de types C\# comporte les catégories suivantes :  
  
-   [Types valeur](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [Types référence](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Types de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 Les variables de types valeur stockent des données alors que les variables de types référence stockent les références aux données.  Les types référence sont également considérés comme des objets.  Les types pointeur ne peuvent être utilisés qu'en mode [non sécurisé](../../../csharp/language-reference/keywords/unsafe.md).  
  
 Il est possible de convertir un type valeur en type référence, puis de revenir en type valeur, en effectuant un [boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  Vous ne pouvez pas convertir un type référence en type valeur, sauf s'il s'agit d'un type valeur boxed.  
  
 En outre, cette section présente [void](../../../csharp/language-reference/keywords/void.md).  
  
 Les types valeur sont également Nullable, ce qui signifie qu'ils peuvent stocker un état de non\-valeur supplémentaire.  Pour plus d'informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableaux de référence des types](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [Types](../../../csharp/programming-guide/types/index.md)