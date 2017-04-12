---
title: "Copie de la valeur du paramètre &quot;ByRef&quot; &quot;&lt;parametername&gt;&quot;dans l’argument correspondant passe du type&quot;&lt;NomType1&gt;&quot; en type&quot;&lt;NomType2&gt;&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
dev_langs:
- VB
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 84574006b2e2ccc669fdd83ebfb6eec06b00f041
ms.lasthandoff: 03/13/2017

---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a>Copie de la valeur du paramètre 'ByRef' '&lt;parametername&gt;'dans l’argument correspondant passe du type'&lt;NomType1&gt;' en type'&lt;NomType2&gt;»
Une procédure est appelée avec un argument qui s’étend au type de paramètre correspondant, et la conversion du paramètre à l’argument est restrictive.  
  
 Quand vous définissez une classe ou une structure, vous pouvez définir un ou plusieurs opérateurs de conversion pour convertir le type de la classe ou de la structure en d’autres types. Vous pouvez également définir des opérateurs de conversion inverse pour convertir ces autres types vers le type de votre classe ou de votre structure. Lorsque vous utilisez votre type de classe ou de structure dans un appel de procédure, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] peut utiliser ces opérateurs de conversion pour convertir le type d’un argument pour le type de son paramètre correspondant.  
  
 Si vous passez l’argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copie parfois sa valeur dans une variable locale de la procédure au lieu de passer une référence. Dans ce cas, la procédure retourne [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit copier la valeur de variable locale dans l’argument dans le code appelant.  
  
 Si une valeur d’argument `ByRef` est copiée dans la procédure, et si l’argument et le paramètre sont du même type, aucune conversion n’est nécessaire. Mais si les types sont différents, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit convertir dans les deux sens. Si un des types est votre type de classe ou structure, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit le convertir vers et à partir de l’autre type. Si une de ces conversions est étendue, la conversion inverse peut être restrictive.  
  
 **ID d’erreur :** BC32053  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si possible, utilisez un argument d’appel du même type que le paramètre de procédure, par conséquent, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne doit pas effectuer de conversion.  
  
-   Si vous avez besoin d’appeler la procédure avec un argument de type différent du type de paramètre, mais n’avez pas besoin de retourner une valeur dans l’argument d’appel, de définir le paramètre pour être [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) au lieu de `ByRef`.  
  
-   Si vous devez retourner une valeur dans l’argument d’appel, définir l’opérateur de conversion inverse [Widening](../../../visual-basic/language-reference/modifiers/widening.md), si possible.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Arguments et paramètres de procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passage des Arguments par valeur et par référence](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Comment : définir un opérateur](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [Comment : définir un opérateur de Conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Conversions de type dans Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
