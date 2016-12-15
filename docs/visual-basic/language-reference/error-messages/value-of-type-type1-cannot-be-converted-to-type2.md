---
title: "Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39; | Microsoft Docs"
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
  - "vbc31194"
  - "bc31194"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31194"
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une valeur de type 'type1' ne peut pas être convertie en 'type2'.Vous pouvez utiliser la propriété 'Value' pour obtenir la valeur de chaîne du premier élément de '\<parentElement\>'.'  
  
 Tentative de cast implicite d'un littéral XML vers un type spécifique.  Le littéral XML ne peut pas être casté implicitement vers le type spécifié.  
  
 **ID d'erreur :** BC31194  
  
### Pour corriger cette erreur  
  
-   Utilisez la propriété `Value` du littéral XML pour référencer sa valeur en tant que `String`.  Utilisez la fonction `CType`, une autre fonction de conversion de type, ou la classe <xref:System.Convert> pour effectuer un cast de la valeur comme type spécifié.  
  
## Voir aussi  
 <xref:System.Convert>   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)