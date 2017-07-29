---
title: "base (référence C#)"
description: "base, mot clé (C#)"
keywords: "base (C#) ; base, mot clé (C#) ; base, mot clé (référence C#) ; base, mot clé (référence du langage C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: 14
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
ms.openlocfilehash: c875ca834fc66e0bf6cd596f376773badca757e3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="base-c-reference"></a>base (référence C#)
Le mot clé `base` sert à accéder aux membres de la classe de base à partir d’une classe dérivée :  
  
-   Il appelle une méthode de la classe de base qui a été substituée par une autre méthode.  
  
-   Il spécifie quel constructeur de classe de base doit être appelé lors de la création d’instances de la classe dérivée.  
  
 L’accès à une classe de base est autorisé uniquement dans un constructeur, une méthode d’instance ou un accesseur de propriété d’instance.  
  
 L’utilisation du mot clé `base` à partir d’une méthode statique est une erreur.  
  
 La classe de base accessible est la classe de base spécifiée dans la déclaration de classe. Par exemple, si vous spécifiez `class ClassB : ClassA`, les membres de ClassA sont accessibles à partir de ClassB, quelle que soit la classe de base de ClassA.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la classe de base `Person` et la classe dérivée `Employee` ont toutes les deux une méthode nommée `Getinfo`. En utilisant le mot clé `base`, vous pouvez appeler la méthode `Getinfo` de la classe de base à partir de la classe dérivée.  
  
 [!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]  
  
 Pour obtenir d’autres exemples, consultez [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md) et [override](../../../csharp/language-reference/keywords/override.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment spécifier le constructeur de classe de base qui est appelé lors de la création d’instances d’une classe dérivée.  
  
 [!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [this](../../../csharp/language-reference/keywords/this.md)

