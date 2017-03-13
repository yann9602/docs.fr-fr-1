---
title: "Proc&#233;dure&#160;: diviser et combiner des instructions dans le code (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb._"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "signes deux-points (:)"
  - "continuation de ligne"
  - "_, caractère de continuation de ligne"
  - ":, caractère de séparation de ligne"
  - "code Visual Basic, sauts de ligne dans"
  - "code Visual Basic, sauts de ligne"
  - "code Visual Basic, continuation de ligne"
  - "longues lignes de code"
  - "marque de fin de ligne"
  - "séquence de continuation de ligne"
  - "traits de soulignement, dans le code"
  - "instructions [Visual Basic], continuation de ligne dans"
  - "sauts de ligne, dans le code"
  - "caractère de continuation de ligne"
  - "code Visual Basic, continuation de ligne dans"
  - "instructions [Visual Basic], sauts de ligne dans"
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Proc&#233;dure&#160;: diviser et combiner des instructions dans le code (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Lorsque vous écrivez votre code, vous pouvez être amené à créer de longues instructions qui vous imposent un défilement horizontal dans l'éditeur de code.  Bien que cela n'affecte pas la façon dont votre code s'exécute, il rend difficile pour vous ou toute personne d'autre lire le code qu'il apparaît sur l'écran.  Il est donc fortement recommandé de répartir cette instruction longue sur plusieurs lignes.  
  
### Pour couper une même instruction en plusieurs lignes  
  
-   À l'endroit auquel vous voulez couper la ligne, utilisez le caractère de continuation de ligne, qui est un trait de soulignement \(`_`\).  Le trait de soulignement doit être immédiatement précédé d'un espace et être immédiatement suivi par un terminateur de ligne \(retour chariot\).  
  
    > [!NOTE]
    >  Dans certains cas, si vous omettez le caractère de continuation de ligne, le compilateur Visual Basic continuera implicitement l'instruction sur la ligne de code.  Pour une liste d'éléments de syntaxe pour lesquels vous pouvez omettre le caractère de continuation de ligne, consultez « continuation de ligne implicite » dans [Statements](../../../visual-basic/programming-guide/language-features/statements.md).  
  
     Dans l'exemple ci\-dessous, l'instruction est répartie sur quatre lignes à l'aide de caractères de continuation terminant toutes les lignes à l'exception de la dernière.  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     L'utilisation de cette séquence simplifie la lecture de votre code, tant à l'écran que sur papier.  
  
     Le caractère de continuation de ligne doit être le dernier caractère dans une ligne.  Vous ne pouvez pas le suivi avec tout autre élément sur la même ligne.  
  
     Certaines limitations existent quant à l'endroit où vous pouvez utiliser le caractère de continuation de ligne ; par exemple, vous ne pouvez pas utiliser au milieu d'un nom de l'argument.  Vous pouvez couper une liste d'arguments à l'aide du caractère de continuation de ligne, mais les noms respectifs des arguments doivent rester intacts.  
  
     Vous ne pouvez pas continuer un commentaire à l'aide d'un caractère de continuation de ligne.  Le compilateur ne vérifie pas les caractères dans un commentaire pour l'ordre particulier.  Dans le cas d'un commentaire à répartir sur plusieurs lignes, répétez le symbole de commentaire \(`'`\) sur chaque ligne.  
  
 Bien que définir chaque instruction sur une ligne séparée est la méthode recommandée, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] vous permet également à plusieurs instructions de placer sur la même ligne.  
  
### Pour placer plusieurs instructions sur une même ligne  
  
-   Séparez les instructions par un caractère deux\-points \(`:`\), comme dans l'exemple suivant.  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## Voir aussi  
 [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)