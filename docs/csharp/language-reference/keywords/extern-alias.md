---
title: "extern alias (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- alias_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: 16
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
ms.openlocfilehash: 66b399aaf6d4b3ba27957f3eadad3c1079ed2e90
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="extern-alias-c-reference"></a>extern alias (référence C#)
Il se peut que vous deviez référencer deux versions d’assemblys qui ont le même nom de type qualifié complet. Par exemple, vous pourriez avoir à utiliser plusieurs versions d’un assembly dans la même application. En utilisant un alias d’assembly externe, vous pouvez encapsuler les espaces de noms de chaque assembly dans des espaces de noms racines nommés par l’alias, ce qui permet de les utiliser dans le même fichier.  
  
> [!NOTE]
>  Le mot clé [extern](../../../csharp/language-reference/keywords/extern.md) est également utilisé comme modificateur de méthode, déclarant une méthode écrite en code non managé.  
  
 Pour référencer deux assemblys portant le même nom de type qualifié complet, vous devez spécifier un alias à l’invite de commandes, comme suit :  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Cela crée les alias externes `GridV1` et `GridV2`. Pour utiliser ces alias à partir d’un programme, référencez-les en utilisant le mot clé `extern`. Exemple :  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Chaque déclaration d’alias externe introduit un espace de noms racine supplémentaire qui est parallèle à l’espace de noms global (mais n’est pas compris dedans). Ainsi, vous pouvez référencer les types de chaque assembly sans ambiguïté en utilisant leur nom qualifié complet, enraciné dans l’alias d’espace de noms approprié.  
  
 Dans l’exemple précédent, `GridV1::Grid` serait le contrôle de grille de `grid.dll`, et `GridV2::Grid` serait le contrôle de grille de `grid20.dll`.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés d’espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [::, opérateur](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)   
 [/reference (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)

