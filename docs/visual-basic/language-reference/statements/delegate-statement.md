---
title: "Delegate Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Delegate"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "delegate keyword"
  - "Delegate statement"
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Delegate Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Permet de déclarer un délégué.  Un délégué est un type référence qui fait référence à une méthode `Shared` d'un type ou à une méthode d'instance d'un objet.  Les procédures présentant des paramètres et types de retour assortis peuvent être utilisées pour créer une instance de cette classe de délégué.  La procédure peut ensuite être appelée ultérieurement par l'intermédiaire de l'instance déléguée.  
  
## Syntaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`attrlist`|Facultatif.  Liste des attributs s'appliquant à ce délégué.  Les attributs multiples sont séparés par des virgules.  Vous devez placer le [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) entre des signes "inférieur à" et "supérieur à" \("`<`" et "`>`"\).|  
|`accessmodifier`|Facultatif.  Spécifie le code pouvant accéder à ce délégué.  Il peut s'agir de l'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md).  Tout code pouvant accéder à l'élément qui déclare le délégué peut y accéder.<br />-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md).  Seul le code dans la classe du délégué ou dans une classe dérivée peut y accéder.<br />-   [Fonction friend](../../../visual-basic/language-reference/modifiers/friend.md).  Seul le code dans le même assembly peut accéder au délégué.<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md).  Seul le code dans l'élément qui déclare le délégué peut y accéder.<br /><br /> Vous pouvez spécifier `Protected Friend` pour permettre l'accès à partir du code dans la classe du délégué, dans une classe dérivée ou dans le même assembly.|  
|`Shadows`|Facultatif.  Indique si ce délégué redéclare et masque un élément de programmation de même nom ou un ensemble d'éléments surchargés, dans une classe de base.  Vous pouvez occulter tout type d'élément déclaré par un autre type.<br /><br /> Un élément occulté n'est pas disponible à partir de la classe dérivée qui l'occulte, sauf à partir de l'emplacement où l'élément d'occultation est inaccessible.  Par exemple, si un élément `Private` occulte un élément de classe de base, le code qui n'est pas autorisé à accéder à l'élément `Private` accède à la place à l'élément de classe de base.|  
|`Sub`|Facultatif, mais `Sub` ou `Function` doit être indiqué.  Déclare cette procédure en tant que procédure `Sub` de délégué qui ne retourne pas de valeur.|  
|`Function`|Facultatif, mais `Sub` ou `Function` doit être indiqué.  Déclare cette procédure en tant que procédure `Function` de délégué qui retourne une valeur.|  
|`name`|Obligatoire.  Nom du type délégué. Ce nom respecte les conventions standard d'affectation de noms aux variables.|  
|`typeparamlist`|Facultatif.  Liste de paramètres de type pour ce délégué.  Les paramètres de type, lorsqu'il y en a plusieurs, sont séparés par des virgules.  Éventuellement, chaque paramètre de type peut être déclaré variant à l'aide des modificateurs génériques `In` et `Out`.  Vous devez mettre la [Type List](../../../visual-basic/language-reference/statements/type-list.md) entre parenthèses et l'introduire avec le mot clé `Of`.|  
|`parameterlist`|Facultatif.  Liste des paramètres qui sont passés à la procédure lorsqu'elle est appelée.  Vous devez mettre la [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md) entre parenthèses.|  
|`type`|Requis si vous spécifiez une procédure `Function`.  Type de données de la valeur de retour.|  
  
## Notes  
 L'instruction `Delegate` définit les types de paramètres et de retour d'une classe déléguée.  Les procédures présentant des paramètres et types de retour assortis peuvent être utilisées pour créer une instance de cette classe de délégué.  La procédure peut ensuite être appelée ultérieurement par l'intermédiaire de l'instance déléguée, en appelant la méthode `Invoke` du délégué.  
  
 Les délégués peuvent être déclarés au niveau de l'espace de noms, du module, de la classe ou de la structure, mais pas dans une procédure.  
  
 Chaque classe déléguée définit un constructeur auquel les caractéristiques d'une méthode objet sont passées.  Un argument à un constructeur délégué doit correspondre à une référence à une méthode ou à une expression lambda.  
  
 Pour spécifier une référence à une méthode, utilisez la syntaxe suivante :  
  
 `AddressOf` \[`expression`.\]`methodname`  
  
 Le type de l'`expression` au moment de la compilation doit correspondre au nom d'une classe ou d'une interface qui contient une méthode avec le nom spécifié dont la signature correspond à celle de la classe déléguée.  La méthode `methodname` peut être soit une méthode partagée, soit une méthode d'instance.  `methodname` n'est pas facultatif, même si vous créez un délégué pour la méthode par défaut de la classe.  
  
 Pour spécifier une expression lambda, utilisez la syntaxe suivante :  
  
 `Function` \(\[`parm` As `type`, `parm2` As `type2`, ...\]\) `expression`  
  
 La signature de la fonction doit correspondre à celle du type délégué.  Pour plus d'informations sur les expressions lambda, consultez [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Pour plus d'informations sur les délégués, consultez [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md).  
  
## Exemple  
 L'exemple suivant utilise l'instruction `Delegate` pour déclarer un délégué afin de fonctionner sur deux nombres et de retourner un nombre.  La méthode `DelegateTest` accepte une instance d'un délégué de ce type et s'en sert pour fonctionner sur deux nombres.  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## Voir aussi  
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)   
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Comment : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Covariance et contravariance](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)