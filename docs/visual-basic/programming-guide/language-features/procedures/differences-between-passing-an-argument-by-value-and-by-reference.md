---
title: "Differences Between Passing an Argument By Value and By Reference (Visual Basic) | Microsoft Docs"
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
  - "ByRef keyword, passing arguments by reference"
  - "Visual Basic code, procedures"
  - "procedures, passing arguments"
  - "ByVal keyword, passing arguments by value"
  - "arguments [Visual Basic], passing by value or by reference"
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Differences Between Passing an Argument By Value and By Reference (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Lorsque vous passez un ou plusieurs arguments à une procédure, chaque argument correspond à un élément de programmation sous\-jacent dans le code appelant.  Vous pouvez passer la valeur de cet élément sous\-jacent ou une référence à celui\-ci.  Ce concept porte le nom de *mécanisme de passage*.  
  
## Passage par valeur  
 Vous passez un argument *par valeur* en spécifiant le mot clé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) pour le paramètre correspondant dans la définition de la procédure.  Lorsque vous utilisez ce mécanisme de passage, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copie la valeur de l'élément de programmation sous\-jacent dans une variable locale de la procédure.  Le code de la procédure n'a pas accès à l'élément sous\-jacent dans le code appelant.  
  
## Passage par référence  
 Vous passez un argument *par référence* en spécifiant le mot clé [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) pour le paramètre correspondant dans la définition de la procédure.  Lorsque vous utilisez ce mécanisme de passage, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit à la procédure une référence directe à l'élément de programmation sous\-jacent figurant dans le code appelant.  
  
## Mécanisme de passage et type d'élément  
 Le choix de mécanisme de passage est différent de la classification du type d'élément sous\-jacent.  Le passage par valeur ou par référence fait référence à ce que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit au code de la procédure.  Un type valeur ou un type référence fait référence à la manière dont un élément de programmation est stocké dans la mémoire.  
  
 Toutefois, le mécanisme de passage et le type d'élément sont étroitement liés.  La valeur d'un type référence est un pointeur vers les données situées ailleurs dans la mémoire.  Cela signifie que lorsque vous passez un type référence par valeur, le code de la procédure a un pointeur vers les données de l'élément sous\-jacent, bien qu'il ne puisse pas accéder à l'élément sous\-jacent lui\-même.  Par exemple, si l'élément est une variable tableau, le code de la procédure n'a pas accès à la variable elle\-même, mais il peut accéder aux membres du tableau.  
  
## Possibilité de modifier  
 Lorsque vous passez un élément non modifiable en tant qu'argument, la procédure ne peut jamais le modifier dans le code appelant, qu'il soit passé `ByVal` ou `ByRef`.  
  
 Dans le cas d'un élément modifiable, le tableau suivant résume l'interaction entre le type de l'élément et le mécanisme de passage.  
  
|Type d'élément|Passé `ByVal`|Passé `ByRef`|  
|--------------------|-------------------|-------------------|  
|Type valeur \(ne contient qu'une valeur\)|La procédure ne peut pas modifier la variable ni l'un de ses membres.|La procédure peut modifier la variable et ses membres.|  
|Type référence \(contient un pointeur vers une instance de classe ou de structure\)|La procédure ne peut pas changer la variable, mais peut modifier les membres de l'instance qu'elle désigne.|La procédure peut changer la variable et les membres de l'instance qu'elle désigne.|  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)