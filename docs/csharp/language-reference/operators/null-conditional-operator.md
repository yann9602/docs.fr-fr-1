---
title: "?? Opérateur (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ??_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: 17
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a780a11d8dd238187eb82933359bbb151bb3c333
ms.openlocfilehash: de2abc6830419c368c6a62dfd74fc6f2013db9d4
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="-operator-c-reference"></a>?? , opérateur (Informations de référence sur C#)
L'opérateur `??` est appelé l'l'opérateur de fusion Null.  Il retourne l’opérande de partie gauche si ce dernier n’est pas Null ; dans le cas contraire, il retourne l’opérande de partie droite.  
  
## <a name="remarks"></a>Remarques  
 Un type Nullable peut représenter une valeur à partir du domaine du type, ou la valeur peut être non définie (auquel cas la valeur est Null). Utilisez la simplicité de syntaxe de l'opérateur `??` pour retourner une valeur appropriée (l'opérande de partie droite) si l'opérande de partie gauche a un type Nullable dont la valeur est Null. Si vous essayez d'assigner un type valeur Nullable à un type valeur non Nullable sans utiliser l'opérateur `??`, vous générez une erreur au moment de la compilation. Si vous utilisez un cast et si le type valeur Nullable est actuellement non défini, une exception `InvalidOperationException` est levée.  
  
 Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Le résultat d’un opérateur ?? n’est pas considéré comme une constante même si ses deux arguments sont des constantes.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)   
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)   
 [Que signifie réellement « Lifted » ?](http://go.microsoft.com/fwlink/?LinkID=112382)
