---
title: "this (référence C#) | Microsoft Docs"
description: "this, mot clé (référence C#)"
keywords: "this (C#) ; this, mot clé (C#) ; this, mot clé (référence C#) ; this, mot clé (référence du langage C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8e14a32f11b9661ae18fd718fb1a72385fa7f3a7
ms.lasthandoff: 03/13/2017

---
# <a name="this-c-reference"></a>this (référence C#)
Le mot clé `this` fait référence à l’instance actuelle de la classe et est également utilisé comme modificateur du premier paramètre d’une méthode d’extension.  
  
> [!NOTE]
>  Cet article traite de l’utilisation de `this` avec des instances de classe. Pour plus d’informations sur son utilisation dans les méthodes d’extension, consultez [Méthodes d’extension](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
 Voici quelques utilisations courantes de `this` :  
  
-   Pour qualifier des membres masqués par des noms similaires, par exemple :  
  
 [!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   Pour passer un objet comme paramètre à d’autres méthodes, par exemple :  
  
    ```  
    CalcTax(this);  
    ```  
  
-   Pour déclarer des indexeurs, par exemple :  
  
 [!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 Les fonctions membres statiques, car ils existent au niveau de la classe et non comme faisant partie d’un objet, n’ont pas de pointeur `this`. Une erreur consiste à faire référence à `this` dans une méthode statique.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, `this` est utilisé pour qualifier les membres de la classe `Employee`, `name` et `alias`, qui sont masqués par des noms similaires. Il est également utilisé pour passer un objet à la méthode `CalcTax`, qui appartient à une autre classe.  
  
 [!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [base](../../../csharp/language-reference/keywords/base.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)
