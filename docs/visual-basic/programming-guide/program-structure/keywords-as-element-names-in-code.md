---
title: "Utilisation des mots clés comme noms d'éléments dans le code (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f410a0eaac0dcc034d406a89ed1d01a8f228a583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Utilisation des mots clés comme noms d'éléments dans le code (Visual Basic)
N’importe quel élément de programme, par exemple une variable, une classe ou un membre — peut avoir le même nom qu’un mot clé restreint. Par exemple, vous pouvez créer une variable nommée `Loop`. Toutefois, pour faire référence à votre version de celui-ci, qui a le même nom que la limitée `Loop` (mot clé), vous devez le faire précéder d’une chaîne de qualification complète ou le placer entre crochets (`[ ]`), comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 Si vous ne procédez pas à une de ces, Visual Basic suppose l’utilisation de la fonction intrinsèque `Loop` (mot clé) et génère une erreur, comme dans l’exemple suivant :  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Vous pouvez utiliser des crochets lorsque vous faites référence aux formulaires et contrôles et lors de la déclaration d’une variable ou la définition d’une procédure portant le même nom qu’un mot clé restreint. Il est facile d’oublier de qualifier des noms ou à inclure des crochets et ainsi d’introduire des erreurs dans votre code et rendre plus difficile à lire. Pour cette raison, nous vous conseillons pas mots clés restreints comme noms d’éléments de programme. Toutefois, si une version ultérieure de Visual Basic définit un nouveau mot clé qui entre en conflit avec un nom de contrôle ou un formulaire existant, puis vous pouvez utiliser cette technique lorsque votre code de mise à jour pour fonctionner avec la nouvelle version.  
  
> [!NOTE]
>  Votre programme peut également contenir des noms d’éléments fournis par d’autres assemblys référencés. Si ces noms en conflit avec les mots clés restreints, puis placer les crochets autour d’elles permet à Visual Basic pour les interpréter comme vos éléments définis.  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
