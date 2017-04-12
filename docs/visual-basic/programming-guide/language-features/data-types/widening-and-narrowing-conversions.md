---
title: "Conversions étendues et restrictives (Visual Basic) | Documents Microsoft"
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
- widening conversions
- narrowing conversions
- conversions, type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions, exceptions during conversion
- type conversion, exceptions during conversion
- conversions, data type
- conversions, narrowing
- type conversion, narrowing
- data type conversion, widening
- data type conversion, narrowing
- changing data types
- type conversion, widening
- data type conversion, exceptions during conversion
- conversions, widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: 27
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
ms.openlocfilehash: 88c5db6e7e82a88ae8015b581e5a795ec389d003
ms.lasthandoff: 03/13/2017

---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Conversions étendues et restrictives (Visual Basic)
Un facteur important lors d’une conversion de type est si le résultat de la conversion est dans la plage du type de données de destination.  
  
 A *conversion étendue* modifie une valeur de type de données pouvant autoriser toutes les valeurs possibles des données d’origine.  Les conversions étendues préservent la valeur source, mais peuvent modifier sa représentation. Cela se produit si vous convertissez un type intégral en `Decimal`, ou à partir de `Char` à `String`.  
  
 Une *conversion restrictive* modifie une valeur en un type de données qui peut ne pas pouvoir contenir certaines des valeurs possibles. Par exemple, une valeur fractionnaire est arrondie lorsqu’elle est convertie en un type intégral et un type numérique converti en `Boolean` est réduit à la valeur `True` ou `False`.  
  
## <a name="widening-conversions"></a>Conversions étendues  
 Le tableau suivant présente les conversions étendues standard.  
  
|Type de données|S’étend aux types de données <sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Courte](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Entier](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Tout type énuméré ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|Son type intégral sous-jacent et tout type auquel s’étend le type sous-jacent.|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|Tableau `Char`|`Char`tableau,`String`|  
|Tout type|[Objet](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|N’importe quel type dérivé|Un type à partir de laquelle elle est dérivée de base <sup>3</sup>.|  
|Tout type|Toute interface qu’il implémente.|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|N’importe quel type de données ou un type d’objet.|  
  
 <sup>1</sup> par définition, chaque type de données s’élargit par lui-même.  
  
 <sup>2</sup> les conversions de `Integer`, `UInteger`, `Long`, `ULong`, ou `Decimal` à `Single` ou `Double` peuvent entraîner une perte de précision, mais jamais une perte d’amplitude. En ce sens qu’ils n’entraînent pas de perte d’informations.  
  
 <sup>3</sup> il peut sembler surprenant qu’une conversion entre un type dérivé à l’un de ses types de base soit étendue. La justification est que le type dérivé contient tous les membres du type de base, donc il correspond à une instance du type de base. Dans le sens opposé, le type de base ne contient pas tous les nouveaux membres définis par le type dérivé.  
  
 Les conversions étendues réussissent toujours au moment de l’exécution et sans jamais aucune perte de données. Vous pouvez toujours les exécuter implicitement, que la [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) définit le type de commutateur à la vérification de la `On` ou `Off`.  
  
## <a name="narrowing-conversions"></a>Conversions restrictives  
 Les conversions restrictives standard sont les suivantes :  
  
-   La table inverses des conversions étendues dans l’exemple précédent (excepté que chaque type s’élargit par lui-même)  
  
-   Les conversions dans les deux sens entre [booléenne](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) et tout type numérique  
  
-   Les conversions à partir de n’importe quel type numérique à tout type énuméré (`Enum`)  
  
-   Les conversions dans les deux sens entre [chaîne](../../../../visual-basic/language-reference/data-types/string-data-type.md) et tout type numérique, `Boolean`, ou [Date](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   Les conversions d’un type de données ou un objet de type à un type dérivé  
  
 Les conversions restrictives ne pas toujours réussisse au moment de l’exécution et peut échouer ou entraîner une perte de données. Une erreur se produit si le type de données de destination ne peut pas recevoir la valeur convertie. Par exemple, une conversion numérique peut provoquer un dépassement de capacité. Le compilateur ne vous permet pas d’effectuer des conversions restrictives implicitement sauf si la [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) définit le type de commutateur à la vérification de la `Off`.  
  
> [!NOTE]
>  L’erreur de conversion restrictive est supprimée pour les conversions entre les éléments dans un `For Each…Next` collection à la variable de contrôle de boucle. Pour plus d’informations et d’exemples, consultez la section « Conversions restrictives » dans [For Each... L’instruction suivante](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Quand utiliser des Conversions restrictives  
 Vous utilisez une conversion restrictive lorsque vous savez que la valeur source peut être convertie au type de données de destination sans erreur ni perte de données. Par exemple, si vous avez un `String` que vous savez contient « True » ou « False », vous pouvez utiliser la `CBool` (mot clé) à convertir en `Boolean`.  
  
## <a name="exceptions-during-conversion"></a>Exceptions lors de la Conversion  
 Étant donné que les conversions étendues toujours réussissent, ils ne lèvent pas d’exceptions. Généralement, les conversions restrictives, en cas d’échec, lever les exceptions suivantes :  
  
-   <xref:System.InvalidCastException>— Si aucune conversion n’est définie entre les deux types</xref:System.InvalidCastException>  
  
-   <xref:System.OverflowException>— (types intégraux uniquement) si la valeur convertie est trop grande pour le type de cible</xref:System.OverflowException>  
  
 Si une classe ou une structure définit un [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) comme un opérateur de conversion vers ou depuis cette classe ou structure, qui `CType` peut lever une exception appropriée. En outre, qui `CType` peut appeler [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fonctions ou [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] méthodes, qui peuvent à leur tour lever diverses exceptions.  
  
## <a name="changes-during-reference-type-conversions"></a>Modifications apportées au cours des Conversions de Type référence  
 Une conversion d’un *type référence* ne copie que le pointeur vers la valeur. La valeur elle-même n’est ni copiée ni modifiée. La seule chose que vous pouvez modifier est le type de données de la variable contenant le pointeur. Dans l’exemple suivant, le type de données est converti de la classe dérivée vers sa classe de base, mais l’objet qui les deux variables pointent désormais vers est inchangé.  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversions entre des chaînes et d’autres Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [Comment : convertir un objet en un autre Type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Conversions de tableaux](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Fonctions de conversion de types](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
