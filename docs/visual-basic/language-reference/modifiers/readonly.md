---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9ca1d2e4eddb3b88073d6fcd46b0de5c627ba809
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Spécifie qu’une variable ou une propriété peut être lues mais ne pas écrite.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="rules"></a>Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser `ReadOnly` seulement au niveau du module. Cela signifie que le contexte de déclaration pour un `ReadOnly` élément doit être une classe, une structure ou un module et ne peut pas être un fichier source, un espace de noms ou une procédure.  
  
-   **Modificateurs combinés.** Vous ne pouvez pas spécifier `ReadOnly` avec `Static` dans la même déclaration.  
  
-   **Affectation d’une valeur.** Code utilisant un `ReadOnly` propriété ne peut pas définir sa valeur. Mais le code qui a accès au stockage sous-jacent peut attribuer ou modifier la valeur à tout moment.  
  
     Vous pouvez affecter une valeur à une `ReadOnly` variable uniquement dans sa déclaration ou dans le constructeur d’une classe ou structure dans laquelle il est défini.  
  
## <a name="when-to-use-a-readonly-variable"></a>Quand utiliser une Variable en lecture seule  
 Il existe des situations dans lesquelles vous ne pouvez pas utiliser un [instruction Const](../../../visual-basic/language-reference/statements/const-statement.md) pour déclarer et assigner une valeur constante. Par exemple, la `Const` instruction ne peut pas accepter le type de données que vous souhaitez affecter, ou vous n’êtes peut-être pas en mesure de calculer la valeur au moment de la compilation avec une expression constante. Vous ne savez pas encore la valeur au moment de la compilation. Dans ce cas, vous pouvez utiliser un `ReadOnly` variable qui doit contenir une valeur constante.  
  
> [!IMPORTANT]
>  Si le type de données de la variable est un type référence, comme un tableau ou une instance de la classe, ses membres peuvent être changés même si la variable elle-même est `ReadOnly`. L'exemple suivant illustre ce comportement.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Lors de l’initialisation, le tableau vers lequel pointe `characterArray()` contient « x », « y » et « z ». Étant donné que la variable `characterArray` est `ReadOnly`, vous ne pouvez pas modifier sa valeur initialisée ; c'est-à-dire, vous ne pouvez attribuer un nouveau tableau à celui-ci. Toutefois, vous pouvez modifier les valeurs d’une ou plusieurs des membres du groupe. Après un appel à la procédure `changeArrayElement`, le tableau vers lequel pointe `characterArray()` contient « x », « M » et « z ».  
  
 Notez que cela est similaire à la déclaration d’un paramètre de procédure à être [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), ce qui empêche la procédure de modification de l’argument d’appel lui-même, mais lui permet de modifier ses membres.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit un `ReadOnly` propriété pour la date à laquelle un employé a été embauché. La classe stocke la valeur de propriété en interne comme un `Private` variable et seul le code à l’intérieur de la classe peut modifier cette valeur. Toutefois, la propriété est `Public`, et tout code qui peut accéder à la classe peut lire la propriété.  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 Le modificateur `ReadOnly` peut être utilisé dans les contextes suivants :  
  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Voir aussi  
 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
