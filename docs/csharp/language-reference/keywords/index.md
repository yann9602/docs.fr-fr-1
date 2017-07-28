---
title: "Mots clés C#"
ms.date: 2017-03-07
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.keywords
dev_langs:
- CSharp
helpviewer_keywords:
- keywords [C#]
- C# language, keywords
- Visual C#, keywords
- '@ keyword'
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 406579d833b2b3fbd3dbf510c38a69793ea8711f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="c-keywords"></a>Mots clés C#
Les mots clés sont des identificateurs réservés prédéfinis, qui ont des significations spécifiques pour le compilateur. Ils ne peuvent pas être utilisés comme identificateurs dans votre programme, sauf s’ils incluent `@` comme préfixe. Par exemple, `@if` est un identificateur valide, mais pas `if`, car `if` est un mot clé.  
  
 Le premier tableau de cette rubrique répertorie les mots clés qui sont des identificateurs réservés quelle que soit la partie d’un programme C#. Le deuxième tableau de cette rubrique liste les mots clés contextuels en C#. Les mots clés contextuels ont une signification spéciale dans un contexte de programme limité ; ils peuvent être utilisés comme identificateurs en dehors de ce contexte. En règle générale, lorsque de nouveaux mots clés sont ajoutés au langage C#, ils sont ajoutés comme mots clés contextuels afin d’éviter l’interruption des programmes écrits dans les versions antérieures.  
  
|||||  
|---|---|---|---|  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|[as](../../../csharp/language-reference/keywords/as.md)|[base](../../../csharp/language-reference/keywords/base.md)|[bool](../../../csharp/language-reference/keywords/bool.md)|  
|[break](../../../csharp/language-reference/keywords/break.md)|[byte](../../../csharp/language-reference/keywords/byte.md)|[case](../../../csharp/language-reference/keywords/switch.md)|[catch](../../../csharp/language-reference/keywords/try-catch.md)|  
|[char](../../../csharp/language-reference/keywords/char.md)|[checked](../../../csharp/language-reference/keywords/checked.md)|[class](../../../csharp/language-reference/keywords/class.md)|[const](../../../csharp/language-reference/keywords/const.md)|  
|[continue](../../../csharp/language-reference/keywords/continue.md)|[decimal](../../../csharp/language-reference/keywords/decimal.md)|[default](../../../csharp/language-reference/keywords/default.md)|[delegate](../../../csharp/language-reference/keywords/delegate.md)|  
|[do](../../../csharp/language-reference/keywords/do.md)|[double](../../../csharp/language-reference/keywords/double.md)|[else](../../../csharp/language-reference/keywords/if-else.md)|[enum](../../../csharp/language-reference/keywords/enum.md)|  
|[event](../../../csharp/language-reference/keywords/event.md)|[explicit](../../../csharp/language-reference/keywords/explicit.md)|[extern](../../../csharp/language-reference/keywords/extern.md)|[false](../../../csharp/language-reference/keywords/false.md)|  
|[finally](../../../csharp/language-reference/keywords/try-finally.md)|[fixed](../../../csharp/language-reference/keywords/fixed-statement.md)|[float](../../../csharp/language-reference/keywords/float.md)|[for](../../../csharp/language-reference/keywords/for.md)|  
|[foreach](../../../csharp/language-reference/keywords/foreach-in.md)|[goto](../../../csharp/language-reference/keywords/goto.md)|[if](../../../csharp/language-reference/keywords/if-else.md)|[implicit](../../../csharp/language-reference/keywords/implicit.md)|  
|[in](../../../csharp/language-reference/keywords/foreach-in.md)|[in (modificateur générique)](../../../csharp/language-reference/keywords/in-generic-modifier.md)|[int](../../../csharp/language-reference/keywords/int.md)|[interface](../../../csharp/language-reference/keywords/interface.md)|  
|[internal](../../../csharp/language-reference/keywords/internal.md)|[is](../../../csharp/language-reference/keywords/is.md)|[lock](../../../csharp/language-reference/keywords/lock-statement.md)|[long](../../../csharp/language-reference/keywords/long.md)|
|[namespace](../../../csharp/language-reference/keywords/namespace.md)|[new](../../../csharp/language-reference/keywords/new.md)|[null](../../../csharp/language-reference/keywords/null.md)|[object](../../../csharp/language-reference/keywords/object.md)|
[operator](../../../csharp/language-reference/keywords/operator.md)|[out](../../../csharp/language-reference/keywords/out.md)|[out (modificateur générique)](../../../csharp/language-reference/keywords/out-generic-modifier.md)|[override](../../../csharp/language-reference/keywords/override.md)|
|[params](../../../csharp/language-reference/keywords/params.md)|[private](../../../csharp/language-reference/keywords/private.md)|[protected](../../../csharp/language-reference/keywords/protected.md)|[public](../../../csharp/language-reference/keywords/public.md)|
|[readonly](../../../csharp/language-reference/keywords/readonly.md)|[ref](../../../csharp/language-reference/keywords/ref.md)|[return](../../../csharp/language-reference/keywords/return.md)|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|
|[sealed](../../../csharp/language-reference/keywords/sealed.md)|[short](../../../csharp/language-reference/keywords/short.md)|[sizeof](../../../csharp/language-reference/keywords/sizeof.md)|[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)|
|[static](../../../csharp/language-reference/keywords/static.md)|[string](../../../csharp/language-reference/keywords/string.md)|[struct](../../../csharp/language-reference/keywords/struct.md)|[switch](../../../csharp/language-reference/keywords/switch.md)|
|[this](../../../csharp/language-reference/keywords/this.md)|[throw](../../../csharp/language-reference/keywords/throw.md)|[true](../../../csharp/language-reference/keywords/true.md)|[try](../../../csharp/language-reference/keywords/try-catch.md)|   
|[typeof](../../../csharp/language-reference/keywords/typeof.md)|[uint](../../../csharp/language-reference/keywords/uint.md)|[ulong](../../../csharp/language-reference/keywords/ulong.md)|[unchecked](../../../csharp/language-reference/keywords/unchecked.md)|
|[unsafe](../../../csharp/language-reference/keywords/unsafe.md)|[ushort](../../../csharp/language-reference/keywords/ushort.md)|[using](../../../csharp/language-reference/keywords/using.md)|[using static](using-static.md)|
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|[void](../../../csharp/language-reference/keywords/void.md)|[volatile](../../../csharp/language-reference/keywords/volatile.md)|[while](../../../csharp/language-reference/keywords/while.md)|

## <a name="contextual-keywords"></a>Mots clés contextuels  
 Un mot clé contextuel sert à donner une signification spécifique dans le code, sans pour autant être un mot réservé en C#. Certains mots clés contextuels, tels que `partial` et `where`, ont des significations spéciales dans deux contextes ou plus.  
  
||||  
|---|---|---|  
|[add](../../../csharp/language-reference/keywords/add.md)|[alias](../../../csharp/language-reference/keywords/extern-alias.md)|[ascending](../../../csharp/language-reference/keywords/ascending.md)|  
|[async](../../../csharp/language-reference/keywords/async.md)|[await](../../../csharp/language-reference/keywords/await.md)|[descending](../../../csharp/language-reference/keywords/descending.md)|  
|[dynamic](../../../csharp/language-reference/keywords/dynamic.md)|[from](../../../csharp/language-reference/keywords/from-clause.md)|[get](../../../csharp/language-reference/keywords/get.md)|  
|[global](../../../csharp/language-reference/keywords/global.md)|[group](../../../csharp/language-reference/keywords/group-clause.md)|[into](../../../csharp/language-reference/keywords/into.md)|  
|[join](../../../csharp/language-reference/keywords/join-clause.md)|[let](../../../csharp/language-reference/keywords/let-clause.md)|[nameof](nameof.md)|   
|[orderby](../../../csharp/language-reference/keywords/orderby-clause.md)|[partial (type)](../../../csharp/language-reference/keywords/partial-type.md)|[partial (méthode)](../../../csharp/language-reference/keywords/partial-method.md)|   
|[remove](../../../csharp/language-reference/keywords/remove.md)|[select](../../../csharp/language-reference/keywords/select-clause.md)|[set](../../../csharp/language-reference/keywords/set.md)|   
|[value](../../../csharp/language-reference/keywords/value.md)|[var](../../../csharp/language-reference/keywords/var.md)|[when (condition de filtre)](when.md)|   
|[where (contrainte de type générique)](../../../csharp/language-reference/keywords/where-generic-type-constraint.md)|[where (clause de requête)](../../../csharp/language-reference/keywords/where-clause.md)|[yield](../../../csharp/language-reference/keywords/yield.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du langage C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)

