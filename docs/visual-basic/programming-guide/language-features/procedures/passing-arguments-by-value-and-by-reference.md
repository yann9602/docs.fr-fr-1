---
title: "Passage d’un argument par valeur et par référence (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 752c0c8e90cafe457cbd5d684bc984a1ea4632ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Passage d’un argument par valeur et par référence (Visual Basic)
Dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], vous pouvez passer un argument à une procédure *par valeur* ou *par référence*. Il s’agit du *mécanisme de passage*, et détermine si la procédure peut modifier l’élément de programmation sous-jacent à l’argument dans le code appelant. La déclaration de procédure détermine le mécanisme de passage pour chaque paramètre en spécifiant le [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) (mot clé).  
  
## <a name="distinctions"></a>Distinctions  
 Lorsque vous passez un argument à une procédure, tenez compte des diverses distinctions qui interagissent entre eux :  
  
-   Si l’élément de programmation sous-jacent est modifiable ou non modifiable  
  
-   Si l’argument lui-même est modifiable ou non modifiable  
  
-   Si l’argument est passé par valeur ou par référence  
  
-   Si le type de données d’argument est un type valeur ou un type référence  
  
 Pour plus d’informations, consultez [les différences entre modifiables et non modifiables Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) et [les différences entre en passant un Argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Choix du mécanisme de passage  
 Vous devez choisir le mécanisme de passage avec soin pour chaque argument.  
  
-   **Protection**. Dans le choix entre les deux mécanismes de transfert, le critère le plus important est l’exposition de l’appel de variables à modifier. L’avantage de passage d’un argument `ByRef` est que la procédure peut retourner une valeur au code appelant via cet argument. L’avantage de passage d’un argument `ByVal` permet d’empêcher une variable d’être modifiée par la procédure.  
  
-   **Performances**. Bien que le mécanisme de passage peut affecter les performances de votre code, la différence est généralement insignifiante. Une exception à cela est un type de valeur passé `ByVal`. Dans ce cas, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] copie le contenu de la totalité des données de l’argument. Par conséquent, pour un type de valeur élevée comme une structure, il peut être plus efficace de passer `ByRef`.  
  
     Pour les types référence, seul le pointeur vers les données est copié (quatre octets sur les plateformes 32 bits, huit octets sur les plateformes 64 bits). Par conséquent, vous pouvez passer des arguments de type `String` ou `Object` par valeur sans nuire aux performances.  
  
## <a name="determination-of-the-passing-mechanism"></a>Détermination du mécanisme de passage  
 La déclaration de procédure spécifie le mécanisme de passage pour chaque paramètre. Le code appelant ne peut pas remplacer un `ByVal` mécanisme.  
  
 Si un paramètre est déclaré avec `ByRef`, le code appelant peut forcer le mécanisme à `ByVal` en mettant le nom de l’argument entre parenthèses dans l’appel. Pour plus d’informations, consultez [Comment : forcer un Argument à passer par valeur](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 La valeur par défaut dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] consiste à passer des arguments par valeur.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Quand passer un Argument par valeur  
  
-   Si l’élément de code appelant sous-jacent à l’argument est un élément non modifiable, déclarez le paramètre correspondant [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Aucun code ne peut modifier la valeur d’un élément non modifiable.  
  
-   Si l’élément sous-jacent est modifiable, mais vous ne souhaitez pas que la procédure pour être en mesure de modifier sa valeur, déclarez le paramètre `ByVal`. Uniquement le code appelant peut modifier la valeur d’un élément modifiable passé par valeur.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Quand passer un Argument par référence  
  
-   Si la procédure authentique besoin de modifier l’élément sous-jacent dans le code appelant, déclarez le paramètre correspondant [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
-   Si l’exécution correcte du code dépend de la procédure de modification de l’élément sous-jacent dans le code appelant, déclarez le paramètre `ByRef`. Si vous le passez par valeur ou si le code appelant substitue le `ByRef` mécanisme de passage en mettant l’argument entre parenthèses, l’appel de procédure peut produire des résultats inattendus.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant illustre quand passer des arguments par valeur et les passer par référence. Procédure `Calculate` possède à la fois un `ByVal` et un `ByRef` paramètre. Étant donné un taux d’intérêt, `rate`et une somme d’argent, `debt`, la tâche de la procédure consiste à calculer une nouvelle valeur pour `debt` qui est le résultat de l’application le taux d’intérêt à la valeur d’origine de `debt`. Étant donné que `debt` est un `ByRef` paramètre, le nouveau total est représenté dans la valeur de l’argument dans le code appelant qui correspond à `debt`. Paramètre `rate` est un `ByVal` paramètre car `Calculate` ne devez pas modifier sa valeur.  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)  
 [Guide pratique : modifier la valeur d’un argument de la procédure](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Guide pratique : protéger un argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Guide pratique : forcer le passage d’un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)  
 [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
