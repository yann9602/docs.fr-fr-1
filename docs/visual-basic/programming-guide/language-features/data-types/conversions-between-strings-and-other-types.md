---
title: "Conversions Between Strings and Other Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "data type conversion, string"
  - "conversions, type"
  - "string conversion"
  - "conversions, data type"
  - "type conversion, string"
  - "regional options"
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Conversions Between Strings and Other Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez convertir une valeur numérique, `Boolean` ou date\/heure vers le type `String`.  Vous pouvez également opérer la conversion inverse, c'est\-à\-dire d'une chaîne vers un type de données numérique, `Boolean` ou `Date`, à condition que le contenu de la chaîne soit une valeur reconnue par le type de données de destination.  Si tel n'est pas le cas, une erreur d'exécution se produit.  
  
 Ces différentes conversions \(dans l'un et l'autre sens\) sont des conversions restrictives.  Utilisez les mots clés de conversion de type \(`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort` et `CType`\).  Les fonctions <xref:Microsoft.VisualBasic.Strings.Format%2A> et <xref:Microsoft.VisualBasic.Conversion.Val%2A> vous permettent de mieux contrôler les conversions entre les chaînes et les nombres.  
  
 Si vous avez défini une classe ou une structure, vous pouvez définir des opérateurs de conversion de type entre `String` et le type de votre classe ou structure.  Pour plus d'informations, consultez [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## Conversion de nombres en chaînes  
 Vous pouvez utiliser la fonction `Format` pour convertir un nombre vers une chaîne mise en forme, qui peut inclure non seulement les chiffres appropriés, mais également des symboles de mise en forme tels qu'un symbole monétaire \(par exemple, `$`\), des séparateurs de milliers ou des *symboles de groupement des chiffres* \(tels que `,`\) et un séparateur décimal \(tel que `.`\).  `Format` utilise automatiquement les symboles appropriés en fonction des paramètres **Options régionales** spécifiés dans le **Panneau de configuration** de Windows.  
  
 Notez que l'opérateur de concaténation \(`&`\) peut convertir implicitement un nombre en chaîne, comme le montre l'exemple suivant.  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## Conversion de chaînes en nombres  
 Vous pouvez utiliser la fonction `Val` pour convertir explicitement les chiffres d'une chaîne en nombre.  `Val` lit la chaîne jusqu'à ce qu'elle rencontre un caractère autre qu'un chiffre, un espace, une tabulation, un saut de ligne ou un point.  Les séquences "&O" et "&H" altèrent la base du système numérique et interrompent la lecture.  Tant qu'elle n'arrête pas sa lecture, la fonction `Val` convertit tous les caractères appropriés en une valeur numérique.  Par exemple, l'instruction suivante retourne la valeur `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Lorsque [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] convertit une chaîne en valeur numérique, il utilise les **Options régionales** spécifiées dans le **Panneau de configuration** de Windows pour interpréter le séparateur de milliers, le séparateur décimal et le symbole monétaire.  Cela signifie qu'une conversion peut réussir avec certains paramètres, mais pas avec d'autres.  Par exemple, la valeur `"$14.20"` est acceptée pour le paramètre régional Anglais \(États\-Unis\), mais pas pour un paramètre régional français.  
  
## Voir aussi  
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Introduction aux applications internationales basées sur le .NET Framework](/visual-studio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)