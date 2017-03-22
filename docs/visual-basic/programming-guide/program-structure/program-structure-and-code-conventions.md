---
title: Structure de programme et Conventions de codage (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions, Visual Basic
- programs, structure
- program structure
- naming conventions, Visual Basic
- best practices, coding conventions
- conventions, Visual Basic coding
- Visual Basic code
- programming, Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: 21
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cd25d99d74bf1e4d416c9da63758f6ad04027258
ms.lasthandoff: 03/13/2017

---
# <a name="program-structure-and-code-conventions-visual-basic"></a>Structure de programme et conventions de codage (Visual Basic)
Cette section présente le type [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] structure du programme, fournit un simple [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de programme, « Hello, World » et décrit [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] conventions de code. Conventions de code sont des suggestions qui reposent pas sur la logique d’un programme mais sur sa structure physique et son apparence. Suivant les rend votre code plus facile à lire, à comprendre et à gérer. Conventions de code incluent, entre autres :  
  
-   Formats normalisés d’étiquetage et de commentaire de code.  
  
-   Instructions pour l’espacement, la mise en forme et la mise en retrait du code.  
  
-   Conventions de dénomination des objets, des variables et des procédures.  
  
 Les rubriques suivantes présentent un ensemble d’instructions pour de programmation [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programmes, ainsi que des exemples d’utilisation appropriée.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Structure d’un programme Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 Fournit une vue d’ensemble des éléments qui composent un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programme.  
  
 [Procédure Main dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 Décrit la procédure qui sert le début du point et de contrôle général pour votre application.  
  
 [Références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 Explique comment référencer des objets dans d’autres assemblys.  
  
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 Décrit comment les espaces de noms organisent les objets dans les assemblys.  
  
 [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 Comprend des instructions générales pour les noms des procédures, des constantes, variables, arguments et objets.  
  
 [Conventions de codage Visual Basic](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 Examine les instructions utilisées pour développer les exemples de cette documentation.  
  
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Décrit comment compiler sélectivement des blocs de code spécifiques tout en indiquant au compilateur d’ignorer d’autres.  
  
 [Guide pratique : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 Indique comment répartir les instructions longues sur plusieurs lignes et associer des instructions courtes sur une seule ligne.  
  
 [Guide pratique : réduire et masquer des sections de code](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 Indique comment réduire et masquer des sections de code dans la [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] éditeur de code.  
  
 [Guide pratique : étiqueter des instructions](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 Montre comment marquer une ligne de code afin d’identifier pour une utilisation avec des instructions telles que `On Error Goto`.  
  
 [Caractères spéciaux dans le code](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 Explique comment et où utiliser des caractères non numériques et non alphabétiques.  
  
 [Commentaires dans le code](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 Explique comment ajouter des commentaires descriptifs à votre code.  
  
 [Utilisation des mots clés comme noms d’éléments dans le code](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 Décrit comment utiliser des crochets (`[]`) pour délimiter les noms de variables qui sont également [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] mots clés.  
  
 [Me, My, MyBase et MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 Décrit les différentes méthodes pour faire référence aux éléments d’un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programme.  
  
 [Restrictions liées à Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 Traite de la suppression des limites connues du codage dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Conventions typographiques](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 Fournit les conventions de codage standards pour [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [Écriture de code](https://docs.microsoft.com/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 Décrit les fonctionnalités qui facilitent l’écriture et la gestion de votre code.
