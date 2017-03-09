---
title: "Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument. | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc41999"
  - "bc41999"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC41999"
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une procédure est appelée avec un argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) d'un type différent de celui de son paramètre correspondant.  
  
 Si vous passez un argument `ByRef`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] copie parfois sa valeur dans une variable locale de la procédure au lieu de passer une référence.  Dans ce cas, lors du retour de la procédure, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] doit copier la valeur de la variable locale dans l'argument du code appelant.  
  
 Si une valeur d'argument `ByRef` est copiée dans la procédure et que l'argument et le paramètre sont du même type, aucune conversion n'est nécessaire.  Mais si les types sont différents, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] doit effectuer une conversion dans les deux sens.  Étant donné que vous ne pouvez pas utiliser `CType` ou l'un des autres mots clés de conversion sur un argument ou un paramètre de procédure, une telle conversion est toujours implicite.  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC41999  
  
### Pour corriger cette erreur  
  
-   Si possible, utilisez un argument d'appel du même type que le paramètre de procédure. Ainsi, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] n'a pas besoin d'effectuer une conversion.  
  
-   Si vous devez appeler la procédure avec un type d'argument autre que le type du paramètre, sans retourner une valeur dans l'argument d'appel, affectez au paramètre la valeur [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) au lieu de `ByRef`.  
  
## Voir aussi  
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)