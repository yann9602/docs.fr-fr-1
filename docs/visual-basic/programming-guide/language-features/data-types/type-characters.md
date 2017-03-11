---
title: "Type Characters (Visual Basic) | Microsoft Docs"
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
  - "&H prefix for hexadecimal values"
  - "hexadecimal literals"
  - "F literal type character"
  - "& identifier type character"
  - "type characters"
  - "octal literals"
  - "literals, hexadecimal"
  - "&O prefix for octal values"
  - "literals, default types"
  - "defaults, literal types"
  - "C literal type character"
  - "type characters, literal"
  - "$ identifier type character"
  - "L literal type character"
  - "UI literal type characters"
  - "default literal types"
  - "D literal type character"
  - "literals, octal"
  - "S literal type character"
  - "! identifier type character"
  - "US literal type characters"
  - "% identifier type character"
  - "data types [Visual Basic], type characters"
  - "characters, identifier type"
  - "type characters, identifier"
  - "# identifier type character"
  - "identifier type characters"
  - "literal type characters"
  - "I literal type character"
  - "R literal type character"
  - "@ identifier type character"
  - "UL literal type characters"
  - "literal types, default"
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Type Characters (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

En plus de spécifier un type de données dans une instruction de déclaration, vous pouvez forcer le type de données de certains éléments de programmation à l'aide d'un *caractère de type*.  Le caractère de type doit immédiatement suivre l'élément \(aucun autre caractère ne doit venir s'interposer\).  
  
 Le caractère de type ne fait pas partie du nom de l'élément.  Un élément défini avec un caractère de type peut être référencé sans celui\-ci.  
  
## Caractères de type d'identificateur  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] met à votre disposition des *caractères de type d'identificateur* que vous pouvez utiliser dans une déclaration pour spécifier le type de données d'une variable ou d'une constante.  Le tableau suivant répertorie les caractères de type d'identificateur disponibles et donne des exemples de leur emploi.  
  
|Caractère de type d'identificateur|Type de données|Exemple|  
|----------------------------------------|---------------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Il n'existe aucun caractère de type d'identificateur pour les types de données `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong` ou `UShort`, ni pour les types de données composites, tels que les tableaux ou les structures.  
  
 Dans certains cas, vous pouvez ajouter le caractère `$` à une fonction [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)], par exemple `Left$` au lieu de `Left`, afin d'obtenir une valeur retournée de type `String`.  
  
 Dans tous les cas, le caractère de type d'identificateur doit immédiatement suivre le nom de l'identificateur.  
  
## Caractères de type de littéral  
 Un *littéral* est une représentation textuelle d'une valeur particulière d'un type de données.  
  
### Types de littéral par défaut  
 La forme d'un littéral, telle qu'elle se présente dans votre code, détermine normalement son type de données.  Le tableau ci\-dessous répertorie ces types par défaut.  
  
|Forme textuelle de littéral|Type de données par défaut|Exemple|  
|---------------------------------|--------------------------------|-------------|  
|Numérique, aucune partie fractionnaire|`Integer`|`2147483647`|  
|Numérique, aucune partie fractionnaire, trop grand pour `Integer`|`Long`|`2147483648`|  
|Numérique, partie fractionnaire|`Double`|`1.2`|  
|Placé entre guillemets doubles|`String`|`"A"`|  
|Placé entre signes dièse|`Date`|`#5/17/1993 9:32 AM#`|  
  
### Types de littéral forcés  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] met à votre disposition un ensemble de *caractères de type de littéral* que vous pouvez utiliser pour forcer un littéral à prendre un type de données autre que celui qui est indiqué par sa forme.  Pour ce faire, ajoutez le caractère souhaité après le littéral.  Le tableau suivant répertorie les caractères de type de littéral disponibles et donne des exemples de leur emploi.  
  
|Caractère de type de littéral|Type de données|Exemple|  
|-----------------------------------|---------------------|-------------|  
|`S`|`Short`|`I = 347S`|  
|`I`|`Integer`|`J = 347I`|  
|`L`|`Long`|`K = 347L`|  
|`D`|`Decimal`|`X = 347D`|  
|`F`|`Single`|`Y = 347F`|  
|`R`|`Double`|`Z = 347R`|  
|`US`|`UShort`|`L = 347US`|  
|`UI`|`UInteger`|`M = 347UI`|  
|`UL`|`ULong`|`N = 347UL`|  
|`C`|`Char`|`Q = "."C`|  
  
 Il n'existe aucun caractère de type de littéral pour les types de données `Boolean`, `Byte`, `Date`, `Object`, `SByte` ou `String`, ni pour les types de données composites, tels que les tableaux ou les structures.  
  
 Les littéraux peuvent également utiliser les caractères de type d'identificateur \(`%`, `&`, `@`, `!`, `#`, `$`\), tout comme le peuvent les variables, les constantes et les expressions.  Toutefois, les caractères de type de littéral \(`S`, `I`, `L`, `D`, `F`, `R`, `C`\) peuvent être utilisés uniquement avec des littéraux.  
  
 Dans tous les cas, le caractère de type de littéral doit immédiatement suivre la valeur littérale.  
  
## Littéraux hexadécimaux et octaux  
 Le compilateur interprète normalement un littéral entier comme représenté avec le système de numération décimale \(base 10\).  Vous pouvez forcer un littéral entier à être hexadécimal \(base 16\) avec le préfixe `&H` et vous pouvez le forcer à être octal \(base 8\) avec le préfixe `&O`.  Les chiffres qui suivent le préfixe doivent être adaptés au système de numération.  Le tableau suivant illustre ce système de représentation.  
  
|Base numérique|Préfixe|Valeurs de chiffres valables|Exemple|  
|--------------------|-------------|----------------------------------|-------------|  
|Hexadécimale \(base 16\)|`&H`|0\-9 et A\-F|`&HFFFF`|  
|Octale \(base 8\)|`&O`|0\-7|`&O77`|  
  
 Vous pouvez faire suivre un littéral préfixé d'un caractère de type de littéral.  L'exemple suivant fournit une illustration.  
  
```  
Dim counter As Short = &H8000S  
Dim flags As UShort = &H8000US  
```  
  
 Dans l'exemple précédent, `counter` a la valeur décimale \-32 768 et `flags` a la valeur décimale \+32 768.  
  
## Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)