---
title: "Implicit and Explicit Conversions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conversions, type"
  - "variables [Visual Basic], changing data type"
  - "casting"
  - "conversions, data type"
  - "type conversion, implicit conversions"
  - "CType function, conversions"
  - "casting, data types"
  - "data type conversion, explicit"
  - "type conversion, explicit conversions"
  - "data types [Visual Basic], casting"
  - "conversions, implicit"
  - "explicit data type conversions"
  - "conversions"
  - "changing data types"
  - "conversions, explicit"
  - "data type conversion, implicit"
  - "implicit data type conversions"
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Implicit and Explicit Conversions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Une *conversion implicite* ne requiert pas de syntaxe particulière dans le code source.  Dans l'exemple suivant, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit implicitement la valeur de `k` en une valeur à virgule flottante simple précision avant de l'assigner à `q`.  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 Une *conversion explicite* utilise un mot clé de conversion de type.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit plusieurs tels mots clés qui forcent une expression entre parenthèses au type de données désiré.  Ces mots clés agissent comme des fonctions, mais le compilateur génère le code en ligne, si bien que l'exécution est légèrement plus rapide qu'avec un appel de fonction.  
  
 Dans l'exemple ci\-dessous qui fait suite à l'exemple précédent, le mot clé `CInt` reconvertit la valeur de `q` en un entier avant de l'assigner à `k`.  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## Mots clés de conversion  
 Le tableau suivant répertorie les mots clés de conversion disponibles.  
  
||||  
|-|-|-|  
|Mot clé de conversion de type|Convertit une expression vers le type de données|Types de données autorisés d'expression à convertir|  
|`CBool`|[Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Tout type numérique \(y compris `Byte`, `SByte` et les types énumérés\), `String`, `Object`|  
|`CByte`|[Byte Data Type](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|Tout type numérique \(y compris `SByte` et les types énumérés\), `Boolean`, `String`, `Object`|  
|`CChar`|[Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|  
|`CDate`|[Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|  
|`CDbl`|[Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md)|Tout type numérique \(y compris `Byte`, `SByte` et les types énumérés\), `Boolean`, `String`, `Object`|  
|`CDec`|[Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|Tout type numérique \(y compris `Byte`, `SByte` et les types énumérés\), `Boolean`, `String`, `Object`|  
|`CInt`|[Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|Tout type numérique \(y compris `Byte`, `SByte` et les types énumérés\), `Boolean`, `String`, `Object`|  
|`CLng`|[Long Data Type](../../../../visual-basic/language-reference/data-types/long-data-type.md)|Tout type numérique \(y compris `Byte`, `SByte` et les types énumérés\), `Boolean`, `String`, `Object`|  
|`CObj`|[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)|Tout type|  
|`CSByte`|[SByte Data Type](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|Tout type numérique \(y compris `Byte` et les types énumérés\), `Boolean`, `String`, `Object`|  
|`CShort`|[Short Data Type](../../../../visual-basic/language-reference/data-types/short-data-type.md)|Tout type numérique \(y compris `Byte`, `SByte` et les types énumérés\), `Boolean`, `String`, `Object`|  
|`CSng`|[Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md)|Tout type numérique \(y compris `Byte`, `SByte` et les types énumérés\), `Boolean`, `String`, `Object`|  
|`CStr`|[String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)|Tout type numérique \(y compris `Byte`, `SByte` et les types énumérés\), `Boolean`, tableau `Char`, `Char`, `Date`, `Object`|  
|`CType`|Type spécifié après la virgule \(`,`\)|Lors d'une conversion vers un *type de données élémentaire* \(y compris un tableau d'un type élémentaire\), les mêmes types que ceux qui sont autorisés pour le mot clé de conversion correspondant<br /><br /> Lors d'une conversion vers un *type de données composite*, les interfaces qu'il implémente et les classes à partir desquelles il hérite<br /><br /> Lors de la conversion vers une classe ou une structure sur laquelle vous avez surchargé `CType`, cette classe ou structure|  
|`CUInt`|[UInteger Data Type](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|Tout type numérique \(y compris `Byte`, `SByte` et les types énumérés\), `Boolean`, `String`, `Object`|  
|`CULng`|[ULong Data Type](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|Tout type numérique \(y compris `Byte`, `SByte` et les types énumérés\), `Boolean`, `String`, `Object`|  
|`CUShort`|[UShort Data Type](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|Tout type numérique \(y compris `Byte`, `SByte` et les types énumérés\), `Boolean`, `String`, `Object`|  
  
## La fonction CType  
 La [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) opère sur deux arguments.  Le premier correspond à l'expression à convertir, le second au type de données de destination ou à la classe d'objet.  Notez que le premier argument doit être une expression, et non un type.  
  
 `CType` est une *fonction inline*, ce qui signifie que le code compilé effectue la conversion, souvent sans générer d'appel de fonction.  Les performances sont alors améliorées.  
  
 Pour obtenir une comparaison entre `CType` et les autres mots clés de conversion de type, consultez [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) et [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
### Types élémentaires  
 L'exemple suivant illustre l'utilisation du mot clé `CType` :  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### Types composites  
 Vous pouvez utiliser le mot clé `CType` pour convertir des valeurs vers des types de données composites ou élémentaires.  Vous pouvez également l'utiliser pour forcer la conversion d'une classe d'objet vers le type de l'une de ses interfaces, comme dans l'exemple suivant.  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### Types tableau  
 `CType` peut également convertir des types de données tableau, comme dans l'exemple suivant.  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 Pour obtenir des informations supplémentaires et un exemple, consultez [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).  
  
### Types définissant CType  
 Vous pouvez définir `CType` sur une classe ou une structure que vous avez définie.  Cela vous permet de convertir des valeurs vers et à partir du type de votre classe ou structure.  Pour obtenir des informations supplémentaires et un exemple, consultez [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
> [!NOTE]
>  Les valeurs utilisées avec un mot clé de conversion doivent être acceptées par le type de données de destination, sans quoi une erreur se produit.  Par exemple, si vous tentez de convertir un type `Long` en `Integer`, la valeur du type `Long` doit se situer dans la plage acceptée par le type de données `Integer`.  
  
> [!CAUTION]
>  La spécification de `CType` pour effectuer une conversion à partir d'un type de classe vers un autre échoue au moment de l'exécution si le type source ne dérive pas du type de destination.  Un tel échec lève une exception <xref:System.InvalidCastException>.  
  
 Toutefois, si l'un des types est une structure ou une classe que vous avez définie et si vous avez défini `CType` sur cette structure ou cette classe, une conversion peut réussir si elle satisfait aux exigences de votre `CType`.  Consultez [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
 Pour désigner le processus de conversion explicite, on parle également de *casting* d'une expression vers un certain type de données ou une classe d'objet.  
  
## Voir aussi  
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)