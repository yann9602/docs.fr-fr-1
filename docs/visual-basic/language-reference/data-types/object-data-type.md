---
title: "Object Data Type | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Object"
  - "vb.Variant"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object variables, Object type"
  - "data types [Visual Basic], assigning"
  - "Object data type"
  - "Object data type, reference"
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Object Data Type
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Contient des adresses qui font référence aux objets.  Vous pouvez assigner un type référence \(chaîne, tableau, classe ou interface\) à une variable `Object`.  Une variable `Object` peut également faire référence à des données de tout type valeur \(numérique, `Boolean`, `Char`, `Date`, structure ou énumération\).  
  
## Notes  
 Le type de données `Object` peut pointer vers des données de tout type de données, y compris toute instance d'objet que votre application reconnaît.  Utilisez `Object` lorsque vous ne savez pas au moment de la compilation quel est le type de données vers lequel la variable peut pointer.  
  
 La valeur par défaut de `Object` est `Nothing` \(référence nulle\).  
  
## Types de données  
 Vous pouvez assigner une variable, une constante ou une expression de n'importe quel type de données à une variable `Object`.  Pour déterminer le type de données auquel une variable `Object` fait actuellement référence, vous pouvez utiliser la méthode <xref:System.Type.GetTypeCode%2A> de la classe <xref:System.Type?displayProperty=fullName>.  L'exemple suivant illustre ce comportement.  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 Le type de données `Object` est un type référence.  Toutefois, Visual Basic traite une variable `Object` comme un type valeur lorsqu'elle fait référence aux données d'un type valeur.  
  
## Stockage  
 Quel que soit le type de données auquel elle fait référence, une variable `Object` ne contient pas la valeur de donnée elle\-même, mais plutôt un pointeur vers la valeur.  Elle occupe toujours quatre octets dans la mémoire de l'ordinateur ; toutefois, ces quatre octets ne comprennent pas le stockage des données représentant la valeur de la variable.  Étant donné que le code utilise le pointeur pour localiser les données, les variables `Object` contenant des types valeur sont légèrement plus lentes que celles qui sont explicitement typées.  
  
## Conseils de programmation  
  
-   **Considérations sur l'interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, tels que des objets Automation ou COM, gardez à l'esprit que les types pointeur dans d'autres environnements ne sont pas compatibles avec le type `Object` Visual Basic.  
  
-   **Performances.** Une variable que vous déclarez avec le type `Object` est assez flexible pour contenir une référence à n'importe quel objet.  Toutefois, lorsque vous appelez une méthode ou une propriété sur une variable de ce type, vous subissez toujours la *liaison tardive* \(au moment de l'exécution\).  Pour forcer la *liaison anticipée* \(au moment de la compilation\) et obtenir de meilleures performances, déclarez la variable avec un nom de classe spécifique ou effectuez un cast de celle\-ci en type de données spécifique.  
  
     Lorsque vous déclarez une variable objet, essayez d'utiliser un type de classe spécifique, par exemple <xref:System.OperatingSystem> au lieu du type `Object` généralisé.  Vous devez également utiliser la classe la plus spécifique parmi les classes disponibles, telle que <xref:System.Windows.Forms.TextBox> au lieu de <xref:System.Windows.Forms.Control>, de façon à pouvoir accéder à ses propriétés et méthodes.  Vous pouvez généralement utiliser la liste **Classes** dans l'**Explorateur d'objets** pour rechercher le nom des classes disponibles.  
  
-   **Extension.** Tous les types de données et tous les types référence s'étendent au type de données `Object`.  Cela signifie que vous pouvez convertir n'importe quel type en `Object` sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=fullName>.  
  
     Toutefois, si vous effectuez une conversion entre des types valeur et `Object`, Visual Basic exécute des opérations appelées *conversion boxing* et *conversion unboxing* qui ralentissent l'exécution.  
  
-   **Caractères de type.**  `Object` n'a aucun caractère de type de littéral ou caractère de type d'identificateur.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la classe <xref:System.Object?displayProperty=fullName>.  
  
## Exemple  
 L'exemple suivant illustre une variable `Object` pointant vers une instance d'objet.  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## Voir aussi  
 <xref:System.Object>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [How to: Determine Whether Two Objects Are Related](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [How to: Determine Whether Two Objects Are Identical](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)