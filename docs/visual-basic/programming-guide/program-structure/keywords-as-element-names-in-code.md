---
title: "Keywords as Element Names in Code (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, naming conventions"
  - "keywords [Visual Basic], in code"
  - "name conflicts"
  - "element names, in code"
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Keywords as Element Names in Code (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Tout élément de programme — tel qu'une variable, une classe ou un membre — peut avoir le même nom qu'un mot clé restreint.  Vous pouvez, par exemple, créer une variable appelée `Loop`.  Cependant, pour faire référence à votre version de variable — qui porte le même nom que le mot clé `Loop` restreint — vous devez soit la faire précéder d'une chaîne de qualification complète, soit la placer entre crochets \(`[ ]`\), comme le montrent les exemples suivants :  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 Si vous ne procédez pas de l'une de ces façons, Visual Basic part du principe que le mot clé `Loop` intrinsèque est utilisé et il génère une erreur, comme ci\-dessous :  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Vous pouvez utiliser des crochets lorsque vous faites référence à des formulaires et des contrôles, et lorsque vous déclarez une variable ou définissez une procédure ayant le même nom qu'un mot clé restreint.  Il peut être assez facile d'oublier de qualifier des noms ou d'inclure des crochets, et ainsi d'introduire des erreurs dans votre code et de le rendre difficile à lire.  C'est la raison pour laquelle nous vous recommandons de ne pas utiliser de mots clés restreints comme noms d'éléments de programme.  Cependant, si une version ultérieure de Visual Basic définit un nouveau mot clé qui entre en conflit avec un nom de formulaire ou de contrôle existant, vous pouvez utiliser cette technique lorsque vous effectuez une mise à jour de votre code afin de pouvoir utiliser la nouvelle version.  
  
> [!NOTE]
>  Votre programme peut également contenir des noms d'éléments fournis par d'autres assemblys référencés.  Si ces noms entrent en conflit avec des mots clés restreints, le fait de les placer entre crochets force Visual Basic à les interpréter comme vos éléments définis.  
  
## Voir aussi  
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)