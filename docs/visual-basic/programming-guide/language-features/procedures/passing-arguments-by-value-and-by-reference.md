---
title: "Passing Arguments by Value and by Reference (Visual Basic) | Microsoft Docs"
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
  - "passing arguments, by value or by reference"
  - "ByVal keyword, passing arguments by value"
  - "arguments [Visual Basic], passing by value or by reference"
  - "argument passing, by value or by reference"
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Passing Arguments by Value and by Reference (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

En [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], vous pouvez passer un argument à une procédure *par valeur* ou *par référence*.  Cette opération est appelée *mécanisme de passage* et détermine si la procédure peut modifier l'élément de programmation sous\-jacent à l'argument dans le code appelant.  La déclaration de procédure détermine le mécanisme de passage pour chaque paramètre en spécifiant le mot clé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
## Distinctions  
 Lorsque vous passez un argument à une procédure, informez\-vous des diverses distinctions qui ont une interaction entre elles :  
  
-   L'élément de programmation sous\-jacent est\-il modifiable ou non modifiable ?  
  
-   L'argument lui\-même est\-il modifiable ou non modifiable ?  
  
-   L'argument est\-il passé par valeur ou par référence ?  
  
-   Le type de données d'argument est\-il un type valeur ou un type référence ?  
  
 Pour plus d'informations, consultez [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md) et [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## Choix du mécanisme de passage  
 Vous devez choisir avec soin le mécanisme de passage pour chaque argument.  
  
-   **Protection**.  Lors du choix d'un mécanisme de passage, le critère le plus important est la fréquence à laquelle les variables d'appel doivent changer.  Le passage d'un argument par `ByRef` permet à la procédure de retourner une valeur au code appelant via cet argument.  Le passage d'un argument par `ByVal` permet d'empêcher une variable d'être modifiée par la procédure.  
  
-   **Performances**.  Bien que le mécanisme de passage puisse affecter les performances de votre code, la différence est généralement insignifiante.  La seule exception à cette règle est le passage d'un type valeur par `ByVal`.  Dans ce cas, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copie tout le contenu des données de l'argument.  Par conséquent, dans le cas d'un type valeur de grande taille tel qu'une structure, il peut être préférable d'effectuer un passage `ByRef`.  
  
     Pour les types référence, seul le pointeur vers les données est copié \(quatre octets sur les plateformes 32 bits, huit octets sur les plateformes 64 bits\).  Par conséquent, vous pouvez passer des arguments de type `String` ou `Object` par valeur sans nuire aux performances.  
  
## Détermination du mécanisme de passage  
 La déclaration de procédure spécifie le mécanisme de passage pour chaque paramètre.  Le code appelant ne peut pas substituer un mécanisme d' `ByVal` .  
  
 Si un paramètre est déclaré avec `ByRef`, le code appelant peut forcer le mécanisme à `ByVal` en plaçant le nom de l'argument entre parenthèses dans l'appel.  Pour plus d’informations, consultez [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md).  
  
 Le comportement par défaut en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] consiste à passer les arguments par valeur.  
  
## Quand passer un argument par valeur  
  
-   Si l'élément de code appelant sous\-jacent à l'argument est un élément non modifiable, déclarez le paramètre [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) correspondant.  Aucun code ne peut modifier la valeur d'un élément non modifiable.  
  
-   Si l'élément sous\-jacent est modifiable, et si vous ne souhaitez pas que la procédure puisse modifier sa valeur, déclarez le paramètre `ByVal`.  Seul le code appelant peut modifier la valeur d'un élément modifiable passée par valeur.  
  
## Quand passer un argument par référence  
  
-   Si la procédure nécessite véritablement que l'élément sous\-jacent dans le code appelant soit modifié, déclarez le paramètre [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) correspondant.  
  
-   Si l'exécution correcte du code dépend de la procédure modifiant l'élément sous\-jacent dans le code appelant, déclarez le paramètre `ByRef`.  Si vous le passez par valeur ou si le code appelant substitue le mécanisme de passage `ByRef` en mettant l'argument entre parenthèses, l'appel de procédure peut produire des résultats inattendus.  
  
## Exemple  
  
### Description  
 L'exemple suivant indique quand les arguments doivent être passés par valeur ou par référence.  La procédure `Calculate` contient à la fois les paramètres `ByVal` et `ByRef`.  À partir d'un taux d'intérêt, `rate`, et d'une somme d'argent, `debt`, la tâche de la procédure consiste à calculer une nouvelle valeur pour `debt` qui est le résultat de l'application du taux d'intérêt à la valeur d'origine de `debt`.  Étant donné que `debt` est un paramètre `ByRef`, le nouveau total est représenté dans la valeur de l'argument du code appelant qui correspond à `debt`.  `rate` est un paramètre `ByVal` car `Calculate` ne doit pas modifier sa valeur.  
  
### Code  
 [!code-vb[VbVbcnProcedures#74](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)