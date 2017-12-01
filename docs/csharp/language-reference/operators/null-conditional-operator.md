---
title: "?? , opérateur (Informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a49d36b8580812c08e9ee080a9602d9fc2027ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>?? , opérateur (Informations de référence sur C#)
L'opérateur `??` est appelé l'l'opérateur de fusion Null.  Il retourne l’opérande de partie gauche si ce dernier n’est pas Null ; dans le cas contraire, il retourne l’opérande de partie droite.  
  
## <a name="remarks"></a>Remarques  
 Un type Nullable peut représenter une valeur à partir du domaine du type, ou la valeur peut être non définie (auquel cas la valeur est Null). Vous pouvez utiliser la `??` simplicité de syntaxe de l’opérateur pour retourner une valeur appropriée (l’opérande de droite) si l’opérande de gauche a un type nullable dont la valeur est null. Si vous essayez d'assigner un type valeur Nullable à un type valeur non Nullable sans utiliser l'opérateur `??`, vous générez une erreur au moment de la compilation. Si vous utilisez un cast et si le type valeur Nullable est actuellement non défini, une exception `InvalidOperationException` est levée.  
  
 Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Le résultat d’un opérateur ?? n’est pas considéré comme une constante même si ses deux arguments sont des constantes.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)  
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)  
 [Que signifie réellement « Lifted » ?](http://go.microsoft.com/fwlink/?LinkID=112382)
