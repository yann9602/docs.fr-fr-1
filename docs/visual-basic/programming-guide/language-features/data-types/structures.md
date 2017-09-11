---
title: Structures (Visual Basic) | Documents Microsoft
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
- structures
- user-defined data types, structures
- user-defined types, about user-defined types
- data types [Visual Basic], user-defined
- user-defined data types, about user-defined data types
- types [Visual Basic], user-defined
ms.assetid: 55e86462-5e99-4d33-8018-6d097ca491b2
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
ms.openlocfilehash: d1ba8671af9ff6d50499149fce6d55b3db78ffe0
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="structures-visual-basic"></a><span data-ttu-id="9e9bf-102">Structures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e9bf-102">Structures (Visual Basic)</span></span>
<span data-ttu-id="9e9bf-103">A *structure* est une généralisation du type défini par l’utilisateur (UDT) est pris en charge par les versions précédentes de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="9e9bf-103">A *structure* is a generalization of the user-defined type (UDT) supported by previous versions of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="9e9bf-104">En plus des champs, structures peuvent exposer des propriétés, méthodes et événements.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-104">In addition to fields, structures can expose properties, methods, and events.</span></span> <span data-ttu-id="9e9bf-105">Une structure peut implémenter une ou plusieurs interfaces, et vous pouvez déclarer des niveaux d’accès individuels pour chaque champ.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-105">A structure can implement one or more interfaces, and you can declare individual access levels for each field.</span></span>  
  
 <span data-ttu-id="9e9bf-106">Vous pouvez combiner des éléments de différents types pour créer une structure de données.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-106">You can combine data items of different types to create a structure.</span></span> <span data-ttu-id="9e9bf-107">Une structure associe un ou plusieurs *éléments* entre eux et avec la structure elle-même.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-107">A structure associates one or more *elements* with each other and with the structure itself.</span></span> <span data-ttu-id="9e9bf-108">Lorsque vous déclarez une structure, il devient un *type de données composite*, et vous pouvez déclarer des variables de ce type.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-108">When you declare a structure, it becomes a *composite data type*, and you can declare variables of that type.</span></span>  
  
 <span data-ttu-id="9e9bf-109">Les structures sont utiles lorsque vous souhaitez une seule variable pour contenir plusieurs informations connexes.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-109">Structures are useful when you want a single variable to hold several related pieces of information.</span></span> <span data-ttu-id="9e9bf-110">Par exemple, vous souhaitez peut-être conserver le nom d’un employé, numéro de poste et salaire.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-110">For example, you might want to keep an employee's name, telephone extension, and salary together.</span></span> <span data-ttu-id="9e9bf-111">Vous pouvez utiliser plusieurs variables pour obtenir ces informations, ou vous pouvez définir une structure et utilisez-le pour une variable d’employé unique.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-111">You could use several variables for this information, or you could define a structure and use it for a single employee variable.</span></span> <span data-ttu-id="9e9bf-112">L’avantage de la structure devient évident lorsque vous avez de nombreux employés et par conséquent de nombreuses instances de la variable.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-112">The advantage of the structure becomes apparent when you have many employees and therefore many instances of the variable.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e9bf-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9e9bf-113">In This Section</span></span>  
 [<span data-ttu-id="9e9bf-114">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="9e9bf-114">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 <span data-ttu-id="9e9bf-115">Montre comment déclarer une structure et ses éléments.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-115">Shows how to declare a structure and its elements.</span></span>  
  
 [<span data-ttu-id="9e9bf-116">Variables de structure</span><span class="sxs-lookup"><span data-stu-id="9e9bf-116">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 <span data-ttu-id="9e9bf-117">Explique comment assigner une structure à une variable et accéder à ses éléments.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-117">Covers assigning a structure to a variable and accessing its elements.</span></span>  
  
 [<span data-ttu-id="9e9bf-118">Structures et autres éléments de programmation</span><span class="sxs-lookup"><span data-stu-id="9e9bf-118">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 <span data-ttu-id="9e9bf-119">Récapitule comment les structures interagissent avec les tableaux, objets, procédures et l’autre.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-119">Summarizes how structures interact with arrays, objects, procedures, and each other.</span></span>  
  
 [<span data-ttu-id="9e9bf-120">Structures et classes</span><span class="sxs-lookup"><span data-stu-id="9e9bf-120">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 <span data-ttu-id="9e9bf-121">Décrit les similitudes et les différences entre les classes et structures.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-121">Describes the similarities and differences between structures and classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9e9bf-122">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="9e9bf-122">Related Sections</span></span>  
 [<span data-ttu-id="9e9bf-123">Types de données</span><span class="sxs-lookup"><span data-stu-id="9e9bf-123">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="9e9bf-124">Présente le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] types de données et explique comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="9e9bf-124">Introduces the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="9e9bf-125">Types de données</span><span class="sxs-lookup"><span data-stu-id="9e9bf-125">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="9e9bf-126">Répertorie les types de données élémentaires fournis par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="9e9bf-126">Lists the elementary data types supplied by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>
