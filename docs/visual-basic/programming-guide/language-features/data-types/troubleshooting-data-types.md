---
title: "Troubleshooting Data Types (Visual Basic) | Microsoft Docs"
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
  - "Char data type, converting"
  - "Decimal data type, conversions"
  - "data types [Visual Basic], troubleshooting"
  - "literals, default types"
  - "type characters, literal"
  - "Mod operator [Visual Basic], in floating-point operations"
  - "troubleshooting Visual Basic, data types"
  - "troubleshooting data types"
  - "floating-point numbers, precision"
  - "Boolean data type, converting"
  - "literal types"
  - "literal type characters"
  - "floating-point numbers, imprecision"
  - "String data type, converting"
  - "floating-point numbers, comparison"
  - "floating-point numbers"
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# Troubleshooting Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette page répertorie des problèmes courants qui peuvent se produire lorsque vous exécutez des opérations sur des types de données intrinsèques.  
  
## Les expressions à virgule flottante ne sont pas considérées comme égales  
 Lorsque vous utilisez des nombres à virgule flottante \([Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md) et [Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md)\), n'oubliez pas qu'ils sont stockés sous forme de fractions binaires.  En d'autres termes, ils ne peuvent pas contenir une représentation exacte d'une quantité qui n'est pas une fraction binaire \(sous la forme k \/ \(2 ^ n\) où k et n désignent des entiers\).  Par exemple, 0,5 \(\= 1\/2\) et 0,3125 \(\= 5\/16\) peuvent être considérés comme des valeurs précises, tandis que 0,2 \(\= 1\/5\) et 0,3 \(\= 3\/10\) peuvent être uniquement des approximations.  
  
 En raison de cette imprécision, vous ne pouvez pas vous baser sur des résultats exacts lorsque vous utilisez des valeurs à virgule flottante.  En particulier, deux valeurs qui sont théoriquement égales peuvent présenter des représentations légèrement différentes.  
  
||  
|-|  
|Pour comparer des quantités à virgule flottante|  
|1.  Calculez la valeur absolue de leur différence, à l'aide de la méthode <xref:System.Math.Abs%2A> de la classe <xref:System.Math> dans l'espace de noms <xref:System>.<br />2.  Déterminez une différence maximale acceptable : par exemple, vous pouvez considérer les deux quantités comme étant égales pour des raisons pratiques si leur différence n'est pas supérieure.<br />3.  Comparez la valeur absolue de la différence à la différence acceptable.|  
  
 L'exemple suivant présente une comparaison correcte et incorrecte de deux valeurs `Double`.  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/visualbasic/troubleshooting-data-types_1.vb)]  
  
 L'exemple précédent utilise la méthode <xref:System.Double.ToString%2A> de la structure <xref:System.Double> pour spécifier une plus grande précision que le mot clé `CStr`.  La valeur par défaut est 15 chiffres, mais le format « G17 » l'étend à 17 chiffres.  
  
## L'opérateur Mod ne retourne pas de résultat précis  
 En raison de l'imprécision du stockage à virgule flottante, [Mod, opérateur](../../../../visual-basic/language-reference/operators/mod-operator.md) peut retourner un résultat inattendu lorsqu'au moins un des opérandes est à virgule flottante.  
  
 [Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) n'utilise pas la représentation à virgule flottante.  Plusieurs nombres qui sont inexacts dans `Single` et `Double` sont exacts dans `Decimal` \(par exemple, 0,2 et 0,3\).  Bien que l'arithmétique soit plus lente en `Decimal` qu'en virgule flottante, cela peut valoir la peine de réduire les performances pour obtenir une plus grande précision.  
  
||  
|-|  
|Pour rechercher le reste entier de quantités à virgule flottante|  
|1.  Déclarez les variables comme `Decimal`.<br />2.  Utilisez le caractère de type de littéral `D` pour forcer les littéraux sur la valeur `Decimal`, au cas où leurs valeurs sont trop grandes pour le type de données `Long`.|  
  
 L'exemple suivant montre l'imprécision potentielle des opérandes à virgule flottante.  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/visualbasic/troubleshooting-data-types_2.vb)]  
  
 L'exemple précédent utilise la méthode <xref:System.Double.ToString%2A> de la structure <xref:System.Double> pour spécifier une plus grande précision que le mot clé `CStr`.  La valeur par défaut est 15 chiffres, mais le format « G17 » l'étend à 17 chiffres.  
  
 Étant donné que `zeroPointTwo` a la valeur `Double`, sa valeur pour 0,2 est une fraction binaire se répétant à l'infini avec une valeur stockée de 0,20000000000000001.  Lorsqu'on divise 2,0 par cette quantité, on obtient 9,9999999999999995 avec un reste de 0,19999999999999991.  
  
 Dans l'expression pour `decimalRemainder`, le caractère de type de littéral `D` force les deux opérandes sur la valeur `Decimal` et 0,2 a une représentation précise.  Par conséquent, l'opérateur `Mod` obtient le reste attendu de 0,0.  
  
 Notez que cela n'est pas suffisant pour déclarer `decimalRemainder` comme `Decimal`.  Vous devez également forcer les littéraux sur la valeur `Decimal`, ou ils utilisent la valeur par défaut `Double` et `decimalRemainder` reçoit la même valeur inexacte que `doubleRemainder`.  
  
