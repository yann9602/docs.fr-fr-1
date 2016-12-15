---
title: "Overflow (Visual Basic Run-Time Error) | Microsoft Docs"
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
  - "vbrERRID_Overflow"
dev_langs: 
  - "VB"
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Overflow (Visual Basic Run-Time Error)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un dépassement de capacité se produit lorsque vous tentez d'effectuer une assignation qui dépasse les limites de la cible de l'assignation.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que les résultats des assignations, calculs et conversions de types de données ne sont pas trop grands pour être représentés dans la plage de variables autorisées pour ce type de valeur et assignez la valeur à une variable d'un type pouvant contenir une plage plus étendue de valeurs, si nécessaire.  
  
2.  Vérifiez que les assignations aux propriétés correspondent à la plage de la propriété dans laquelle elles sont effectuées.  
  
3.  Vérifiez que les nombres utilisés dans les calculs et convertis en entiers n'ont pas de résultats supérieurs aux entiers.  
  
## Voir aussi  
 <xref:System.Int32.MaxValue?displayProperty=fullName>   
 <xref:System.Double.MaxValue?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)