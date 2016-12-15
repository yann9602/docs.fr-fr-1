---
title: "Char Data Type (Visual Basic) | Microsoft Docs"
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
  - "vb.Char"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "literal type characters, C"
  - "Char data type"
  - "C literal type character"
  - "data types [Visual Basic], assigning"
  - "Char data type, character literals"
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Char Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Conserve les points de code 16 bits \(2 octets\) non signés dont la valeur varie entre 0 et 65535.  Chaque *point de code*, ou code de caractère, représente un caractère Unicode unique.  
  
## Notes  
 Utilisez le type de données `Char` lorsque vous devez contenir un caractère unique et n'avez pas besoin de la charge de `String`.  Dans certains cas, vous pouvez utiliser `Char()`, un tableau d'éléments `Char`, pour contenir plusieurs caractères.  
  
 La valeur par défaut de `Char` est le caractère avec un point de code de 0.  
  
## Caractères Unicode  
 Les 128 premiers points de code \(0 à 127\) Unicode correspondent aux lettres et symboles sur un clavier américain standard.  clavier.  Ces 128 premiers points de code sont les mêmes que ceux définis par le jeu de caractères ASCII.  Les 128 points de code suivants \(128–255\) représentent les caractères spéciaux, tels que les lettres de l'alphabet latin, les accents, les symboles monétaires et les fractions.  Unicode utilise les points de code restants \(256\-65 535\) pour une large gamme de symboles, y compris les caractères textuels mondiaux, les signes diacritiques, ainsi que les symboles mathématiques et techniques.  
  
 Vous pouvez utiliser des méthodes telles que <xref:System.Char.IsDigit%2A> et <xref:System.Char.IsPunctuation%2A> sur une variable `Char` pour déterminer sa classification Unicode.  
  
## Conversions de type  
 Visual Basic n'opère pas de conversion directe entre le type `Char` et les types numériques.  Vous pouvez utiliser la fonction <xref:Microsoft.VisualBasic.Strings.Asc%2A> ou <xref:Microsoft.VisualBasic.Strings.AscW%2A> pour convertir une valeur `Char` en un `Integer` qui représente son point de code.  Vous pouvez utiliser <xref:Microsoft.VisualBasic.Strings.Chr%2A> ou <xref:Microsoft.VisualBasic.Strings.ChrW%2A> pour convertir une valeur `Integer` en un `Char` qui représente son point de code.  
  
 Si le commutateur de vérification de type \([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)\) est activé, vous devez ajouter le caractère de type de littéral à un littéral de chaîne à un caractère pour l'identifier comme type de données `Char`.  L'exemple suivant illustre ce comportement.  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## Conseils de programmation  
  
-   **Nombres négatifs.** `Char` est un type non signé et ne peut pas représenter de valeur négative.  Dans tous les cas, vous ne devez pas utiliser `Char` pour stocker des valeurs numériques.  
  
-   **Considérations sur l'interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n'oubliez pas que les types de caractères possèdent une largeur des données différente \(8 bits\) dans d'autres environnements.  Si vous passez un argument de 8 bits à un tel composant, déclarez\-le comme type de données `Byte` et non comme `Char` dans votre nouveau code Visual Basic.  
  
-   **Extension.** Le type de données `Char` s'étend à `String`.  Cela signifie que vous pouvez convertir `Char` en `String` sans produire d'erreur <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caractères de type.** L'ajout du caractère de type de littéral `C` à un littéral de chaîne à un caractère le force au type de données `Char`.  `Char` n'a aucun caractère de type identificateur.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Char?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Char?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)