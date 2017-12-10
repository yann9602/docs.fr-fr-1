---
title: "Interopérabilité (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2965543066b0846a6a4f8a3199590049947122f2
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="e5077-102">Interopérabilité (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e5077-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="e5077-103">L’interopérabilité vous permet de préserver et de tirer parti d’investissements existants en code non managé.</span><span class="sxs-lookup"><span data-stu-id="e5077-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="e5077-104">Le code qui s’exécute sous le contrôle du common language runtime (CLR) est appelé *code managé*, et le code qui s’exécute en dehors du CLR est appelé *code non managé*.</span><span class="sxs-lookup"><span data-stu-id="e5077-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="e5077-105">COM, COM+, les composants C++, les composants ActiveX et l’API Microsoft Win32 sont des exemples de code non managé.</span><span class="sxs-lookup"><span data-stu-id="e5077-105">COM, COM+, C++ components, ActiveX components, and Microsoft Win32 API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="e5077-106">Le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] permet l’interopérabilité avec du code non managé par des services d’appel de code non managé, l’espace de noms <xref:System.Runtime.InteropServices>, l’interopérabilité C++ et l’interopérabilité COM (COM Interop).</span><span class="sxs-lookup"><span data-stu-id="e5077-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5077-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e5077-107">In This Section</span></span>  
 [<span data-ttu-id="e5077-108">Vue d’ensemble de l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="e5077-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="e5077-109">Décrit les méthodes qui permettent l’interopérabilité entre le code managé et le code non managé en C#.</span><span class="sxs-lookup"><span data-stu-id="e5077-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="e5077-110">Comment : accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#</span><span class="sxs-lookup"><span data-stu-id="e5077-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="e5077-111">Décrit les fonctionnalités introduites dans Visual C# pour faciliter la programmation Office.</span><span class="sxs-lookup"><span data-stu-id="e5077-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="e5077-112">Comment : utiliser des propriétés indexées dans la programmation COM Interop</span><span class="sxs-lookup"><span data-stu-id="e5077-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="e5077-113">Explique comment utiliser des propriétés indexées pour accéder aux propriétés COM qui ont des paramètres.</span><span class="sxs-lookup"><span data-stu-id="e5077-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="e5077-114">Comment : utiliser l’appel de code non managé pour lire un fichier audio</span><span class="sxs-lookup"><span data-stu-id="e5077-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="e5077-115">Explique comment utiliser des services d’appel de code non managé pour lire un fichier son .wav sur le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="e5077-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="e5077-116">Procédure pas à pas : programmation Office</span><span class="sxs-lookup"><span data-stu-id="e5077-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="e5077-117">Montre comment créer un classeur Excel et un document Word qui contient un lien vers le classeur.</span><span class="sxs-lookup"><span data-stu-id="e5077-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="e5077-118">Exemple de classe COM</span><span class="sxs-lookup"><span data-stu-id="e5077-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="e5077-119">Montre comment exposer une classe C# en tant qu’objet COM.</span><span class="sxs-lookup"><span data-stu-id="e5077-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e5077-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="e5077-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e5077-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5077-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="e5077-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e5077-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e5077-123">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="e5077-123">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="e5077-124">Procédure pas à pas : programmation Office</span><span class="sxs-lookup"><span data-stu-id="e5077-124">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
