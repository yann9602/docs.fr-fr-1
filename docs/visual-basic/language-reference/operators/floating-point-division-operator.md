---
title: "/, Opérateur (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./
dev_langs:
- VB
helpviewer_keywords:
- division operator, floating point
- floating-point numbers, division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators, division
- division, by zero
- operators [Visual Basic], division
- division operator, syntax
- / operator [Visual Basic]
- math operators
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 18
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
ms.openlocfilehash: 71b4f64f6deeb334412c87131ccd9480620f284f
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-visual-basic"></a>/, opérateur (Visual Basic)
Effectue la division de deux nombres et retourne un résultat à virgule flottante.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
expression1 / expression2  
```  
  
## <a name="parts"></a>Composants  
 `expression1`  
 Obligatoire. Toute expression numérique.  
  
 `expression2`  
 Obligatoire. Toute expression numérique.  
  
## <a name="supported-types"></a>Types pris en charge  
 Tous les types numériques, y compris les types non signés et à virgule flottante et `Decimal`.  
  
## <a name="result"></a>Résultat  
 Le résultat est le quotient entier de `expression1` divisé par `expression2`, y compris tout élément restant.  
  
 Le [\, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) renvoie le quotient entier, sans le reste.  
  
## <a name="remarks"></a>Remarques  
 Le type de données du résultat dépend des types des opérandes. Le tableau suivant présente la façon dont le type de données du résultat est déterminé.  
  
|Types de données d’opérande|Type de données de résultat|  
|------------------------|----------------------|  
|Les deux expressions sont des types de données intégraux ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [octets](../../../visual-basic/language-reference/data-types/byte-data-type.md), [court](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [entier](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Une expression est un [unique](../../../visual-basic/language-reference/data-types/single-data-type.md) type de données et l’autre n’est pas un [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Une expression est un [décimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) type de données et l’autre n’est pas un [unique](../../../visual-basic/language-reference/data-types/single-data-type.md) ou un [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|Des expressions sont un [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) type de données|`Double`|  
  
 Avant d’effectuer la division, toutes les expressions numériques intégrales sont étendues à `Double`. Si vous affectez le résultat à un type intégral, Visual Basic essaie de convertir le résultat de `Double` à ce type. Cela peut lever une exception si le résultat ne tient pas dans ce type. En particulier, consultez « Tentative de Division par zéro » sur cette page d’aide.  
  
 Si `expression1` ou `expression2` a la valeur [rien](../../../visual-basic/language-reference/nothing.md), elle est considérée comme nulle.  
  
## <a name="attempted-division-by-zero"></a>Tentative de Division par zéro  
 Si `expression2` correspond à zéro, le `/` opérateur se comporte différemment pour les types de données différents d’opérande. Le tableau suivant répertorie les comportements possibles.  
  
|Types de données d’opérande|Comportement si `expression2` est égal à zéro|  
|------------------------|---------------------------------------|  
|Virgule flottante (`Single` ou `Double`)|Retourne l’infini (<xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity>), ou <xref:System.Double.NaN>(pas un nombre) si `expression1` est également zéro</xref:System.Double.NaN> </xref:System.Double.NegativeInfinity> </xref:System.Double.PositiveInfinity>|  
|`Decimal`|Lève une exception<xref:System.DivideByZeroException></xref:System.DivideByZeroException>|  
|Intégral (signé ou non signé)|Tentative de conversion en type intégral lève <xref:System.OverflowException>, car les types intégraux ne peut pas accepter <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, ou <xref:System.Double.NaN></xref:System.Double.NaN> </xref:System.Double.NegativeInfinity> </xref:System.Double.PositiveInfinity> </xref:System.OverflowException>|  
  
> [!NOTE]
>  Le `/` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `/` opérateur pour effectuer une division à virgule flottante. Le résultat est le quotient de deux opérandes.  
  
 [!code-vb[VbVbalrOperators&#16;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 Les expressions dans l’exemple précédent retournent les valeurs 2,5 et 3,333333. Notez que le résultat est toujours en virgule flottante (`Double`), même si les deux opérandes sont des constantes entières.  
  
## <a name="see-also"></a>Voir aussi  
 [/ =, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [\, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)   
 [Types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)   
 [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Priorité des opérateurs dans Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Opérateurs arithmétiques en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

