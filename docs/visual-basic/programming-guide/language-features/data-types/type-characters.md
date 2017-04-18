---
title: "Tapez les caractères (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals
- F literal type character
- '& identifier type character'
- type characters
- octal literals
- literals, hexadecimal
- '&O prefix for octal values'
- literals, default types
- defaults, literal types
- C literal type character
- type characters, literal
- $ identifier type character
- L literal type character
- UI literal type characters
- default literal types
- D literal type character
- literals, octal
- S literal type character
- '! identifier type character'
- US literal type characters
- '% identifier type character'
- data types [Visual Basic], type characters
- characters, identifier type
- type characters, identifier
- '# identifier type character'
- identifier type characters
- literal type characters
- I literal type character
- R literal type character
- '@ identifier type character'
- UL literal type characters
- literal types, default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6e112e7d221ef8e7a660094306bbb242c988e843
ms.lasthandoff: 03/13/2017

---
# <a name="type-characters-visual-basic"></a>Caractères de type (Visual Basic)
En plus de spécifier un type de données dans une instruction de déclaration, vous pouvez forcer le type de données de certains éléments de programmation avec un *caractère de type*. Le caractère de type doit suivre immédiatement l’élément, sans caractères concernés de n’importe quel type.  
  
 Le caractère de type ne fait pas partie du nom de l’élément. Un élément défini avec un caractère de type peut être référencé sans caractère de type.  
  
## <a name="identifier-type-characters"></a>Caractères de Type d’identificateur  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fournit un jeu de *caractères de type d’identificateur*, que vous pouvez utiliser dans une déclaration pour spécifier le type de données d’une variable ou constante. Le tableau suivant présente les caractères de type identificateur disponible avec des exemples d’utilisation.  
  
|Caractère de type d’identificateur|Type de données|Exemple|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Il n’existe aucun caractère de type identificateur pour le `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, ou `UShort` des types de données, ni pour les types de données composites tels que les tableaux ou les structures.  
  
 Dans certains cas, vous pouvez ajouter la `$` à un [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de fonction, par exemple `Left$` au lieu de `Left`, afin d’obtenir une valeur retournée de type `String`.  
  
 Dans tous les cas, le caractère de type identificateur doit suivre immédiatement le nom d’identificateur.  
  
## <a name="literal-type-characters"></a>Caractères de Type littéral  
 A *littéral* est une représentation textuelle d’une valeur particulière d’un type de données.  
  
### <a name="default-literal-types"></a>Types de littéral par défaut  
 La forme d’un littéral, tel qu’il apparaît dans votre code normalement détermine son type de données. Le tableau suivant présente les types par défaut.  
  
|Forme textuelle de littéral|Type de données par défaut|Exemple|  
|-----------------------------|-----------------------|-------------|  
|Numérique, aucune partie fractionnaire|`Integer`|`2147483647`|  
|Numérique, aucune partie fractionnaire, trop grand pour`Integer`|`Long`|`2147483648`|  
|Numérique, partie fractionnaire|`Double`|`1.2`|  
|Placé entre guillemets doubles|`String`|`"A"`|  
|Compris entre signes dièse|`Date`|`#5/17/1993 9:32 AM#`|  
  
### <a name="forced-literal-types"></a>Types de littéral forcés  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fournit un jeu de *caractères de type littéral*, que vous pouvez utiliser pour forcer un littéral à prendre un type de données différent de celui de son formulaire indique. Pour cela, en ajoutant le caractère à la fin du littéral. Le tableau suivant présente les caractères de type de littéral disponibles avec des exemples d’utilisation.  
  
|Caractère de type littéral|Type de données|Exemple|  
|----------------------------|---------------|-------------|  
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
  
 Il n’existe aucun caractère de type de littéral pour les `Boolean`, `Byte`, `Date`, `Object`, `SByte`, ou `String` des types de données, ni pour les types de données composites tels que les tableaux ou les structures.  
  
 Les littéraux peuvent également utiliser les caractères de type d’identificateur (`%`, `&`, `@`, `!`, `#`, `$`), comme des variables, des constantes et des expressions. Toutefois, les caractères de type de littéral (`S`, `I`, `L`, `D`, `F`, `R`, `C`) peut être utilisé uniquement avec des littéraux.  
  
 Dans tous les cas, le caractère de type de littéral doit suivre immédiatement la valeur littérale.  
  
## <a name="hexadecimal-and-octal-literals"></a>Littéraux hexadécimaux et octaux  
 Le compilateur construes normalement un littéral d’entier dans le système décimal (base 10). Vous pouvez forcer un littéral entier à être hexadécimal (base 16) avec le `&H` préfixe et vous pouvez le forcer à être octal (base 8) avec le `&O` préfixe. Les chiffres qui suivent le préfixe doivent être appropriées pour le système. Le tableau suivant illustre ce comportement.  
  
|Nombre de base|Préfixe|Valeurs de chiffre valide|Exemple|  
|-----------------|------------|------------------------|-------------|  
|Hexadécimale (base 16)|`&H`|0-9 et A-F|`&HFFFF`|  
|Octale (base 8)|`&O`|0-7|`&O77`|  
  
 Vous pouvez suivre un littéral préfixé avec un caractère de type littéral. L’exemple suivant illustre ce point.  
  
```  
Dim counter As Short = &H8000S  
Dim flags As UShort = &H8000US  
```  
  
 Dans l’exemple précédent, `counter` a la valeur décimale-32&768; et `flags` a la valeur décimale +&32;&768;.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Types valeur et Types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Dépannage des Types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
