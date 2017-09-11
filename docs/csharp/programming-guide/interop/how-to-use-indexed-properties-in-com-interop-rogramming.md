---
title: "Comment : utiliser des propriétés indexées dans la programmation COM Interop (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
caps.latest.revision: 20
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
ms.openlocfilehash: 19e620415adefd6190d3896377eaf6a7cf944f28
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="ee5ff-102">Comment : utiliser des propriétés indexées dans la programmation COM Interop (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ee5ff-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="ee5ff-103">Les *propriétés indexées* améliorent la façon dont les propriétés COM avec des paramètres sont consommées dans la programmation C#.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="ee5ff-104">Les propriétés indexées fonctionnent avec d’autres fonctionnalités dans Visual C#, comme les [arguments nommés et facultatifs](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), un nouveau type ([dynamique](../../../csharp/language-reference/keywords/dynamic.md)) et [les informations de type incorporées](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), pour améliorer la programmation Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)), and [embedded type information](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="ee5ff-105">Dans les versions antérieures de C#, les méthodes sont accessibles comme des propriétés uniquement si la méthode `get` n’a aucun paramètre et que la méthode `set` a un seul et unique paramètre de valeur.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="ee5ff-106">Toutefois, toutes les propriétés COM ne respectent pas ces restrictions.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="ee5ff-107">Par exemple, la propriété [Range](http://go.microsoft.com/fwlink/?LinkId=166053) d’Excel a un accesseur `get` qui nécessite un paramètre pour le nom de la plage.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-107">For example, the Excel [Range](http://go.microsoft.com/fwlink/?LinkId=166053) property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="ee5ff-108">Dans le passé, parce que vous ne pouviez pas accéder à la propriété `Range` directement, vous deviez utiliser la méthode `get_Range` à la place, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 <span data-ttu-id="ee5ff-109">[!code-cs[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ee5ff-109">[!code-cs[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]</span></span>  
  
 <span data-ttu-id="ee5ff-110">Les propriétés indexées vous permettent d’écrire ce qui suit à la place :</span><span class="sxs-lookup"><span data-stu-id="ee5ff-110">Indexed properties enable you to write the following instead:</span></span>  
  
 <span data-ttu-id="ee5ff-111">[!code-cs[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ee5ff-111">[!code-cs[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee5ff-112">L’exemple précédent utilise également la fonctionnalité des [arguments facultatifs](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), qui vous permet d’omettre `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-112">The previous example also uses the [optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="ee5ff-113">De la même façon que pour définir la valeur de la propriété `Value` d’un objet [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) dans Visual C# 2008 et versions antérieures, deux arguments sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-113">Similarly to set the value of the `Value` property of a [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) object in Visual C# 2008 and earlier, two arguments are required.</span></span> <span data-ttu-id="ee5ff-114">L’un fournit un argument pour un paramètre facultatif qui spécifie le type de la valeur de la plage.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-114">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="ee5ff-115">L’autre fournit la valeur de la propriété `Value`.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-115">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="ee5ff-116">Les exemples suivants illustrent ces techniques.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-116">The following examples illustrate these techniques.</span></span> <span data-ttu-id="ee5ff-117">Les deux définissent la valeur de la cellule A1 sur `Name`.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-117">Both set the value of the A1 cell to `Name`.</span></span>
  
 <span data-ttu-id="ee5ff-118">[!code-cs[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="ee5ff-118">[!code-cs[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]</span></span>  
  
 <span data-ttu-id="ee5ff-119">Les propriétés indexées vous permettent d’écrire le code suivant à la place.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-119">Indexed properties enable you to write the following code instead.</span></span>  
  
 <span data-ttu-id="ee5ff-120">[!code-cs[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="ee5ff-120">[!code-cs[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]</span></span>  
  
 <span data-ttu-id="ee5ff-121">Vous ne pouvez pas créer vos propres propriétés indexées.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-121">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="ee5ff-122">La fonctionnalité prend uniquement en charge la consommation de propriétés indexées existantes.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-122">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee5ff-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="ee5ff-123">Example</span></span>  
 <span data-ttu-id="ee5ff-124">L'exemple de code suivant illustre l'exemple complet.</span><span class="sxs-lookup"><span data-stu-id="ee5ff-124">The following code shows a complete example.</span></span> <span data-ttu-id="ee5ff-125">Pour plus d’informations sur la configuration d’un projet qui accède à l’API Office, consultez [Guide pratique pour accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="ee5ff-125">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
 <span data-ttu-id="ee5ff-126">[!code-cs[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="ee5ff-126">[!code-cs[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee5ff-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee5ff-127">See Also</span></span>  
 <span data-ttu-id="ee5ff-128">[Arguments nommés et facultatifs](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="ee5ff-128">[Named and Optional Arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) </span></span>  
 <span data-ttu-id="ee5ff-129">[dynamic](../../../csharp/language-reference/keywords/dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="ee5ff-129">[dynamic](../../../csharp/language-reference/keywords/dynamic.md) </span></span>  
 <span data-ttu-id="ee5ff-130">[Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="ee5ff-130">[Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span></span>  
 <span data-ttu-id="ee5ff-131">[Guide pratique pour utiliser des arguments nommés et facultatifs dans la programmation Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span><span class="sxs-lookup"><span data-stu-id="ee5ff-131">[How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span></span>  
 <span data-ttu-id="ee5ff-132">[Guide pratique pour accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md) </span><span class="sxs-lookup"><span data-stu-id="ee5ff-132">[How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md) </span></span>  
 [<span data-ttu-id="ee5ff-133">Procédure pas à pas : programmation Office</span><span class="sxs-lookup"><span data-stu-id="ee5ff-133">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)

