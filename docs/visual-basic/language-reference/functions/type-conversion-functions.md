---
title: "Type Conversion Functions (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.CUShort"
  - "vb.csng"
  - "vb.CDate"
  - "CByte"
  - "CSng"
  - "vb.CDec"
  - "CBool"
  - "CStr"
  - "vb.CULng"
  - "CDec"
  - "CVErr"
  - "CDbl"
  - "CShort"
  - "vb.CObj"
  - "vb.CVErr"
  - "CULng"
  - "vb.cdbl"
  - "vb.cbool"
  - "CObj"
  - "CDate"
  - "CLng"
  - "vb.cstr"
  - "vb.cbyte"
  - "vb.clng"
  - "vb.CChar"
  - "CUShort"
  - "vb.CUInt"
  - "vb.cint"
  - "vb.CShort"
  - "CInt"
  - "CUInt"
  - "CChar"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "CDate function"
  - "CByte function"
  - "Integer data type, converting"
  - "string conversion, conversion functions"
  - "fractions"
  - "data types [Visual Basic], converting"
  - "text, converting"
  - "CDec function"
  - "Char data type, converting"
  - "type conversion, functions for"
  - "Single data type, converting"
  - "numbers, rounding"
  - "rounding numbers, type conversion"
  - "CUShort function"
  - "Long data type, converting"
  - "return values, data types"
  - "single-precision numbers, converting"
  - "data type conversion, functions for"
  - "CStr function"
  - "times, converting"
  - "CSng function"
  - "conversions, type conversion functions"
  - "CBool function"
  - "CDbl function"
  - "CUInt function"
  - "Currency data type, conversion functions"
  - "numbers, converting"
  - "Double data type, converting"
  - "CLng function"
  - "CSByte function"
  - "double-precision numbers"
  - "Decimal data type, converting"
  - "Boolean data type, converting"
  - "integers, type conversion functions"
  - "dates, converting"
  - "CULng function"
  - "CInt function"
  - "Date data type, converting"
  - "Byte data type, converting"
  - "String data type, converting"
  - "CChar function"
  - "banker's rounding"
  - "Short data type, converting"
  - "rounding numbers, banker's rounding"
  - "type conversion, Visual Basic vs. .NET Framework"
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Type Conversion Functions (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Ces fonctions sont compilées "inline", c'est\-à\-dire que le code de conversion fait partie du code qui évalue l'expression.  Parfois, aucune procédure n'est appelée pour effectuer la conversion, ce qui permet d'améliorer les performances.  Chaque fonction convertit une expression en un type de données spécifique.  
  
## Syntaxe  
  
```  
CBool(expression)  
CByte(expression)  
CChar(expression)  
CDate(expression)  
CDbl(expression)  
CDec(expression)  
CInt(expression)  
CLng(expression)  
CObj(expression)  
CSByte(expression)  
CShort(expression)  
CSng(expression)  
CStr(expression)  
CUInt(expression)  
CULng(expression)  
CUShort(expression)  
```  
  
## Élément  
 `expression`  
 Obligatoire.  Toute expression du type de données source.  
  
## Type de données de la valeur de retour  
 Le nom de la fonction détermine le type de données de la valeur qu'elle retourne, comme l'illustre le tableau suivant.  
  
|Nom de la fonction|Type de données retourné|Plage de l'argument `expression`|  
|------------------------|------------------------------|--------------------------------------|  
|`CBool`|[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Toute expression numérique, `Char` ou `String` valide.|  
|`CByte`|[Byte Data Type](../../../visual-basic/language-reference/data-types/byte-data-type.md)|0 à 255 \(non signé\) ; les parties fractionnaires sont arrondies.<sup>1</sup>|  
|`CChar`|[Char Data Type](../../../visual-basic/language-reference/data-types/char-data-type.md)|Toute expression `Char` ou `String` valide ; seul le premier caractère d'un `String` est converti ; la valeur peut être comprise entre 0 et 65 535 \(non signé\).|  
|`CDate`|[Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md)|Toute représentation valide de la date et de l'heure.|  
|`CDbl`|[Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md)|\-1,79769313486231570E\+308 à \-4,94065645841246544E\-324 pour les valeurs négatives ; 4,94065645841246544E\-324 à 1,79769313486231570E\+308 pour les valeurs positives.|  
|`CDec`|[Decimal Data Type](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|\+\/\-79 228 162 514 264 337 593 543 950 335 pour les nombres sans décimales.  La plage de valeurs des nombres à 28 décimales est  \+\/\-7,9228162514264337593543950335.  Le plus petit nombre différent de zéro est 0,0000000000000000000000000001 \(\+\/\-1E\-28\).|  
|`CInt`|[Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)|\-2 147 483 648 à 2 147 483 647 ; les parties fractionnaires sont arrondies.<sup>1</sup>|  
|`CLng`|[Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md)|\-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807 ; les parties fractionnaires sont arrondies.<sup>1</sup>|  
|`CObj`|[Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)|Toute expression valide.|  
|`CSByte`|[SByte Data Type](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|\-128 à 127 ; les parties fractionnaires sont arrondies.<sup>1</sup>|  
|`CShort`|[Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)|\-32 768 à 32 767 ; les parties fractionnaires sont arrondies.<sup>1</sup>|  
|`CSng`|[Single Data Type](../../../visual-basic/language-reference/data-types/single-data-type.md)|\-3,402823E\+38 à \-1,401298E\-45 pour les valeurs négatives ; 1,401298E\-45 à 3,402823E\+38 pour les valeurs positives.|  
|`CStr`|[String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md)|Les valeurs retournées pour `CStr` dépendent de l'argument `expression`.  Consultez [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|  
|`CUInt`|[UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|0 à 4 294 967 295 \(non signé\) ; les parties fractionnaires sont arrondies.<sup>1</sup>|  
|`CULng`|[ULong Data Type](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|0 à 18 446 744 073 709 551 615 \(non signé\) ; les parties fractionnaires sont arrondies.<sup>1</sup>|  
|`CUShort`|[UShort Data Type](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|0 à 65 535 \(non signé\) ; les parties fractionnaires sont arrondies.<sup>1</sup>|  
  
 <sup>1</sup> Les parties fractionnaires peuvent faire l'objet d'un type spécial d'arrondissement nommé *arrondi bancaire*.  Consultez « Notes » pour obtenir plus d'informations.  
  
## Notes  
 En règle générale, vous devez utiliser les fonctions de conversion de Visual Basic de préférence aux méthodes .NET Framework, telles que `ToString()`, sur la classe <xref:System.Convert>, sur une structure de type ou sur une classe.  Les fonctions de Visual Basic sont conçues pour une interaction optimale avec le code Visual Basic ; elles permettent également de raccourcir votre code source et d'en faciliter la lecture.  En outre, les méthodes de conversion .NET Framework ne produisent pas toujours les mêmes résultats que les fonctions Visual Basic, par exemple, lors de la conversion de `Boolean` en `Integer`.  Pour plus d'informations, consultez [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## Comportement  
  
-   **Contrainte.** En général, vous pouvez utiliser des fonctions de conversion des types de données pour forcer les résultats d'une opération à correspondre à un type de données particulier au lieu du type de données par défaut.  Par exemple, utilisez `CDec` pour fonctionner en arithmétique décimale et non en arithmétique en simple précision, en double précision ou en arithmétique sur des nombres entiers.  
  
-   **Échec des conversions.** Si le `expression` passé à la fonction se trouve en dehors de la plage du type de données dans lequel il doit être converti, un <xref:System.OverflowException> se produit.  
  
-   **Parties fractionnaires.** Lorsque vous convertissez une valeur non entière dans un type entier, les fonctions de conversion d'entiers \(`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng` et `CUShort`\) suppriment la partie fractionnaire et arrondissent la valeur au nombre entier le plus proche.  
  
     Si la partie fractionnaire est exactement égale à 0,5, les fonctions de conversion d'entier l'arrondissent toujours au nombre entier pair le plus proche.  Par exemple, 0,5 est arrondi à 0, tandis que 1,5 et 2,5 sont arrondis à 2.  Cela est parfois appelé l'*arrondi bancaire*, et son objectif est de compenser un écart qui pourrait s'accumuler lors de l'ajout de plusieurs nombres similaires.  
  
     `CInt` et `CLng` diffèrent des fonctions <xref:Microsoft.VisualBasic.Conversion.Int%2A> et <xref:Microsoft.VisualBasic.Conversion.Fix%2A> qui tronquent, au lieu d'arrondir, la partie fractionnaire d'un nombre.  De plus, `Fix` et `Int` retournent toujours une valeur du même type de données que celui que vous avez passé.  
  
-   **Conversions date\/heure.** Utilisez la fonction <xref:Microsoft.VisualBasic.Information.IsDate%2A> pour déterminer si une valeur peut être convertie en une date et une heure.  `CDate` reconnaît des littéraux de date et des littéraux d'heure mais pas de valeurs numériques.  Pour convertir une valeur `Date` Visual Basic 6.0 en une valeur  `Date` dans Visual Basic 2005 ou une version ultérieure, vous pouvez utiliser la méthode <xref:System.DateTime.FromOADate%2A?displayProperty=fullName>.  
  
-   **Valeurs date\/heure neutres.** Le [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) contient toujours des informations concernant la date et l'heure.  Dans le cadre de la conversion de type, Visual Basic considère la valeur 1\/1\/0001 \(le 1er janvier de l'année 1\) comme une *valeur neutre* pour la date et 00:00:00 \(minuit\) comme une valeur neutre pour l'heure.  Si vous convertissez une valeur `Date` en une chaîne, `CStr` n'inclut pas de valeurs neutres dans la chaîne obtenue.  Par exemple, si vous convertissez `#January 1, 0001 9:30:00#` en une chaîne, la chaîne obtenue est "9:30:00 AM" ; les informations relatives à la date sont supprimées.  Cependant, les informations de date sont toujours présentes dans la valeur `Date` d'origine et peuvent être récupérées à l'aide de fonctions, telles que la fonction <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
-   **Respect de la culture.** Les fonctions de conversion de type impliquant des chaînes effectuent des conversions en fonction des paramètres de culture actuels de l'application.  Par exemple, `CDate` reconnaît les formats de date définis dans les paramètres régionaux de votre système.  Vous devez fournir le jour, le mois et l'année selon l'ordre correct pour vos paramètres régionaux ; sinon, la date pourrait être incorrectement interprétée.  Les formats de date complets ne sont pas reconnus s'ils contiennent une chaîne précisant un jour de la semaine \(par exemple, "mercredi"\).  
  
     Si vous devez effectuer une conversion depuis ou vers une représentation sous forme de chaîne d'une valeur dans un format différent de celui spécifié dans vos paramètres régionaux, vous ne pouvez pas utiliser les fonctions de conversion de type Visual Basic.  Pour cela, utilisez les méthodes `ToString(IFormatProvider)` et `Parse(String, IFormatProvider)` du type de cette valeur.  Par exemple, utilisez <xref:System.Double.Parse%2A?displayProperty=fullName> lors de la conversion d'une chaîne en un `Double` et utilisez <xref:System.Double.ToString%2A?displayProperty=fullName> lors de la conversion d'une valeur de type `Double` en une chaîne.  
  
## CType, fonction  
 La [fonction CType](../../../visual-basic/language-reference/functions/ctype-function.md) accepte un deuxième argument, `typename`, et force `expression` à correspondre à `typename`, où `typename` peut être n'importe quel type de données, structure, classe ou interface vers lequel une conversion valide existe.  
  
 Pour obtenir une comparaison entre `CType` et les autres mots clés de conversion de type, consultez [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) et [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
## CBool, exemple  
 L'exemple suivant utilise la fonction `CBool` pour convertir des expressions en valeurs `Boolean`.  Si une expression prend une valeur différente de zéro, `CBool` retourne `True` ; sinon, elle retourne `False`.  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_1.vb)]  
  
## CByte, exemple  
 L'exemple suivant utilise la fonction `CByte` pour convertir une expression en un `Byte`.  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_2.vb)]  
  
## CChar, exemple  
 L'exemple suivant utilise la fonction `CChar` pour convertir le premier caractère d'une expression `String` en un type `Char`.  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_3.vb)]  
  
 L'argument d'entrée de `CChar` doit être du type de données `Char` ou `String`.  Vous ne pouvez pas utiliser `CChar` pour convertir un nombre en un caractère, car `CChar` ne peut pas accepter un type de données numérique.  L'exemple suivant obtient un nombre représentant un point de code \(code de caractère\) et le convertit dans le caractère correspondant.  Il utilise la fonction <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> pour obtenir la chaîne de chiffres, `CInt` pour convertir la chaîne en type `Integer` et `ChrW` pour convertir le nombre en type `Char`.  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_4.vb)]  
  
## CDate, exemple  
 L'exemple suivant utilise la fonction `CDate` pour convertir des chaînes en valeurs `Date`.  En général, les dates et les heures codées de manière irréversible comme des chaînes \(comme l'illustre cet exemple\) ne sont pas recommandées.  Utilisez plutôt des littéraux de date et d'heure, tels que \#Feb 12, 1969\# et \#4:45:23 PM\#.  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_5.vb)]  
  
## Exemple CDbl  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_6.vb)]  
  
## CDec, exemple  
 L'exemple suivant utilise la fonction `CDec` pour convertir une valeur numérique en `Decimal`.  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_7.vb)]  
  
## CInt, exemple  
 L'exemple suivant utilise la fonction `CInt` pour convertir une valeur en `Integer`.  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_8.vb)]  
  
## Exemple CLng  
 L'exemple suivant utilise la fonction `CLng` pour convertir des valeurs en `Long`.  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_9.vb)]  
  
## CObj, exemple  
 L'exemple suivant utilise la fonction `CObj` pour convertir une valeur numérique en `Object`.  La variable `Object` contient uniquement un pointeur de quatre octets, qui pointe vers la valeur `Double` qui lui est assignée.  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_10.vb)]  
  
## Exemple CSByte  
 L'exemple suivant utilise la fonction `CSByte` pour convertir une valeur numérique en `SByte`.  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_11.vb)]  
  
## CShort, exemple  
 L'exemple suivant utilise la fonction `CShort` pour convertir une valeur numérique en `Short`.  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_12.vb)]  
  
## Exemple CSng  
 L'exemple suivant utilise la fonction `CSng` pour convertir des valeurs en `Single`.  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_13.vb)]  
  
## Exemple CStr  
 L'exemple suivant utilise la fonction `CStr` pour convertir une valeur numérique en `String`.  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_14.vb)]  
  
 L'exemple suivant utilise la fonction `CStr` pour convertir des valeurs `Date` en valeurs `String`.  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_15.vb)]  
  
 `CStr` retourne toujours une valeur `Date` au format de date courte des paramètres régionaux en cours, par exemple, "15\/06\/2003 16:35:47".  Toutefois, `CStr` supprime les *valeurs neutres* de 1\/1\/0001 pour la date et 00:00:00 pour l'heure.  
  
 Pour plus d'informations sur les valeurs retournées par `CStr`, consultez [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).  
  
## Exemple CUInt  
 L'exemple suivant utilise la fonction `CUInt` pour convertir une valeur numérique en `UInteger`.  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_16.vb)]  
  
## CULng, exemple  
 L'exemple suivant utilise la fonction `CULng` pour convertir une valeur numérique en `ULong`.  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_17.vb)]  
  
## CUShort, exemple  
 L'exemple suivant utilise la fonction `CUShort` pour convertir une valeur numérique en `UShort`.  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/type-conversion-functions_18.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>   
 <xref:Microsoft.VisualBasic.Strings.Format%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Str%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>   
 [Conversion Functions](../../../visual-basic/language-reference/functions/conversion-functions.md)   
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)