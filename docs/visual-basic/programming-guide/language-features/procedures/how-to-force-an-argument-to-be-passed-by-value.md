---
title: "Comment : forcer un Argument est passé par valeur (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedures, arguments
- procedures, parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures, calling
- arguments [Visual Basic], in parentheses
- procedure arguments, in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: eea3466534f1797170ae4bc72afbcba899929911
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Comment : forcer le passage d’un argument par valeur (Visual Basic)
La déclaration de procédure détermine le mécanisme de passage. Si un paramètre est déclaré [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit passer l’argument correspondant par référence. Cela permet à la procédure modifier la valeur de l’élément de programmation sous-jacent à l’argument dans le code appelant. Si vous souhaitez protéger l’élément sous-jacent contre une telle modification, vous pouvez remplacer le `ByRef` mécanisme de passage de la procédure appeler en mettant le nom de l’argument entre parenthèses. Ces parenthèses sont ajoutent les parenthèses entourant la liste d’arguments de l’appel.  
  
 Le code appelant ne peut pas remplacer un [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mécanisme.  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Pour forcer un argument à passer par valeur  
  
-   Si le paramètre correspondant est déclaré `ByVal` dans la procédure, vous n’avez pas besoin prendre des mesures supplémentaires. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]doit déjà passer l’argument par valeur.  
  
-   Si le paramètre correspondant est déclaré `ByRef` dans la procédure, mettez l’argument entre parenthèses dans l’appel de procédure.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant substitue une `ByRef` déclaration de paramètre. Dans l’appel qui force `ByVal`, notez les deux niveaux de parenthèses.  
  
 [!code-vb[VbVbcnProcedures n °&39;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures numéro&40;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 Lors de la `str` est placée entre parenthèses supplémentaires dans la liste d’arguments, les `setNewString` procédure ne peut pas modifier sa valeur dans le code appelant, et `MsgBox` affiche « Ne peut pas être remplacé si passé ByVal ». Lors de la `str` n’est pas placé entre des parenthèses supplémentaires, la procédure peut le modifier, et `MsgBox` affiche « Il s’agit d’une nouvelle valeur pour l’argument inString. »  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Lorsque vous passez une variable par référence, vous devez utiliser le `ByRef` (mot clé) pour spécifier ce mécanisme.  
  
 La valeur par défaut dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] consiste à passer des arguments par valeur. Toutefois, il est conseillé de comprennent le [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) mot-clé avec chaque paramètre déclaré. Cela rend votre code plus facile à lire.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Si une procédure déclare un paramètre [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), l’exécution correcte du code peut dépendre de la possibilité de modifier l’élément sous-jacent dans le code appelant. Si le code appelant substitue ce mécanisme appelant en mettant l’argument entre parenthèses, ou si elle passe un argument non modifiable, la procédure ne peut pas modifier l’élément sous-jacent. Cela peut produire des résultats inattendus dans le code appelant.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Il existe toujours un risque potentiel en autorisant une procédure modifier la valeur sous-jacente à un argument dans le code appelant. Assurez-vous que cette valeur pour être modifiée et préparez-vous à vérifier la validité avant de l’utiliser.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Comment : passer des Arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)   
 [Passage des Arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)   
 [Différences entre les Arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Différences entre le passage d’un Argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [Comment : modifier la valeur d’un Argument de procédure](./how-to-change-the-value-of-a-procedure-argument.md)   
 [Comment : protéger un Argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Passage des Arguments par Position et par nom](./passing-arguments-by-position-and-by-name.md)   
 [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
