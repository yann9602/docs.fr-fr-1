---
title: Delegate, instruction | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Delegate
dev_langs:
- VB
helpviewer_keywords:
- delegate keyword
- Delegate statement
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
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
ms.openlocfilehash: 9ac9e28c82f8a6b5a9c1398961d831c956a649e0
ms.lasthandoff: 03/13/2017

---
# <a name="delegate-statement"></a>Delegate, instruction
Utilisé pour déclarer un délégué. Un délégué est un type référence qui fait référence à un `Shared` d’un type ou à une méthode d’instance d’un objet de méthode. Toute procédure présentant des types de paramètres et de retour peut être utilisée pour créer une instance de cette classe déléguée. La procédure peut ensuite être appelée ultérieurement au moyen de l’instance de délégué.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`attrlist`|Facultatif. Liste des attributs qui s’appliquent à ce délégué. Les attributs multiples sont séparés par des virgules. Vous devez placer le [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md) dans des crochets pointus («`<`« et »`>`»).|  
|`accessmodifier`|Facultatif. Spécifie le code qui peut accéder au délégué. Il peut s'agir d'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md). Tout code qui peut accéder à l’élément qui déclare le délégué peut y accéder.<br />-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md). Seul le code dans la classe du délégué ou une classe dérivée peut y accéder.<br />-   [Ami](../../../visual-basic/language-reference/modifiers/friend.md). Seul le code dans le même assembly peut accéder au délégué.<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md). Seul le code dans l’élément qui déclare le délégué peut y accéder.<br /><br /> Vous pouvez spécifier `Protected Friend` pour activer l’accès à partir de code dans la classe du délégué, une classe dérivée ou le même assembly.|  
|`Shadows`|Facultatif. Indique que ce délégué redéclare et masque un élément de programmation portant le même nom ou un ensemble d’éléments surchargés, dans une classe de base. Vous pouvez occulter tout type d'élément déclaré par un autre type.<br /><br /> Un élément occulté n'est pas disponible à partir de la classe dérivée qui l'occulte, sauf à partir de l'emplacement où l'élément d'occultation est inaccessible. Par exemple, si un `Private` élément occulte un élément de la classe de base, le code qui n’est pas autorisé à accéder à la `Private` élément accède à l’élément de classe de base à la place.|  
|`Sub`|Facultatif, mais `Sub` ou `Function` doit apparaître. Déclare cette procédure en tant que délégué `Sub` procédure qui ne retourne pas de valeur.|  
|`Function`|Facultatif, mais `Sub` ou `Function` doit apparaître. Déclare cette procédure en tant que délégué `Function` procédure qui retourne une valeur.|  
|`name`|Obligatoire. Nom du type délégué. suit les conventions d’affectation de noms de variable standard.|  
|`typeparamlist`|Facultatif. Liste des paramètres de type pour ce délégué. Plusieurs paramètres de type sont séparés par des virgules. Éventuellement, chaque paramètre de type peut être déclaré variant à l’aide de `In` et `Out` modificateurs génériques. Vous devez placer le [Type liste](../../../visual-basic/language-reference/statements/type-list.md) entre parenthèses et l’introduire avec le `Of` (mot clé).|  
|`parameterlist`|Facultatif. Liste des paramètres qui sont passés à la procédure lorsqu’elle est appelée. Vous devez placer le [liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md) entre parenthèses.|  
|`type`|Obligatoire si vous spécifiez un `Function` procédure. Type de données de la valeur de retour.|  
  
## <a name="remarks"></a>Remarques  
 La `Delegate` instruction définit les types de paramètres et de retour d’une classe déléguée. Les procédures présentant des paramètres et types de retour peuvent être utilisé pour créer une instance de cette classe déléguée. La procédure peut ensuite être appelée ultérieurement au moyen de l’instance de délégué en appelant du délégué `Invoke` méthode.  
  
 Les délégués peuvent être déclarés à l’espace de noms, niveau du module, classe ou structure, mais pas dans une procédure.  
  
 Chaque classe déléguée définit un constructeur auquel les caractéristiques d’une méthode objet sont passées. Argument d’un constructeur délégué doit être une référence à une méthode ou une expression lambda.  
  
 Pour spécifier une référence à une méthode, utilisez la syntaxe suivante :  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Le type de compilation de le `expression` doit être le nom d’une classe ou une interface qui contient une méthode portant le nom spécifié dont la signature correspond à la signature de la classe déléguée. Le `methodname` peut être soit une méthode partagée, soit une méthode d’instance. Le `methodname` n’est pas facultatif, même si vous créez un délégué pour la méthode par défaut de la classe.  
  
 Pour spécifier une expression lambda, utilisez la syntaxe suivante :  
  
 `Function`([`parm` As `type`, `parm2` As `type2`, ...])`expression`  
  
 La signature de la fonction doit correspondre à celui du type délégué. Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Pour plus d’informations sur les délégués, consultez [délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la `Delegate` instruction pour déclarer un délégué pour fonctionner sur deux nombres et de retourner un nombre. Le `DelegateTest` méthode prend une instance d’un délégué de ce type et l’utilise pour fonctionner sur deux nombres.  
  
 [!code-vb[VbVbalrDelegates&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)   
 [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Comment : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Types génériques dans Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Covariance et Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8)   
 [Dans](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Sortie](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
