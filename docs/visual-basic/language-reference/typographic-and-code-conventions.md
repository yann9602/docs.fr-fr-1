---
title: "Typographic and Code Conventions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "coding conventions, Visual Basic"
  - "best practices, coding conventions"
  - "conventions, Visual Basic coding"
  - "typographic conventions"
  - "document conventions"
  - "conventions, documentation"
  - "Visual Basic code, conventions"
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typographic and Code Conventions (Visual Basic)
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

La documentation Visual Basic utilise les conventions typographiques et de code suivantes.  
  
## Conventions typographiques  
  
|Exemple|Description|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Les mots clés spécifiques au langage et les membres du runtime ont des lettres majuscules initiales et un format similaire à celui montré dans cet exemple.|  
|SmallProject, ButtonCollection|Les mots et les phrases que vous êtes invité à taper ont un format similaire à celui montré dans cet exemple.|  
|[Module Statement](../../visual-basic/language-reference/statements/module-statement.md)|Les liens que vous pouvez activer pour accéder à une autre page d'aide ont un format similaire à celui montré dans cet exemple.|  
|*objet*, *Nomvariable*, `argumentList`|Les espaces réservés pour les informations que vous fournissez ont un format similaire à celui montré dans cet exemple.|  
|\[ Shadows \], \[ *listeExpressions* \]|Dans la syntaxe, les éléments entre crochets sont facultatifs.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|Dans la syntaxe, lorsque vous devez faire un choix entre deux ou plusieurs éléments, les éléments sont mis entre accolades et séparés par des barres verticales.<br /><br /> Vous devez sélectionner un seul de ces éléments.|  
|\[ `Protected` &#124; `Friend` \]|Dans la syntaxe, lorsque vous avez la possibilité de choisir entre deux ou plusieurs éléments, les éléments sont placés entre crochets et séparés par des barres verticales.<br /><br /> Vous pouvez sélectionner toute combinaison des éléments, ou aucun élément.|  
|\[{ `ByVal` &#124; `ByRef` }\]|Dans la syntaxe, lorsque vous ne pouvez sélectionner qu'un élément, mais que vous pouvez également omettre complètement les éléments, les éléments sont placés entre crochets entourés d'accolades et séparés par des barres verticales.|  
|*NomMembre* 1, *NomMembre*2, *NomMembre*3|Les instances multiples du même espace réservé sont différenciées par les indices, comme indiqué dans l'exemple.|  
|*NomMembre1*<br /><br /> ...<br /><br /> *NomMembreN*|Dans la syntaxe, les points de suspension \(...\) indiquent un nombre indéfini d'éléments du type précédant immédiatement ces points de suspension.<br /><br /> Dans le code, les points de suspension indiquent que du code a été omis par souci de clarté.|  
|ESC, ENTER|Les noms de touches et les combinaison de touches sur le clavier qui apparaissent tout en majuscules.|  
|ALT\+F1|Lorsque des signes plus \(\+\) apparaissent entre les noms des touches, vous devez maintenir une touche enfoncée tout en appuyant sur l'autre.  Par exemple, ALT\+F1 signifie maintenir la touche ALT enfoncée, tout en appuyant sur la touche F1.|  
  
## Conventions de code  
  
|Exemple|Description|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Les exemples de code apparaissent dans une police à pas fixe et ont le format montré dans cet exemple.|  
|L'instruction précédente affecte à `sampleString` la valeur « Hello, world\! ».|Les éléments de code contenus dans le texte explicatif apparaissent dans une police à pas fixe, comme le montre cet exemple.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Une apostrophe \('\) ou le mot clé REM introduisent des commentaires de code.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Un espace suivi d'un trait de soulignement \( \_\) à la fin d'une ligne indique que l'instruction continue sur la ligne suivante.|  
  
## Voir aussi  
 [Visual Basic Language Reference](../../visual-basic/language-reference/index.md)   
 [Mots clés](../../visual-basic/language-reference/keywords/index.md)   
 [Visual Basic Runtime Library Members](../../visual-basic/language-reference/runtime-library-members.md)   
 [Visual Basic Naming Conventions](../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Procédure : diviser et combiner des instructions dans le code](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)   
 [Comments in Code](../../visual-basic/programming-guide/program-structure/comments-in-code.md)