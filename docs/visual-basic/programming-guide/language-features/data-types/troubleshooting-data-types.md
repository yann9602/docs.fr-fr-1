---
title: "Dépannage des types de données (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4d2fb1cd1be9c88ad0dd413eedb8a226fe59f41e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-data-types-visual-basic"></a>Dépannage des types de données (Visual Basic)
Cette page répertorie certains problèmes courants qui peuvent se produire lorsque vous effectuez des opérations sur les types de données intrinsèques.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Expressions en virgule flottante ne sont pas considérés comme égal  
 Lorsque vous travaillez avec des nombres à virgule flottante ([unique Type de données](../../../../visual-basic/language-reference/data-types/single-data-type.md) et [Type de données Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)), souvenez-vous qu’elles sont stockées sous forme de fractions binaires. Cela signifie qu’ils ne peuvent pas contenir une représentation exacte d’une quantité qui n’est pas une fraction binaire (sous la forme k / (2 ^ n) où k et n sont des entiers). Par exemple, 0,5 (= 1/2) et 0,3125 (= 5/16) peuvent être considérés comme des valeurs précises, tandis que 0,2 (= 1/5) et 0,3 (= 3/10) peuvent être uniquement des approximations.  
  
 Pour cette raison imprécision, vous ne pouvez pas compter sur des résultats exacts lorsque vous utilisez des valeurs à virgule flottante. En particulier, les deux valeurs sont égales en théorie peuvent ont des représentations légèrement différentes.  
  
| Pour comparer des quantités à virgule flottante | 
|---| 
|1.  Calculer la valeur absolue de leur différence à l’aide de la <xref:System.Math.Abs%2A> méthode de la <xref:System.Math> classe dans le <xref:System> espace de noms.<br />2.  Déterminez une différence maximale acceptable, par exemple, vous pouvez considérer les deux quantités soient égaux pour des raisons pratiques si leur différence n’est pas supérieure.<br />3.  Comparez la valeur absolue de la différence à la différence acceptable.|  
  
 L’exemple suivant montre une comparaison correcte et incorrecte de deux `Double` valeurs.  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 L’exemple précédent utilise la <xref:System.Double.ToString%2A> méthode de la <xref:System.Double> structure afin qu’il peut spécifier une meilleure précision que les `CStr` mot clé. La valeur par défaut est 15 chiffres, mais le format « G17 » l’étend à 17 chiffres.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod, opérateur ne retourne pas de résultat exact  
 En raison de l’imprécision du stockage à virgule flottante, le [MOD, opérateur](../../../../visual-basic/language-reference/operators/mod-operator.md) peut retourner un résultat inattendu lorsqu’au moins un des opérandes est à virgule flottante.  
  
 Le [Type de données Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) n’utilise pas de représentation à virgule flottante. Plusieurs nombres qui sont inexacts dans `Single` et `Double` sont exacts dans `Decimal` (par exemple, 0,2 et 0,3). Bien que l’arithmétique est plus lent dans `Decimal` que dans à virgule flottante, il peut être important de réduire les performances pour obtenir une meilleure précision.  
  
