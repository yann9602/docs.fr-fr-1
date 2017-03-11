---
title: "Widening and Narrowing Conversions (Visual Basic) | Microsoft Docs"
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
  - "widening conversions"
  - "narrowing conversions"
  - "conversions, type"
  - "data types [Visual Basic], changing"
  - "variables [Visual Basic], changing data type"
  - "conversions, exceptions during conversion"
  - "type conversion, exceptions during conversion"
  - "conversions, data type"
  - "conversions, narrowing"
  - "type conversion, narrowing"
  - "data type conversion, widening"
  - "data type conversion, narrowing"
  - "changing data types"
  - "type conversion, widening"
  - "data type conversion, exceptions during conversion"
  - "conversions, widening"
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Widening and Narrowing Conversions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Le fait que le résultat se situe ou non dans la plage du type de données de destination constitue un élément d'information important dans la conversion de type.  
  
 *Une conversion étendue* modifie une valeur à un type de données qui peut tenir compte de la valeur possible des données d'origine.  Les conversions étendues préservent la valeur source, mais peuvent modifier sa représentation.  Cela se produit si vous convertissez un type intégral à `Decimal`, ou d' `Char` à `String`.  
  
 Dans une *conversion restrictive*, la valeur est convertie dans un type de données susceptible de ne pas pouvoir accueillir certaines valeurs possibles des données.  Par exemple, une valeur fractionnaire est arrondie lorsqu'elle est convertie en un type intégral, et un type numérique converti à `Boolean` est réduit au `True` ou à `False`.  
  
## Conversions étendues  
 Le tableau suivant répertorie les conversions étendues standard.  
  
|||  
|-|-|  
|Type de données|Extension aux types de données <sup>1</sup>|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Entier](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double` <sup>2</sup>|  
|[Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double` <sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double` <sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double` <sup>2</sup>|  
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Tout type énuméré \([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)\)|Son type intégral sous\-jacent et tout type auquel le type sous\-jacent s'étend.|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|Tableau `Char`|Tableau `Char`, `String`|  
|Tout type|[Objet](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Tout type dérivé|tout type de base dont il est dérivé <sup>3</sup>.|  
|Tout type|Toute interface qu'il implémente.|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|tout type de données ou type d'objet.|  
  
 <sup>1</sup> Par définition, chaque type de données s'élargit par lui\-même.  
  
 <sup>2</sup> Les conversions de `Integer`, `UInteger`, `Long`, `ULong` ou `Decimal` en `Single` ou `Double` peuvent entraîner un manque de précision, mais jamais une perte d'amplitude.  Elles n'entraînent donc jamais de perte d'information.  
  
 <sup>3</sup> Il peut sembler surprenant qu'une conversion entre un type dérivé et l'un de ses types de base soit étendue.  Cela s'explique par le fait que le type dérivé contient tous les membres du type de base ; il se qualifie donc comme une instance du type de base.  Dans le sens opposé, le type de base ne contient aucun nouveau membre défini par le type dérivé.  
  
 Les conversions étendues réussissent toujours au moment de l'exécution et sans jamais aucune perte de données.  Vous pouvez toujours les exécuter implicitement, que l'[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) attribue la valeur `On` ou `Off` au commutateur de vérification de type.  
  
## Conversions restrictives  
 Les conversions restrictives standard sont les suivantes :  
  
-   Conversions inverses des conversions étendues dans le tableau précédent \(excepté que chaque type s'élargit par lui\-même\).  
  
-   Conversions entre un type [Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) et tout type numérique \(dans l'un et l'autre sens\).  
  
-   Conversions de n'importe quel type numérique en un type énuméré \(`Enum`\).  
  
-   Conversions dans l'un et l'autre sens entre [String](../../../../visual-basic/language-reference/data-types/string-data-type.md) et tout type numérique, `Boolean` ou [Date](../../../../visual-basic/language-reference/data-types/date-data-type.md).  
  
-   Conversions entre un type de données ou un type d'objet et un type dérivé de lui.  
  
 Les conversions restrictives ne réussissent pas toujours au moment de l'exécution et peuvent échouer ou entraîner la perte de données.  Une erreur se produit si le type de données de destination ne peut pas accueillir la valeur convertie.  Par exemple, une conversion numérique peut provoquer un dépassement de capacité.  Le compilateur ne vous permet pas d'exécuter des conversions restrictives implicitement sauf si l'[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) attribue la valeur `Off` au commutateur de vérification de type.  
  
> [!NOTE]
>  L'erreur de conversion restrictive est supprimée pour les conversions à partir des éléments d'une collection `For Each…Next` vers la variable de contrôle de boucle.  Pour plus d'informations et d'exemples, consultez la section « Conversions restrictives » dans [For Each...Next, instruction](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### Utilisation des conversions restrictives  
 Utilisez une conversion restrictive lorsque vous savez que la valeur source peut être convertie dans le type de données de destination sans erreur ni perte de données.  Par exemple, si vous avez `String` qui contient « true » ou « False », vous pouvez utiliser le mot clé d' `CBool` pour le convertir en `Boolean`.  
  
## Exceptions pendant la conversion  
 Étant donné que les conversions étendues aboutissent toujours, elles ne lèvent pas d'exceptions.  Les conversions restrictives, lorsqu'elles échouent, lèvent le plus souvent les exceptions suivantes :  
  
-   <xref:System.InvalidCastException> — si aucune conversion n'est définie entre les deux types  
  
-   <xref:System.OverflowException> — \(types intégraux uniquement\) si la valeur convertie est trop grande pour le type cible  
  
 Si une classe ou une structure définit [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) pour qu'il serve d'opérateur de conversion vers ou depuis cette classe ou cette structure, `CType` peut lever n'importe quelle exception qu'il estime appropriée.  De plus, `CType` peut appeler des fonctions  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ou des méthodes [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] qui peuvent à leur tour lever diverses exceptions.  
  
## Modification lors des conversions de type référence  
 Une conversion à partir d'un *type référence* ne copie que le pointeur vers la valeur.  La valeur elle\-même n'est ni copiée ni modifiée.  Seul peut être modifié le type de données de la variable contenant le pointeur.  Dans l'exemple suivant, le type de données est converti de la classe dérivée vers sa classe de base, mais l'objet vers lequel pointent les deux variables reste inchangé.  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)