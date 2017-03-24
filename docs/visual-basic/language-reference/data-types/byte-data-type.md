---
title: "Byte Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Byte"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Byte data type"
  - "data types [Visual Basic], assigning"
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Byte Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Contient des entiers 8 bits \(1 octet\) non signés dont la valeur est comprise entre 0 et 255.  
  
## Notes  
 Utilisez le type de données `Byte` pour contenir les données binaires.  
  
 La valeur par défaut de `Byte` est 0.  
  
## Conseils de programmation  
  
-   **Nombres négatifs.** Dans la mesure où `Byte` est un type non signé, il ne peut représenter un nombre négatif.  Si vous utilisez l'opérateur moins unaire \(`-`\) dans une expression qui correspond au type `Byte`, Visual Basic convertit d'abord l'expression en `Short`.  
  
-   **Conversions de format.** Lorsque Visual Basic lit ou écrit des fichiers, ou lorsqu'il appelle des DLL, des méthodes et des propriétés, il peut convertir automatiquement entre différents formats de données.  Les données binaires stockées dans des variables et des tableaux `Byte` sont préservées durant les conversions de format.  Vous ne devez pas utiliser une variable de type `String` pour des données binaires ; en effet, son contenu peut être endommagé pendant la conversion du format ANSI au format Unicode.  
  
-   **Extension.** Le type de données `Byte` s'étend à `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single` ou `Double`.  Ceci signifie que vous pouvez convertir `Byte` en ces types sans rencontrer d'erreur <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caractères de type.**  `Byte` n'a aucun caractère de type de littéral ou caractère de type d'identificateur.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Byte?displayProperty=fullName>.  
  
## Exemple  
 Dans l'exemple suivant, `b` est une variable `Byte`.  Les instructions montrent la plage de la variable et l'application d'opérateurs de décalage de bits vers lui.  
  
 [!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  
  
## Voir aussi  
 <xref:System.Byte?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)