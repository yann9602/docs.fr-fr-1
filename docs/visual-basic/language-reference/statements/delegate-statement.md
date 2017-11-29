---
title: Delegate, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e79a261f74cbc7aa067af63629e31bedf65d163
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-statement"></a>Delegate, instruction
Utilisé pour déclarer un délégué. Un délégué est un type référence qui fait référence à un `Shared` d’un type ou à une méthode d’instance d’un objet de méthode. Toute procédure ayant des types de paramètres et de retour correspondants peut être utilisé pour créer une instance de cette classe déléguée. La procédure peut ensuite être appelée ultérieurement au moyen de l’instance de délégué.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`attrlist`|Facultatif. Liste des attributs qui s’appliquent à ce délégué. Les attributs multiples sont séparés par des virgules. Vous devez placer le [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md) figurant entre crochets («`<`« et »`>`»).|  
|`accessmodifier`|Facultatif. Spécifie le code pouvant accéder le délégué. Il peut s'agir d'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md). Tout code qui peut accéder à l’élément qui déclare le délégué peut y accéder.<br />-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md). Seul le code dans la classe du délégué ou une classe dérivée peut y accéder.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md). Seul le code dans le même assembly peut accéder au délégué.<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md). Seul le code dans l’élément qui déclare le délégué peut y accéder.<br /><br /> Vous pouvez spécifier `Protected Friend` pour activer l’accès à partir du code dans la classe du délégué, une classe dérivée ou le même assembly.|  
|`Shadows`|Facultatif. Indique que ce délégué redéclare et masque un élément de programmation portant le même nom ou un ensemble d’éléments surchargés, dans une classe de base. Vous pouvez occulter tout type d'élément déclaré par un autre type.<br /><br /> Un élément occulté n'est pas disponible à partir de la classe dérivée qui l'occulte, sauf à partir de l'emplacement où l'élément d'occultation est inaccessible. Par exemple, si un `Private` élément occulte un élément de la classe de base, le code qui n’est pas autorisé à accéder à la `Private` élément accède à l’élément de la classe de base à la place.|  
|`Sub`|Facultatif, mais `Sub` ou `Function` doit apparaître. Déclare cette procédure en tant que délégué `Sub` procédure qui ne retourne pas de valeur.|  
|`Function`|Facultatif, mais `Sub` ou `Function` doit apparaître. Déclare cette procédure en tant que délégué `Function` procédure qui retourne une valeur.|  
|`name`|Obligatoire. Nom du type délégué ; suit les conventions d’affectation de noms de variable standard.|  
|`typeparamlist`|Facultatif. Liste des paramètres de type pour ce délégué. Plusieurs paramètres de type sont séparés par des virgules. Éventuellement, chaque paramètre de type peut être déclaré variant à l’aide de `In` et `Out` modificateurs génériques. Vous devez placer le [Type liste](../../../visual-basic/language-reference/statements/type-list.md) entre parenthèses et introduire avec la `Of` (mot clé).|  
|`parameterlist`|Facultatif. Liste des paramètres qui sont passés à la procédure lorsqu’elle est appelée. Vous devez placer le [liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md) entre parenthèses.|  
|`type`|Obligatoire si vous spécifiez un `Function` procédure. Type de données de la valeur de retour.|  
  
## <a name="remarks"></a>Remarques  
 La `Delegate` instruction définit les types de paramètres et de retour d’une classe déléguée. Toute procédure ayant des paramètres et types de retour correspondants peut être utilisé pour créer une instance de cette classe déléguée. La procédure peut ensuite être appelée ultérieurement au moyen de l’instance de délégué, en appelant du délégué `Invoke` (méthode).  
  
 Délégués peuvent être déclarés au niveau de l’espace de noms, un module, une classe ou un niveau de la structure, mais pas dans une procédure.  
  
 Chaque classe déléguée définit un constructeur auquel les caractéristiques d’une méthode objet sont passées. L’argument d’un constructeur délégué doit être une référence à une méthode ou une expression lambda.  
  
 Pour spécifier une référence à une méthode, utilisez la syntaxe suivante :  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Le type de compilation de `expression` doit être le nom d’une classe ou d’une interface qui contient une méthode portant le nom spécifié, dont la signature corresponde à celle de la classe déléguée. La méthode `methodname` peut être une méthode partagée ou d’instance. `methodname` n’est pas facultatif, même si l’on crée un délégué pour la méthode par défaut de la classe.  
  
 Pour spécifier une expression lambda, utilisez la syntaxe suivante :  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 La signature de la fonction doit correspondre à celle du type délégué. Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Pour plus d’informations sur les délégués, consultez [délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `Delegate` instruction pour déclarer un délégué pour fonctionner sur deux nombres et de retourner un nombre. Le `DelegateTest` méthode prend une instance d’un délégué de ce type et l’utilise pour fonctionner sur des paires de numéros de.  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
 [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Guide pratique : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Types génériques en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
