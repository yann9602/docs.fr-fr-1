---
title: Introduction aux transformations fonctionnelles pures (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 34c4b94577291f300dd2a14ffc33a5ec04b31782
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="introduction-to-pure-functional-transformations-c"></a><span data-ttu-id="4c8ab-102">Introduction aux transformations fonctionnelles pures (C#)</span><span class="sxs-lookup"><span data-stu-id="4c8ab-102">Introduction to Pure Functional Transformations (C#)</span></span>
<span data-ttu-id="4c8ab-103">Cette section présente les transformations fonctionnelles, y compris les concepts sous-jacents et les constructions de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="4c8ab-103">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="4c8ab-104">Elle décrit le contraste qu'il existe entre la programmation orientée objet et la programmation avec transformation fonctionnelle, et fournit des conseils pour aider les programmeurs à passer de l'une à l'autre.</span><span class="sxs-lookup"><span data-stu-id="4c8ab-104">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="4c8ab-105">Bien que les transformations fonctionnelles puissent être utilisées dans de nombreux scénarios de programmation, la transformation XML est utilisée ici comme exemple concret.</span><span class="sxs-lookup"><span data-stu-id="4c8ab-105">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c8ab-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4c8ab-106">In This Section</span></span>  
  
|<span data-ttu-id="4c8ab-107">Rubrique</span><span class="sxs-lookup"><span data-stu-id="4c8ab-107">Topic</span></span>|<span data-ttu-id="4c8ab-108">Description</span><span class="sxs-lookup"><span data-stu-id="4c8ab-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4c8ab-109">Concepts et terminologie (transformation fonctionnelle) (C#)</span><span class="sxs-lookup"><span data-stu-id="4c8ab-109">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)|<span data-ttu-id="4c8ab-110">Présente les concepts et la terminologie des transformations fonctionnelles pures.</span><span class="sxs-lookup"><span data-stu-id="4c8ab-110">Introduces the concepts and terminology of pure functional transformations.</span></span>|  
|[<span data-ttu-id="4c8ab-111">Comparaison de la programmation fonctionnelle et de la programmation impérative (C#)</span><span class="sxs-lookup"><span data-stu-id="4c8ab-111">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)|<span data-ttu-id="4c8ab-112">Compare et contraste la programmation fonctionnelle avec la programmation impérative (procédurale) plus traditionnelle.</span><span class="sxs-lookup"><span data-stu-id="4c8ab-112">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|  
|[<span data-ttu-id="4c8ab-113">Refactorisation dans des fonctions pures (C#)</span><span class="sxs-lookup"><span data-stu-id="4c8ab-113">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)|<span data-ttu-id="4c8ab-114">Présente les fonctions pures et fournit des exemples de fonctions pures et impures.</span><span class="sxs-lookup"><span data-stu-id="4c8ab-114">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|  
|[<span data-ttu-id="4c8ab-115">Applicabilité des transformations fonctionnelles (C#)</span><span class="sxs-lookup"><span data-stu-id="4c8ab-115">Applicability of Functional Transformation (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/applicability-of-functional-transformation.md)|<span data-ttu-id="4c8ab-116">Décrit des scénarios de transformation fonctionnelle courants.</span><span class="sxs-lookup"><span data-stu-id="4c8ab-116">Describes typical scenarios for functional transformations.</span></span>|  
|[<span data-ttu-id="4c8ab-117">Transformation fonctionnelle de données XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c8ab-117">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)|<span data-ttu-id="4c8ab-118">Décrit les transformations fonctionnelles dans le contexte de la transformation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="4c8ab-118">Describes functional transformations in the context of transforming XML trees.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c8ab-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c8ab-119">See Also</span></span>  
 [<span data-ttu-id="4c8ab-120">Transformations fonctionnelles pures de données XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4c8ab-120">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)

