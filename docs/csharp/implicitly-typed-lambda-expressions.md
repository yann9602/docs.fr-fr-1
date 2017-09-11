---
title: "Expressions lambda implicitement typées"
description: "Découvrez pourquoi vous ne pouvez pas utiliser une déclaration de variable implicitement typée pour déclarer une expression lambda."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 663613af001f9727c48bd48553540305e47a6bab
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="56a68-104">Expressions lambda implicitement typées</span><span class="sxs-lookup"><span data-stu-id="56a68-104">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="56a68-105">Je n’utilise pas `var` pour déclarer cette arborescence d’expression.</span><span class="sxs-lookup"><span data-stu-id="56a68-105">I'm not using `var` to declare this expression tree.</span></span> <span data-ttu-id="56a68-106">Vous ne pouvez pas utiliser une déclaration de variable implicitement typée pour déclarer une expression lambda,</span><span class="sxs-lookup"><span data-stu-id="56a68-106">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="56a68-107">car cela crée un problème de logique circulaire pour le compilateur.</span><span class="sxs-lookup"><span data-stu-id="56a68-107">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="56a68-108">La déclaration `var` indique au compilateur de déterminer le type de la variable à partir du type de l’expression située à droite de l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="56a68-108">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="56a68-109">Une expression lambda n’a pas de type au moment de la compilation, mais elle peut être convertie en n’importe quel type d’expression ou de délégué correspondant.</span><span class="sxs-lookup"><span data-stu-id="56a68-109">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="56a68-110">Quand vous assignez une expression lambda à une variable d’un type de délégué ou d’expression, vous indiquez au compilateur de convertir l’expression lambda en une expression ou un délégué qui corresponde à la signature de la variable assignée.</span><span class="sxs-lookup"><span data-stu-id="56a68-110">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="56a68-111">Le compilateur doit tenter de faire correspondre ce qui se trouve à droite de l’assignation avec ce qui se trouve à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="56a68-111">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="56a68-112">Les deux côtés de l’assignation ne peuvent pas indiquer au compilateur d’examiner l’objet situé de l’autre côté de l’opérateur d’assignation et de vérifier si le type correspond.</span><span class="sxs-lookup"><span data-stu-id="56a68-112">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="56a68-113">Pour plus d’informations sur ce comportement du langage C#, lisez [cet article](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (téléchargement PDF)</span><span class="sxs-lookup"><span data-stu-id="56a68-113">You can get even more details on why the C# language specifies that behavior by reading [this article](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF Download)</span></span>



