---
title: Variables de structure (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef42c44de84caffde909eb2b3e9361016a6abb97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="2210c-102">Variables de structure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2210c-102">Structure Variables (Visual Basic)</span></span>
<span data-ttu-id="2210c-103">Une fois que vous avez créé une structure, vous pouvez déclarer des variables au niveau de la procédure et au niveau du module en tant que type.</span><span class="sxs-lookup"><span data-stu-id="2210c-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="2210c-104">Par exemple, vous pouvez créer une structure qui enregistre les informations concernant un système informatique.</span><span class="sxs-lookup"><span data-stu-id="2210c-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="2210c-105">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2210c-105">The following example demonstrates this.</span></span>  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 <span data-ttu-id="2210c-106">Vous pouvez désormais déclarer des variables de ce type.</span><span class="sxs-lookup"><span data-stu-id="2210c-106">You can now declare variables of that type.</span></span> <span data-ttu-id="2210c-107">L’exemple suivant illustre cela.</span><span class="sxs-lookup"><span data-stu-id="2210c-107">The following declaration illustrates this.</span></span>  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  <span data-ttu-id="2210c-108">Dans les classes et les modules, les structures déclarées à l’aide de la [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) par défaut d’un accès public.</span><span class="sxs-lookup"><span data-stu-id="2210c-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="2210c-109">Si vous envisagez une structure soit privée, assurez-vous que vous devez la déclarer à l’aide de la [privé](../../../../visual-basic/language-reference/modifiers/private.md) (mot clé).</span><span class="sxs-lookup"><span data-stu-id="2210c-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>  
  
## <a name="access-to-structure-values"></a><span data-ttu-id="2210c-110">Accès aux valeurs de la Structure</span><span class="sxs-lookup"><span data-stu-id="2210c-110">Access to Structure Values</span></span>  
 <span data-ttu-id="2210c-111">Pour assigner et récupérer des valeurs dans les éléments d’une variable de structure, vous utilisez la même syntaxe que vous utilisez pour définir et obtenir les propriétés sur un objet.</span><span class="sxs-lookup"><span data-stu-id="2210c-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="2210c-112">Vous placez l’opérateur d’accès au membre (`.`) entre le nom de variable de structure et le nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="2210c-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="2210c-113">L’exemple suivant accède à des éléments des variables déclarées précédemment comme type `systemInfo`.</span><span class="sxs-lookup"><span data-stu-id="2210c-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a><span data-ttu-id="2210c-114">Assignation de Variables de Structure</span><span class="sxs-lookup"><span data-stu-id="2210c-114">Assigning Structure Variables</span></span>  
 <span data-ttu-id="2210c-115">Vous pouvez également affecter une variable à un autre si les deux sont du même type de structure.</span><span class="sxs-lookup"><span data-stu-id="2210c-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="2210c-116">Cette opération copie tous les éléments d’une structure aux éléments correspondants dans l’autre.</span><span class="sxs-lookup"><span data-stu-id="2210c-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="2210c-117">L’exemple suivant illustre cela.</span><span class="sxs-lookup"><span data-stu-id="2210c-117">The following declaration illustrates this.</span></span>  
  
```  
yourSystem = mySystem  
```  
  
 <span data-ttu-id="2210c-118">Si un élément de structure est un type référence, comme un `String`, `Object`, ou tableau, le pointeur vers les données est copié.</span><span class="sxs-lookup"><span data-stu-id="2210c-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="2210c-119">Dans l’exemple précédent, si `systemInfo` avait inclus une variable objet, puis l’exemple précédent aurait copié le pointeur à partir de `mySystem` à `yourSystem`, et une modification de données de l’objet via une structure seraient en vigueur lors de l’accès par l’autre structure.</span><span class="sxs-lookup"><span data-stu-id="2210c-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2210c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2210c-120">See Also</span></span>  
 [<span data-ttu-id="2210c-121">Types de données</span><span class="sxs-lookup"><span data-stu-id="2210c-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="2210c-122">Types de données élémentaires</span><span class="sxs-lookup"><span data-stu-id="2210c-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="2210c-123">Types de données composites</span><span class="sxs-lookup"><span data-stu-id="2210c-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="2210c-124">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="2210c-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="2210c-125">Structures</span><span class="sxs-lookup"><span data-stu-id="2210c-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="2210c-126">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="2210c-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="2210c-127">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="2210c-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="2210c-128">Structures et autres éléments de programmation</span><span class="sxs-lookup"><span data-stu-id="2210c-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [<span data-ttu-id="2210c-129">Structures et classes</span><span class="sxs-lookup"><span data-stu-id="2210c-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="2210c-130">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="2210c-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
