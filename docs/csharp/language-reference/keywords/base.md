---
title: "base (référence C#)"
description: "Découvrez le mot clé base, qui sert à accéder aux membres de la classe de base à partir d’une classe dérivée en C#."
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
ms.sourcegitcommit: 867f9eb286fa7ff5ef3e9167c1ab944c81161216
ms.openlocfilehash: b3a389d92373b6ba5995a7644b0440f9d8fad9ac
ms.contentlocale: fr-fr
ms.lasthandoff: 08/17/2017

---
# <a name="base-c-reference"></a><span data-ttu-id="feda4-103">base (référence C#)</span><span class="sxs-lookup"><span data-stu-id="feda4-103">base (C# Reference)</span></span>

<span data-ttu-id="feda4-104">Le mot clé `base` sert à accéder aux membres de la classe de base à partir d’une classe dérivée :</span><span class="sxs-lookup"><span data-stu-id="feda4-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="feda4-105">Il appelle une méthode de la classe de base qui a été substituée par une autre méthode.</span><span class="sxs-lookup"><span data-stu-id="feda4-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="feda4-106">Il spécifie quel constructeur de classe de base doit être appelé lors de la création d’instances de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="feda4-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="feda4-107">L’accès à une classe de base est autorisé uniquement dans un constructeur, une méthode d’instance ou un accesseur de propriété d’instance.</span><span class="sxs-lookup"><span data-stu-id="feda4-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="feda4-108">L’utilisation du mot clé `base` à partir d’une méthode statique est une erreur.</span><span class="sxs-lookup"><span data-stu-id="feda4-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="feda4-109">La classe de base accessible est la classe de base spécifiée dans la déclaration de classe.</span><span class="sxs-lookup"><span data-stu-id="feda4-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="feda4-110">Par exemple, si vous spécifiez `class ClassB : ClassA`, les membres de ClassA sont accessibles à partir de ClassB, quelle que soit la classe de base de ClassA.</span><span class="sxs-lookup"><span data-stu-id="feda4-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="feda4-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="feda4-111">Example</span></span>
<span data-ttu-id="feda4-112">Dans cet exemple, la classe de base `Person` et la classe dérivée `Employee` ont toutes les deux une méthode nommée `Getinfo`.</span><span class="sxs-lookup"><span data-stu-id="feda4-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="feda4-113">En utilisant le mot clé `base`, vous pouvez appeler la méthode `Getinfo` de la classe de base à partir de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="feda4-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

<span data-ttu-id="feda4-114">[!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="feda4-114">[!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]</span></span>

<span data-ttu-id="feda4-115">Pour obtenir d’autres exemples, consultez [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md) et [override](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="feda4-115">For additional examples, see [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md), and [override](../../../csharp/language-reference/keywords/override.md).</span></span>

## <a name="example"></a><span data-ttu-id="feda4-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="feda4-116">Example</span></span>
<span data-ttu-id="feda4-117">Cet exemple montre comment spécifier le constructeur de classe de base qui est appelé lors de la création d’instances d’une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="feda4-117">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

<span data-ttu-id="feda4-118">[!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="feda4-118">[!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="feda4-119">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="feda4-119">C# language specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="feda4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="feda4-120">See also</span></span>
 <span data-ttu-id="feda4-121">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="feda4-121">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="feda4-122">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="feda4-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="feda4-123">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="feda4-123">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="feda4-124">this</span><span class="sxs-lookup"><span data-stu-id="feda4-124">this</span></span>](../../../csharp/language-reference/keywords/this.md)
