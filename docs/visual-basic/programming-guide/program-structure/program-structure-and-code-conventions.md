---
title: "Structure de programme et conventions de codage (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "conventions de codage"
  - "code Visual Basic, conventions de codage"
  - "conventions de codage, Visual Basic"
  - "programmes, structure"
  - "structure de programme"
  - "conventions d’affectation de noms, Visual Basic"
  - "meilleures pratiques, conventions de codage"
  - "conventions, codage Visual Basic"
  - "code Visual Basic"
  - "programmer, conventions de codage Visual Basic"
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Structure de programme et conventions de codage (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette section présente la structure du programme [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] standard, fournit un programme [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] simple, « Hello, World », et décrit les conventions de code [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Les conventions de code sont des suggestions qui reposent non pas sur la logique d'un programme mais sur sa structure et son aspect physiques.  Le respect de ces conventions facilite la lecture, la compréhension et la maintenance du code.  Les conventions de code incluent notamment les éléments suivants :  
  
-   formats normalisés d'étiquetage et de commentaire du code ;  
  
-   indications relatives à l'espacement, au format et à la mise en retrait du code ;  
  
-   conventions d'affectation de noms à des objets, variables et procédures.  
  
 Les rubriques suivantes présentent un ensemble d'instructions de programmation pour les programmes [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], ainsi que des exemples d'utilisation appropriée.  
  
## Dans cette section  
 [Structure of a Visual Basic Program](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 Propose une vue d'ensemble des éléments qui composent un programme [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 Décrit la procédure qui sert de point de départ et de contrôle général de l'application.  
  
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 Explique comment référencer les objets dans d'autres assemblys.  
  
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 Explique comment les espaces de noms organisent les objets dans les assemblys.  
  
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 Inclut des indications générales pour les procédures d'affectation de noms, les constantes, variables, arguments et objets.  
  
 [Visual Basic Coding Conventions](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 Examine les instructions utilisées pour le développement des exemples de cette documentation.  
  
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Décrit comment compiler de façon sélective des blocs de code particuliers tout en demandant au compilateur d'en ignorer d'autres.  
  
 [Procédure : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 Indique comment répartir les instructions longues sur plusieurs lignes et associer des instructions courtes sur une même ligne.  
  
 [How to: Collapse and Hide Sections of Code](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 Indique comment réduire et masquer des sections de code dans l'éditeur de code [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 Illustre comment marquer une ligne de code afin de l'identifier pour être utilisée avec des instructions telles que `On Error Goto`.  
  
 [Special Characters in Code](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 Montre comment et où utiliser des caractères non numériques et non alphabétiques.  
  
 [Comments in Code](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 Indique comment ajouter des commentaires descriptifs à votre code.  
  
 [Keywords as Element Names in Code](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 Montre comment utiliser les crochets \(`[]`\) pour délimiter les noms de variables qui sont également des mots clés [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 Décrit différentes méthodes pour faire référence aux éléments d'un programme [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [Visual Basic Limitations](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 Traite de la suppression des limites de codage connues en [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## Rubriques connexes  
 [Typographic and Code Conventions](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 Propose des conventions de codage standard pour [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [Écriture de code](/visual-studio/ide/writing-code-in-the-code-and-text-editor)  
 Décrit les fonctionnalités qui facilitent l'écriture de votre code et sa gestion.