---
title: "Valeur de type &#39; type1 &#39; ne peut pas être converti en &#39; type2 &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords: BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: efa6fcd4d996fb3277cc4cac2af16a86a2d65977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>Valeur de type &#39; type1 &#39; ne peut pas être converti en &#39; type2 &#39;
Valeur de type 'type1' ne peut pas être convertie en 'type2'. Vous pouvez utiliser la propriété 'Value' pour obtenir la valeur de chaîne du premier élément de '\<parentElement >'.  
  
 Une tentative de conversion implicite d’un littéral XML vers un type spécifique a été effectuée. Le littéral XML ne peut pas être implicitement converti vers le type spécifié.  
  
 **ID d’erreur :** BC31194  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Utilisez la propriété `Value` du littéral XML pour faire référence à sa valeur comme une `String`. Utilisez la fonction `CType` , une autre fonction de conversion de type, ou la classe <xref:System.Convert> pour effectuer un cast de la valeur vers le type spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Convert>  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
