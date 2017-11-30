---
title: Conventions typographiques (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7b6db5c223b0548e308b49a686cff72eaaf8da36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Conventions typographiques (Visual Basic)
Documentation de Visual Basic utilise les conventions de code suivant typographiques.  
  
## <a name="typographic-conventions"></a>Conventions typographiques  
  
|Exemple|Description|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Mots clés spécifiques au langage et les membres du runtime ont des lettres majuscules initiales et sont mises en forme comme illustré dans cet exemple.|  
|**SmallProject**, **ButtonCollection**|Mots et expressions que vous êtes invité à taper sont mis en forme comme illustré dans cet exemple.|  
|[Module (instruction)](../../visual-basic/language-reference/statements/module-statement.md)|Vous pouvez cliquer pour accéder à une autre page d’aide de liens sont mises en forme comme illustré dans cet exemple.|  
|*objet*, *variableName*,`argumentList`|Espaces réservés pour les informations que vous fournissez sont mis en forme comme illustré dans cet exemple.|  
|[Ombres], [ *expressionList* ]|Dans la syntaxe, les éléments facultatifs sont placés entre crochets.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|Dans la syntaxe, lorsque vous devez faire un choix entre deux ou plusieurs éléments, les éléments sont placés entre accolades et séparés par des barres verticales.<br /><br /> Vous devez sélectionner un seul et unique, des éléments.|  
|[ `Protected` &#124; `Friend` ]|Dans la syntaxe, lorsque vous avez la possibilité de choisir entre deux ou plusieurs éléments, les éléments sont placés entre crochets et séparés par des barres verticales.<br /><br /> Vous pouvez sélectionner n’importe quelle combinaison des éléments, ou aucun élément.|  
|[{ `ByVal` &#124; `ByRef` }]|Dans la syntaxe, lorsque vous pouvez sélectionner ne plusieurs éléments, mais vous pouvez également omettre les éléments complètement, les éléments sont placés entre crochets entourés d’accolades et séparés par des barres verticales.|  
|*memberName*1, *memberName*2, *memberName*3|Plusieurs instances du même espace réservé sont différenciées par les indices, comme indiqué dans l’exemple.|  
|*Nom_membre1*<br /><br /> ...<br /><br /> *memberNameN*|Dans la syntaxe, les points de suspension (...) est utilisé pour indiquer un nombre indéfini d’éléments du type immédiatement devant les points de suspension.<br /><br /> Dans le code, les points de suspension qui indiquent code omis par souci de clarté.|  
|ÉCHAP, ENTREZ|Les noms de clés et les séquences de touches du clavier apparaissent dans toutes les lettres majuscules.|  
|ALT + F1|Lorsque le signe plus (+) apparaissent entre les noms de clé, vous devez maintenir une touche enfoncée tout en appuyant sur l’autre. Par exemple, ALT + F1 signifie maintenez la touche ALT enfoncée tout en appuyant sur la touche F1.|  
  
## <a name="code-conventions"></a>Conventions de code  
  
|Exemple|Description|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Exemples de code apparaissent dans une police à espacement fixe et sont mises en forme comme illustré dans cet exemple.|  
|L’instruction précédente définit la valeur de `sampleString` à « Hello, world ! »|Éléments de code dans un texte explicatif apparaissent dans une police à espacement fixe, comme indiqué dans cet exemple.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Commentaires de code introduites par une apostrophe (') ou le mot clé REM.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Un espace suivi par un trait de soulignement (_) à la fin d’une ligne indique que l’instruction continue sur la ligne suivante.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le langage Visual Basic](../../visual-basic/language-reference/index.md)  
 [Mots clés](../../visual-basic/language-reference/keywords/index.md)  
 [Membres de la bibliothèque runtime Visual Basic](../../visual-basic/language-reference/runtime-library-members.md)  
 [Conventions d’affectation de noms de Visual Basic](../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Guide pratique : diviser et combiner des instructions dans le code](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [Commentaires dans le code](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
