---
title: Key (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20dbe4e67fb3e415ba0202555ace7fd5afed68d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
Le `Key` mot clé permet de spécifier le comportement des propriétés de types anonymes. Seules les propriétés que vous désignez comme propriétés de clé participent aux tests d’égalité entre les instances de type anonyme, ou un calcul de valeurs de code de hachage. Les valeurs des propriétés de clé ne peut pas être modifiés.  
  
 Vous désignez une propriété d’un type anonyme comme propriété de clé en plaçant le mot clé `Key` devant sa déclaration dans la liste d’initialisation. Dans l’exemple suivant, `Airline` et `FlightNo` sont des propriétés de clé, mais `Gate` n’est pas.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 Lorsqu’un nouveau type anonyme est créé, il hérite directement de <xref:System.Object>. Le compilateur substitue trois membres hérités : <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, et <xref:System.Object.ToString%2A>. Le code de substitution qui est généré pour <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> est basée sur les propriétés de clé. S’il en existe aucune propriété de clé dans le type, <xref:System.Object.GetHashCode%2A> et <xref:System.Object.Equals%2A> ne sont pas substitués.  
  
## <a name="equality"></a>Égalité  
 Deux instances de type anonyme sont égales si elles sont des instances du même type et si les valeurs de leurs propriétés de clé sont égales. Dans les exemples suivants, `flight2` est égal à `flight1` à partir de l’exemple précédent, car ce sont des instances du même anonyme type et ils ont des valeurs correspondantes pour leurs propriétés de clé. Toutefois, `flight3` n’est pas égal à `flight1` , car il a une valeur différente pour une propriété de clé, `FlightNo`. Instance `flight4` n’est pas du même type que `flight1` car ils désignent des propriétés différentes comme propriétés de clé.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 Si deux instances sont déclarées avec uniquement des propriétés non-clés, identiques dans nom, type, ordre et valeur, les deux instances ne sont pas égaux. Une instance sans propriété de clé est uniquement égale à elle-même.  
  
 Pour plus d’informations sur les conditions dans lesquelles deux instances de type anonyme sont des instances du même type anonyme, consultez [Types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Calcul de Code de hachage  
 Comme <xref:System.Object.Equals%2A>, la fonction de hachage qui est définie dans <xref:System.Object.GetHashCode%2A> pour un type anonyme est basé sur les propriétés de clé du type. Les exemples suivants illustrent l’interaction entre les propriétés de clé et le hachage des valeurs de code.  
  
 Les instances d’un type anonyme qui ont les mêmes valeurs pour toutes les propriétés de clé ont la même valeur de code de hachage, même si des propriétés non-clés n’ont pas de valeurs correspondantes. L’instruction suivante retourne `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 Les instances d’un type anonyme qui ont des valeurs différentes pour une ou plusieurs propriétés de clé ont des valeurs de code de hachage différent. L’instruction suivante retourne `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 Instances de types anonymes qui désignent des propriétés différentes comme propriétés de clé ne sont pas des instances du même type. Ils ont des valeurs de code de hachage différentes même lorsque les noms et valeurs de toutes les propriétés sont identiques. L’instruction suivante retourne `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a>Valeurs en lecture seule  
 Les valeurs des propriétés de clé ne peut pas être modifiés. Par exemple, dans `flight1` dans les exemples précédents, le `Airline` et `FlightNo` champs sont en lecture seule, mais `Gate` peut être modifié.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Définition du type anonyme](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [Guide pratique : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