## Impossible de convertir correctement le type Boolean en type numérique  
 Les valeurs [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) ne sont pas stockées en tant que nombres et les valeurs stockées ne sont pas destinées à être équivalentes aux nombres.  Pour garantir la compatibilité avec les versions antérieures, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] fournit des mots clés de conversion \([CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`, etc.\) pour effectuer des conversions entre des types `Boolean` et numériques.  Toutefois, d'autres langages exécutent parfois différemment ces conversions, comme c'est le cas pour les méthodes du [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)].  
  
 Vous ne devez jamais écrire un code qui repose sur les valeurs numériques équivalentes à `True` et `False`.  Autant que possible, limitez l'utilisation des variables `Boolean` aux valeurs logiques pour lesquelles elles sont conçues.  Si vous devez combiner `Boolean` et des valeurs numériques, assurez\-vous que vous comprenez la méthode de conversion que vous sélectionnez.  
  
### Conversion dans Visual Basic  
 Lorsque vous utilisez les mots clés de conversion `CType` ou `CBool` pour convertir des types de données numériques en `Boolean`, 0 devient `False` et toutes les autres valeurs deviennent `True`.  Lorsque vous convertissez des valeurs `Boolean` en types numériques à l'aide de mots clés de conversion, `False` devient 0 et `True` devient \-1.  
  
### Conversion dans la structure  
 La méthode <xref:System.Convert.ToInt32%2A> de la classe <xref:System.Convert> dans l'espace de noms <xref:System> convertit `True` en \+1.  
  
 Si vous devez convertir une valeur `Boolean` en un type de données numériques, choisissez attentivement la méthode de conversion à utiliser.  
  
## Un littéral de caractère génère une erreur du compilateur  
 En l'absence de caractères de type, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] utilise des types de données par défaut pour les littéraux.  Le type par défaut pour un littéral de caractère — mis entre guillemets \(`" "`\) — est `String`.  
  
 Le type de données `String` ne s'étend pas au [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).  Cela signifie que si vous souhaitez assigner un littéral à une variable `Char`, vous devez soit effectuer une conversion restrictive soit forcer le littéral sur le type `Char`.  
  
||  
|-|  
|Pour créer un littéral de caractère à assigner à une variable ou une constante|  
|1.  Déclarez la variable ou la constante comme `Char`.<br />2.  Entourez la valeur du caractère par des guillemets \(`" "`\).<br />3.  Faites suivre les guillemets doubles fermants du caractère de type de littéral `C` pour forcer le littéral sur la valeur `Char`.  Cette procédure est nécessaire si le commutateur de vérification de type \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) a la valeur `On`, et elle est recommandée dans tous les cas.|  
  
 L'exemple suivant présente des assignations infructueuses et réussies d'un littéral sur une variable `Char`.  
  
 [!CODE [VbVbalrStatements#49](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrStatements#49)]  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/visualbasic/troubleshooting-data-types_4.vb)]  
  
 Il existe toujours un risque lié à l'utilisation de conversions restrictives, car elles peuvent échouer au moment de l'exécution.  Par exemple, une conversion de `String` en `Char` peut échouer si la valeur `String` contient plusieurs caractères.  Par conséquent, l'utilisation du caractère de type `C` est préconisée.  
  
## Échec de la conversion de chaîne au moment de l'exécution  
 Le type de données String \([String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)\) participe à très peu de conversions étendues.  `String` s'étend uniquement à lui\-même et à `Object`, et seuls `Char` et `Char()` \(tableau `Char`\) s'étendent à `String`.  Cela s'explique par le fait que les variables et les constantes `String` peuvent contenir des valeurs qui ne sont pas prises en charge par d'autres types de données.  
  
 Lorsque le commutateur de vérification de type \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) a la valeur on `On`, le compilateur rejette toutes les conversions restrictives implicites.  Y compris celles qui impliquent `String`.  Votre code peut toujours utiliser les mots clés de conversion tels que `CStr` et [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md), qui invitent le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] à tenter la conversion.  
  
> [!NOTE]
>  L'erreur de conversion restrictive est supprimée pour les conversions à partir des éléments d'une collection `For Each…Next` vers la variable de contrôle de boucle.  Pour plus d'informations et d'exemples, consultez la section « Conversions restrictives » dans [For Each...Next, instruction](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### Protection de la conversion restrictive  
 L'inconvénient des conversions restrictives est qu'elles peuvent échouer au moment de l'exécution.  Par exemple, si une variable `String` contient une valeur autre que « True » ou « False », elle ne peut pas être convertie en `Boolean`.  Si elle contient des caractères de ponctuation, la conversion en un type numérique échoue.  Vous ne devez pas tenter de conversion sauf si vous savez que votre variable `String` contient toujours des valeurs que le type de destination peut accepter.  
  
 Si vous devez effectuer une conversion de `String` en un autre type de données, la procédure la plus sûre consiste à insérer la conversion tentée dans [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  Cela vous permet de gérer les défaillances au moment de l'exécution.  
  
### Tableaux de caractères  
 Un élément `Char` unique et un tableau d'éléments `Char` s'étendent tous deux à `String`.  Toutefois, `String` ne s'étend pas à `Char()`.  Pour convertir une valeur `String` en un tableau `Char`, vous pouvez utiliser la méthode <xref:System.String.ToCharArray%2A> de la classe <xref:System.String?displayProperty=fullName>.  
  
### Valeurs sans signification  
 En général, les valeurs `String` ne sont pas explicites dans d'autres types de données, et la conversion est très artificielle et dangereuse.  Autant que possible, limitez l'utilisation des variables `String` aux séquences de caractère pour lesquelles elles sont conçues.  Vous ne devez jamais écrire un code qui dépend de valeurs équivalentes dans d'autres types.  
  
## Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)