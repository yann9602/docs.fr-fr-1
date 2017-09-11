---
title: COM Interop (Visual Basic)
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
- Visual Basic code, COM interop
- COM interop, in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
caps.latest.revision: 14
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 29275519a00ad0c33a5b85e592532ce456daefe0
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="bf681-102">COM Interop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf681-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="bf681-103">Le modèle COM (Component Object Model) permet à un objet d’exposer ses fonctionnalités à d’autres composants et d’héberger des applications.</span><span class="sxs-lookup"><span data-stu-id="bf681-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="bf681-104">La plupart des logiciels actuels incluent des objets COM.</span><span class="sxs-lookup"><span data-stu-id="bf681-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="bf681-105">Bien que les assemblys .NET représentent le meilleur choix pour les nouvelles applications, vous devrez peut-être parfois utiliser des objets COM.</span><span class="sxs-lookup"><span data-stu-id="bf681-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="bf681-106">Cette section traite de certains des problèmes liés à la création et à l’utilisation des objets COM avec [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf681-106">This section covers some of the issues associated with creating and using COM objects with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bf681-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="bf681-107">In This Section</span></span>  
 [<span data-ttu-id="bf681-108">Introduction à COM Interop</span><span class="sxs-lookup"><span data-stu-id="bf681-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="bf681-109">Fournit une vue d’ensemble de l’interopérabilité COM.</span><span class="sxs-lookup"><span data-stu-id="bf681-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="bf681-110">Guide pratique pour référencer les objets COM à partir de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf681-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="bf681-111">Décrit la procédure à suivre pour ajouter des références aux objets COM qui ont des bibliothèques de types.</span><span class="sxs-lookup"><span data-stu-id="bf681-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="bf681-112">Guide pratique : utiliser les contrôles ActiveX</span><span class="sxs-lookup"><span data-stu-id="bf681-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="bf681-113">Montre comment utiliser des contrôles ActiveX existants pour ajouter des fonctionnalités à la boîte à outils [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf681-113">Demonstrates how to use existing ActiveX controls to add features to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Toolbox.</span></span>  
  
 [<span data-ttu-id="bf681-114">Procédure pas à pas : appel des API Windows</span><span class="sxs-lookup"><span data-stu-id="bf681-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="bf681-115">Vous guide tout au long du processus d’appel des API qui font partie du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="bf681-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="bf681-116">Guide pratique : appeler des API Windows</span><span class="sxs-lookup"><span data-stu-id="bf681-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="bf681-117">Montre comment définir et appeler la fonction `MessageBox` dans User32.dll.</span><span class="sxs-lookup"><span data-stu-id="bf681-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="bf681-118">Guide pratique : appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="bf681-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="bf681-119">Montre comment appeler une fonction Windows qui a un paramètre de type non signé.</span><span class="sxs-lookup"><span data-stu-id="bf681-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="bf681-120">Procédure pas à pas : création d’objets COM avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf681-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="bf681-121">Vous guide tout au long du processus de création d’objets COM avec et sans le modèle de classe COM.</span><span class="sxs-lookup"><span data-stu-id="bf681-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="bf681-122">Dépannage des problèmes liés à l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="bf681-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="bf681-123">Aborde certains des problèmes qui peuvent se poser lors de l’utilisation de COM.</span><span class="sxs-lookup"><span data-stu-id="bf681-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="bf681-124">Interopérabilité COM dans les applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bf681-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="bf681-125">Fournit une vue d’ensemble de l’utilisation d’objets COM et d’objets .NET Framework dans la même application.</span><span class="sxs-lookup"><span data-stu-id="bf681-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="bf681-126">Procédure pas à pas : implémentation de l’héritage avec les objets COM</span><span class="sxs-lookup"><span data-stu-id="bf681-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="bf681-127">Décrit l’utilisation d’objets COM existants comme base des nouveaux objets.</span><span class="sxs-lookup"><span data-stu-id="bf681-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bf681-128">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="bf681-128">Related Sections</span></span>  
 [<span data-ttu-id="bf681-129">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="bf681-129">Interoperating with Unmanaged Code</span></span>](https://msdn.microsoft.com/library/sd10k43k)  
 <span data-ttu-id="bf681-130">Décrit les services d'interopérabilité fournis par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="bf681-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="bf681-131">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bf681-131">Exposing COM Components to the .NET Framework</span></span>](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)  
 <span data-ttu-id="bf681-132">Décrit le processus d’appel de types COM via COM Interop.</span><span class="sxs-lookup"><span data-stu-id="bf681-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="bf681-133">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="bf681-133">Exposing .NET Framework Components to COM</span></span>](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6)  
 <span data-ttu-id="bf681-134">Décrit la préparation et l’utilisation de types managés à partir de COM.</span><span class="sxs-lookup"><span data-stu-id="bf681-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="bf681-135">Application d’attributs d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="bf681-135">Applying Interop Attributes</span></span>](https://msdn.microsoft.com/library/d4w8x20h)  
 <span data-ttu-id="bf681-136">Aborde les attributs que vous pouvez utiliser lors de l’utilisation de code non managé.</span><span class="sxs-lookup"><span data-stu-id="bf681-136">Covers attributes you can use when working with unmanaged code.</span></span>

