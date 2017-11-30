---
title: "Comment : forcer le passage d’un argument par valeur (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fdb2df7e114f49c23db9f5b322ca9dd32135ac88
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Comment : forcer le passage d’un argument par valeur (Visual Basic)
La déclaration de procédure détermine le mécanisme de passage. Si un paramètre est déclaré [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doit passer l’argument correspondant par référence. Cela permet à la procédure modifier la valeur de l’élément de programmation sous-jacent à l’argument dans le code appelant. Si vous souhaitez protéger l’élément sous-jacent contre une telle modification, vous pouvez remplacer le `ByRef` mécanisme de passage de la procédure appeler en mettant le nom de l’argument entre parenthèses. Ces parenthèses sont ajoutent les parenthèses entourant la liste d’arguments dans l’appel.  
  
 Le code appelant ne peut pas remplacer un [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mécanisme.  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Pour forcer un argument à passer par valeur  
  
-   Si le paramètre correspondant est déclaré `ByVal` dans la procédure, vous n’avez pas besoin de prendre des mesures supplémentaires. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]doit déjà passer l’argument par valeur.  
  
-   Si le paramètre correspondant est déclaré `ByRef` dans la procédure, mettez l’argument entre parenthèses dans l’appel de procédure.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant substitue un `ByRef` déclaration de paramètre. Dans l’appel qui force `ByVal`, notez les deux niveaux de parenthèses.  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 Lorsque `str` est placée entre parenthèses supplémentaires dans la liste d’arguments, le `setNewString` procédure ne peut pas modifier sa valeur dans le code appelant, et `MsgBox` affiche « Ne peut pas être remplacé si passé ByVal ». Lorsque `str` n’est pas placé entre parenthèses supplémentaires, la procédure peut le modifier, et `MsgBox` affiche « Il s’agit d’une nouvelle valeur pour l’argument inString. »  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Lorsque vous passez une variable par référence, vous devez utiliser le `ByRef` mot clé pour spécifier ce mécanisme.  
  
 La valeur par défaut dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] consiste à passer des arguments par valeur. Toutefois, il est conseillé pour inclure la [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) mot clé with chaque paramètre déclaré. Cela rend votre code plus facile à lire.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Si une procédure déclare un paramètre [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), l’exécution correcte du code peut dépendre de la possibilité de modifier l’élément sous-jacent dans le code appelant. Si le code appelant substitue ce mécanisme appelant en mettant l’argument entre parenthèses, ou si elle passe un argument non modifiable, la procédure ne peut pas modifier l’élément sous-jacent. Cela peut produire des résultats inattendus dans le code appelant.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Il est toujours un risque potentiel pour autoriser une procédure modifier la valeur sous-jacente à un argument dans le code appelant. Assurez-vous que cette valeur pour être modifiée et préparez-vous à vérifier la validité avant de l’utiliser.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)  
 [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)  
 [Différences entre les arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Différences entre le passage d’un argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Guide pratique : modifier la valeur d’un argument de la procédure](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Guide pratique : protéger un argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)  
 [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