|Pour trouver le reste entier de quantités à virgule flottante|  
|---|  
|1.  Déclarer des variables en tant que `Decimal`.<br />2.  Utilisez le caractère de type de littéral `D` pour forcer les littéraux à `Decimal`, au cas où leurs valeurs sont trop élevées pour la `Long` type de données.|  
  
 L’exemple suivant montre l’imprécision potentielle des opérandes à virgule flottante.  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 L’exemple précédent utilise la <xref:System.Double.ToString%2A> méthode de la <xref:System.Double> structure afin qu’il peut spécifier une meilleure précision que les `CStr` mot clé. La valeur par défaut est 15 chiffres, mais le format « G17 » l’étend à 17 chiffres.  
  
 Étant donné que `zeroPointTwo` est `Double`, sa valeur pour 0,2 est une fraction binaire se répétant avec une valeur stockée de 0,20000000000000001. Divise 2,0 par cette quantité 9,9999999999999995 avec un reste de 0,19999999999999991.  
  
 Dans l’expression de `decimalRemainder`, le caractère de type littéral `D` force les deux opérandes de `Decimal`, et 0,2 a une représentation précise. Par conséquent la `Mod` opérateur Obtient le reste attendu de 0,0.  
  
 Notez qu’il n’est pas suffisant pour déclarer `decimalRemainder` comme `Decimal`. Vous devez également forcer les littéraux à `Decimal`, ou ils utilisent `Double` par défaut et `decimalRemainder` reçoit la même valeur inexacte que `doubleRemainder`.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Type booléen ne convertit pas correctement en Type numérique  
 [Type de données booléen](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) valeurs ne sont pas stockées sous forme de nombres et les valeurs stockées ne sont pas destinées à être équivalentes en nombres. Pour la compatibilité avec les versions antérieures, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fournit des mots clés de conversion ([CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`, et ainsi de suite) pour effectuer des conversions entre `Boolean` et des types numériques. Toutefois, autres langages parfois effectuer ces conversions différemment, comme le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] méthodes.  
  
 Vous devez jamais écrire du code qui s’appuie sur des valeurs numériques équivalentes pour `True` et `False`. Chaque fois que possible, vous devez limiter l’utilisation de `Boolean` variables aux valeurs logiques pour lesquelles elles sont conçues. Si vous devez combiner `Boolean` et des valeurs numériques, assurez-vous que vous comprenez la méthode de conversion que vous sélectionnez.  
  
### <a name="conversion-in-visual-basic"></a>Conversion en Visual Basic  
 Lorsque vous utilisez la `CType` ou `CBool` mots clés de conversion pour convertir les types de données numériques à `Boolean`, 0 devient `False` et toutes les autres valeurs deviennent `True`. Lorsque vous effectuez une conversion `Boolean` valeurs en types numériques à l’aide de mots clés de conversion, `False` devient 0 et `True` devient -1.  
  
### <a name="conversion-in-the-framework"></a>Conversion dans le Framework  
 Le <xref:System.Convert.ToInt32%2A> méthode de la <xref:System.Convert> classe dans le <xref:System> convertit de l’espace de noms `True` à + 1.  
  
 Si vous devez convertir un `Boolean` la valeur en un type de données numérique, soyez prudent sur la méthode de conversion que vous utilisez.  
  
## <a name="character-literal-generates-compiler-error"></a>Le littéral de caractère génère l’erreur du compilateur  
 En l’absence de caractères de n’importe quel type [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] utilise par défaut pour les littéraux, les types de données. Le type par défaut pour un littéral de caractère, entourée de guillemets (`" "`) — est `String`.  
  
 Le `String` type de données ne s’étend pas à la [Type de données Char](../../../../visual-basic/language-reference/data-types/char-data-type.md). Cela signifie que si vous souhaitez assigner un littéral à un `Char` variable, vous devez effectuer une conversion restrictive ou forcer le littéral à la `Char` type.  

|Pour créer un caractère littéral à affecter à une variable ou une constante|
|---|  
|1.  Déclarez la variable ou une constante en tant que `Char`.<br />2.  Placez la valeur de caractère entre guillemets (`" "`).<br />3.  Suivez les guillemets doubles fermants avec le caractère de type littéral `C` pour forcer le littéral à `Char`. Cela est nécessaire si le commutateur de la vérification de type ([Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est `On`, et elle est recommandée dans tous les cas.|  
  
 L’exemple suivant montre des assignations infructueuses et réussies d’un littéral à un `Char` variable.  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 Il existe toujours un risque en utilisant les conversions restrictives, car elles peuvent échouer au moment de l’exécution. Par exemple, une conversion de `String` à `Char` peut échouer si le `String` valeur contient plusieurs caractères. Par conséquent, il est mieux de programmation à utiliser le `C` caractère de type.  
  
## <a name="string-conversion-fails-at-run-time"></a>Échec de la Conversion de chaîne en cours d’exécution  
 Le [Type de données String](../../../../visual-basic/language-reference/data-types/string-data-type.md) participe à très peu de conversions étendues. `String`s’étend uniquement à lui-même et `Object`et uniquement `Char` et `Char()` (un `Char` tableau) s’étendent à `String`. C’est parce que `String` variables et les constantes peuvent contenir des valeurs qui ne peut pas contenir des autres types de données.  
  
 Lorsque la vérification du type de commutateur ([Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est `On`, le compilateur rejette toutes les conversions restrictives implicites. Comprennent celles qui impliquent `String`. Votre code peut toujours utiliser les mots clés de conversion tels que `CStr` et [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md), qui invitent le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pour essayer la conversion.  
  
> [!NOTE]
>  L’erreur de conversion restrictive est supprimée pour les conversions entre les éléments dans un `For Each…Next` collection à la variable de contrôle de boucle. Pour plus d’informations et d’exemples, consultez la section « Conversions restrictives » dans [For Each... L’instruction suivante](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Protection de la Conversion restrictive  
 L’inconvénient des conversions restrictives, qu’elles peuvent échouer au moment de l’exécution. Par exemple, si un `String` variable contient tout autre que « True » ou « False », elle ne peut pas être convertie en `Boolean`. S’il contient des caractères de ponctuation, la conversion en un type numérique échoue. Sauf si vous savez que votre `String` variable contient toujours des valeurs que le type de destination peut accepter, vous ne devez pas essayer une conversion.  
  
 Si vous devez convertir à partir de `String` à un autre type de données, la procédure la plus sûre consiste à placer la tentative de conversion dans le [essayez... Catch... Instruction finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Cela vous permet de traiter un échec d’exécution.  
  
### <a name="character-arrays"></a>Tableaux de caractères  
 Un seul `Char` et un tableau de `Char` les deux s’étendent à des éléments `String`. Toutefois, `String` ne s’étend pas à `Char()`. Pour convertir un `String` valeur un `Char` tableau, vous pouvez utiliser la <xref:System.String.ToCharArray%2A> méthode de la <xref:System.String?displayProperty=nameWithType> classe.  
  
### <a name="meaningless-values"></a>Valeurs sans signification  
 En règle générale, `String` valeurs ne sont pas significatives dans d’autres types de données et la conversion est très artificielle et dangereuse. Chaque fois que possible, vous devez limiter l’utilisation de `String` variables aux séquences de caractère pour lesquelles elles sont conçues. Vous ne devez jamais écrire le code qui s’appuie sur des valeurs équivalentes dans d’autres types.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Caractères de type](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Fonctions de conversion de types](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Utilisation efficace des types de données](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
