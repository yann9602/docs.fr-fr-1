---
title: "ReadOnly (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ReadOnly"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ReadOnly keyword"
  - "variables [Visual Basic], read-only"
  - "ReadOnly property"
  - "properties [Visual Basic], read-only"
  - "read-only variables"
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# ReadOnly (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie qu'une variable ou une propriété peut être lue, mais pas écrite.  
  
## Notes  
  
## Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser `ReadOnly` seulement au niveau du module.  Cela signifie que le contexte de déclaration pour un élément `ReadOnly` doit être une classe, une structure ou un module, et ne peut pas être un fichier source, un espace de noms ou une procédure.  
  
-   **Modificateurs combinés.** Vous ne pouvez pas spécifier `ReadOnly` avec `Static` dans la même déclaration.  
  
-   **Assignation d'une valeur.** Le code utilisant une propriété `ReadOnly` ne peut pas définir sa valeur.  Mais le code qui a accès au stockage sous\-jacent peut assigner ou modifier la valeur n'importe quand.  
  
     Vous pouvez assigner une valeur à une variable `ReadOnly` uniquement dans sa déclaration ou dans le constructeur d'une classe ou d'une structure dans lequel elle est définie.  
  
## Quand utiliser une variable en lecture seule  
 Il y a des situations dans lesquelles vous ne pouvez pas utiliser un [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) pour déclarer et assigner une valeur de constante.  Par exemple, l'instruction `Const` ne pourra peut\-être pas accepter le type de données que vous souhaitez assigner ou vous pouvez ne pas être en mesure de calculer la valeur au moment de la compilation avec une expression constante.  Il est même possible que vous ne connaissiez pas la valeur au moment de la compilation.  Dans ce cas, vous pouvez utiliser une variable `ReadOnly` pour contenir une valeur de constante.  
  
> [!IMPORTANT]
>  Si le type de données de la variable est un type référence, tel qu'un tableau ou une instance de classe, ses membres peuvent être changés même si la variable elle\-même est `ReadOnly`.  L'exemple suivant illustre ce comportement.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Lorsqu'il est initialisé, le tableau vers lequel pointe `characterArray()` contient "x", "y" et "z".  Dans la mesure où la variable `characterArray` est `ReadOnly`, vous ne pouvez pas modifier sa valeur une fois qu'elle est initialisée, c'est\-à\-dire que vous ne pouvez pas lui assigner un nouveau tableau.  Toutefois, vous pouvez modifier les valeurs d'un ou plusieurs des membres du tableau.  Suite à un appel à `changeArrayElement` de la procédure, le tableau vers lequel pointe `characterArray()` contient "x", "M" et "z".  
  
 Notez que ce procédé est semblable à la déclaration d'un paramètre d'une procédure en tant que [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), ce qui empêche la procédure de modifier l'argument appelant lui\-même, mais lui permet de modifier ses membres.  
  
## Exemple  
 L'exemple suivant définit une propriété `ReadOnly` de la date à laquelle un employé a été embauché.  La classe stocke en interne la valeur de propriété en tant que variable `Private` et seul le code à l'intérieur de la classe peut modifier cette valeur.  Toutefois, la propriété est `Public` et tout code qui peut accéder à la classe peut lire la propriété.  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 Le modificateur `ReadOnly` peut être utilisé dans les contextes suivants :  
  
 [Dim, instruction](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## Voir aussi  
 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)