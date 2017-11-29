---
title: "Utilisation efficace des types de données (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e13a1d61aacb06eb336c39aab969847127dfc67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Utilisation efficace des types de données (Visual Basic)
Les variables non déclarées et les variables déclarées sans type de données sont voient attribuer le `Object` type de données. Il est ainsi facile d’écrire rapidement des programmes, mais il peut les rendre à s’exécuter plus lentement.  
  
## <a name="strong-typing"></a>Typage fort  
 Spécifier les types de données pour toutes les variables est appelé *typage fort*. À l’aide d’un typage fort présente plusieurs avantages :  
  
-   Il permet la prise en charge IntelliSense pour vos variables. Cela vous permet de vous permet de voir leurs propriétés et autres membres que vous entrez dans le code.  
  
-   Il bénéficie de la vérification du type du compilateur. Il intercepte les instructions qui peuvent échouer au moment de l’exécution en raison d’erreurs de dépassement de capacité. Il intercepte également les appels aux méthodes sur des objets qui ne les prennent pas en charge.  
  
-   Il en résulte une exécution plus rapide de votre code.  
  
## <a name="most-efficient-data-types"></a>Types de données plus efficaces.  
 Pour les variables qui ne contiennent jamais de fractions, les types de données intégraux sont plus efficaces que les types intégraux. Dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], `Integer` et `UInteger` sont les types numériques la plus efficaces.  
  
 Pour les nombres fractionnaires, `Double` est le type de données la plus efficace, car les processeurs sur les plateformes actuelles exécutent des opérations à virgule flottante à double précision. Toutefois, les opérations avec `Double` ne sont pas aussi rapides qu’avec les types intégraux, tels que `Integer`.  
  
## <a name="specifying-data-type"></a>Spécification du Type de données  
 Utilisez le [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pour déclarer une variable d’un type spécifique. Vous pouvez spécifier simultanément son niveau d’accès à l’aide de la [Public](../../../../visual-basic/language-reference/modifiers/public.md), [protégé](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), ou [privé](../../../../visual-basic/language-reference/modifiers/private.md) (mot clé), comme dans le exemple suivant.  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>Conversion de caractères  
 Le `AscW` et `ChrW` fonctions opèrent en Unicode. Vous devez les utiliser de préférence à `Asc` et `Chr`, qui doit convertir vers et depuis Unicode.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Types de données numériques](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Utilisation de la fonctionnalité IntelliSense](/visualstudio/ide/using-intellisense)
