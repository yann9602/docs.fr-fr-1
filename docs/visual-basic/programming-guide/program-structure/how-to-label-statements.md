---
title: "How to: Label Statements (Visual Basic) | Microsoft Docs"
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
  - "colons (:)"
  - "statements [Visual Basic], labels"
  - ": separator character"
  - "Visual Basic code, labeling statements"
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Label Statements (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les blocs d'instructions sont composés de lignes de code délimitées par le signe deux\-points \(:\).  Les lignes de code précédées d'une chaîne ou d'un entier les identifiant sont dites *étiquetées*.  Les étiquettes d'instruction sont utilisées pour marquer une ligne de code afin de l'identifier pour être utilisée avec des instructions telles que `On Error Goto`.  
  
 Les étiquettes peuvent être l'un ou l'autre de Visual Basic valide identificateurs comme celles des éléments de programmation élément\-ou les littéraux entiers.  Une étiquette doit apparaître au début d'une ligne de code source et doit être suivie par le signe deux\-points \(:\), qu'elle soit ou non suivie par une instruction sur la même ligne.  
  
 Le compilateur identifie les étiquettes en vérifiant si le début de la ligne correspond à un identificateur déjà défini.  Si ce n'est pas le cas, le compilateur suppose que c'est une étiquette.  
  
 Les étiquettes possèdent leur propre espace de déclaration et n'interfèrent en rien avec d'autres identificateurs.  La portée d'une étiquette est le corps de la méthode.  La déclaration d'étiquette est prioritaire dans une situation ambiguë.  
  
> [!NOTE]
>  Les étiquettes peuvent être utilisées uniquement sur des instructions exécutables à l'intérieur de méthodes.  
  
### Pour étiqueter une ligne de code.  
  
-   Placez un identificateur, suivi par le signe deux\-points \(:\), au début de la ligne du code source.  
  
     Par exemple, les lignes de code suivantes sont étiquetées respectivement par `Jump` et `120` :  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## Voir aussi  
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)