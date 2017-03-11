---
title: "Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc32053"
  - "vbc32053"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32053"
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une procédure est appelée avec un argument qui s'étend au type de paramètre correspondant, et la conversion du paramètre à l'argument est restrictive.  
  
 Lorsque vous définissez une classe ou une structure, vous pouvez définir un ou plusieurs opérateurs de conversion pour convertir ce type de classe ou de structure en d'autres types.  Vous pouvez également définir des opérateurs de conversion inverse pour convertir ces autres types en votre type de classe ou de structure.  Lorsque vous utilisez votre type de classe ou de structure dans un appel de procédure, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] peut utiliser ces opérateurs de conversion pour convertir le type d'un argument en type de son paramètre correspondant.  
  
 Si vous passez l'argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] copie parfois sa valeur dans une variable locale de la procédure au lieu de passer une référence.  Dans ce cas, lors du retour de la procédure, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] doit copier la valeur de la variable locale dans l'argument du code appelant.  
  
 Si une valeur d'argument `ByRef` est copiée dans la procédure et que l'argument et le paramètre sont du même type, aucune conversion n'est nécessaire.  Mais si les types sont différents, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] doit effectuer une conversion dans les deux sens.  Si l'un des types est votre type de classe ou de structure, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] doit le convertir vers et à partir de l'autre type.  Si l'une de ces conversions est étendue, la conversion inverse peut être restrictive.  
  
 **ID d'erreur :** BC32053  
  
### Pour corriger cette erreur  
  
-   Si possible, utilisez un argument d'appel du même type que le paramètre de procédure. Ainsi, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] n'a pas besoin d'effectuer une conversion.  
  
-   Si vous devez appeler la procédure avec un type d'argument autre que le type du paramètre, sans retourner une valeur dans l'argument d'appel, affectez au paramètre la valeur [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) au lieu de `ByRef`.  
  
-   Si vous devez retourner une valeur dans l'argument d'appel, affectez à l'opérateur de conversion inverse la valeur [Widening](../../../visual-basic/language-reference/modifiers/widening.md), si possible.  
  
## Voir aussi  
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)