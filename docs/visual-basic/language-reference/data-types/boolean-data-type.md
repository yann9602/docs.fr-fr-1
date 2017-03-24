---
title: "Boolean Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.FALSE"
  - "vb.TRUE"
  - "vb.Boolean"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Boolean data type"
  - "Boolean values, False keyword"
  - "False keyword [Visual Basic]"
  - "True keyword [Visual Basic]"
  - "Boolean values, True keyword"
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Boolean Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Stocke des valeurs qui peuvent être uniquement `True` ou `False`.  Les mots clé `True` et `False` correspondent aux deux états des variables `Boolean`.  
  
## Notes  
 Utilisez [Boolean Data Type \(Visual Basic\)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) pour contenir des valeurs à deux états, tels que true\/false, oui\/non ou actif\/inactif.  
  
 La valeur par défaut de `Boolean` est `False`.  
  
 Les valeurs `Boolean` ne sont pas stockées en tant que nombres et les valeurs stockées ne sont pas destinées à être équivalentes aux nombres.  Vous ne devez jamais écrire un code qui repose sur les valeurs numériques équivalentes à `True` et `False`.  Autant que possible, limitez l'utilisation des variables `Boolean` aux valeurs logiques pour lesquelles elles sont conçues.  
  
## Conversions de type  
 Lorsque Visual Basic convertit des valeurs de type de données numériques en `Boolean`, 0 devient `False` et toutes les autres valeurs deviennent `True`.  Lorsque Visual Basic convertit des valeurs `Boolean` en types numériques, `False` devient 0 et `True` devient \-1.  
  
 Lorsque vous convertissez des valeurs `Boolean` et des types de données numériques, n'oubliez pas que les méthodes de conversion .NET Framework ne produisent pas toujours le même résultat que les mots clé de conversion Visual Basic.  En effet, la conversion Visual Basic conserve un comportement compatible avec les versions antérieures.  Pour plus d'informations, consultez « Le type booléen ne se convertit pas correctement en type numérique » dans [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## Conseils de programmation  
  
-   **Nombres négatifs.** `Boolean` n'est pas un type numérique et ne peut pas représenter de valeur négative.  Dans tous les cas, vous ne devez pas utiliser `Boolean` pour stocker des valeurs numériques.  
  
-   **Caractères de type.**  `Boolean` n'a aucun caractère de type de littéral ou caractère de type d'identificateur.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Boolean?displayProperty=fullName>.  
  
## Exemple  
 Dans l'exemple suivant, `runningVB` est une variable de type `Boolean` qui enregistre une simple valeur yes\/no.  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## Voir aussi  
 <xref:System.Boolean?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [CType, fonction](../../../visual-basic/language-reference/functions/ctype-function.md)