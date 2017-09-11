---
title: Conversions de type dans Visual Basic | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- conversions, type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion
- conversions, data type
- changing data types
- data type conversion
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 61606572dd1f10dc5df4ed4baec02f230a23c8d6
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="44e64-102">Conversions de type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="44e64-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="44e64-103">Le processus de modification d’une valeur à partir d’un type de données à un autre type est appelé *conversion*.</span><span class="sxs-lookup"><span data-stu-id="44e64-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="44e64-104">Les conversions sont soit *étendues* ou *restrictives*, en fonction de la capacité de données des types concernés.</span><span class="sxs-lookup"><span data-stu-id="44e64-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="44e64-105">Ils sont également *implicite* ou *explicite*, en fonction de la syntaxe dans le code source.</span><span class="sxs-lookup"><span data-stu-id="44e64-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44e64-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="44e64-106">In This Section</span></span>  
 [<span data-ttu-id="44e64-107">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="44e64-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="44e64-108">Explique les conversions classées par si le type de destination peut stocker les données.</span><span class="sxs-lookup"><span data-stu-id="44e64-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="44e64-109">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="44e64-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="44e64-110">Traite des conversions classifiées par si [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] effectue automatiquement.</span><span class="sxs-lookup"><span data-stu-id="44e64-110">Discusses conversions classified by whether [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] performs them automatically.</span></span>  
  
 [<span data-ttu-id="44e64-111">Conversion entre des chaînes et d’autres types</span><span class="sxs-lookup"><span data-stu-id="44e64-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="44e64-112">Décrit la conversion entre des chaînes et numérique, `Boolean`, ou les valeurs de date/heure.</span><span class="sxs-lookup"><span data-stu-id="44e64-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="44e64-113">Comment : convertir un objet en un autre Type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="44e64-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="44e64-114">Montre comment convertir une `Object` variable en un autre type de données.</span><span class="sxs-lookup"><span data-stu-id="44e64-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="44e64-115">Conversions de tableau</span><span class="sxs-lookup"><span data-stu-id="44e64-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="44e64-116">Vous guide dans le processus de conversion entre les tableaux de types de données différents.</span><span class="sxs-lookup"><span data-stu-id="44e64-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="44e64-117">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="44e64-117">Related Sections</span></span>  
 [<span data-ttu-id="44e64-118">Types de données</span><span class="sxs-lookup"><span data-stu-id="44e64-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="44e64-119">Présente le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] types de données et explique comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="44e64-119">Introduces the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="44e64-120">Types de données</span><span class="sxs-lookup"><span data-stu-id="44e64-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="44e64-121">Répertorie les types de données élémentaires fournis par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="44e64-121">Lists the elementary data types supplied by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 [<span data-ttu-id="44e64-122">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="44e64-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="44e64-123">Présente des problèmes courants qui peuvent se produire lorsque vous travaillez avec des types de données.</span><span class="sxs-lookup"><span data-stu-id="44e64-123">Discusses some common problems that can arise when working with data types.</span></span>
