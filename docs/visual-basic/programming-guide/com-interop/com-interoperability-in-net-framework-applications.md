---
title: "Interopérabilité COM dans les applications .NET Framework (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 28ec54dc062d4fdea4836b0ecc8699982dace623
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="4464c-102">Interopérabilité COM dans les applications .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4464c-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="4464c-103">Lorsque vous souhaitez utiliser les objets COM et .NET Framework dans la même application, vous devez résoudre les différences dans la façon dont les objets existent dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="4464c-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="4464c-104">Un objet .NET Framework se trouve dans la mémoire managée, la mémoire contrôlée par le common language runtime et peut être déplacé par le runtime en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="4464c-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="4464c-105">Un objet COM se trouve dans la mémoire non managée et n’est pas censé déplacer vers un autre emplacement de mémoire.</span><span class="sxs-lookup"><span data-stu-id="4464c-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="4464c-106">et [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fournissent des outils pour contrôler l’interaction de ces composants managés et.</span><span class="sxs-lookup"><span data-stu-id="4464c-106"> and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="4464c-107">Pour plus d’informations sur le code managé, consultez [Common Language Runtime](../../../standard/clr.md).</span><span class="sxs-lookup"><span data-stu-id="4464c-107">For more information about managed code, see [Common Language Runtime](../../../standard/clr.md).</span></span>  
  
 <span data-ttu-id="4464c-108">Outre l’utilisation des objets COM dans les applications .NET, vous pouvez souhaiter également utiliser [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pour développer des objets accessibles à partir de code non managé via COM.</span><span class="sxs-lookup"><span data-stu-id="4464c-108">In addition to using COM objects in .NET applications, you may also want to use [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="4464c-109">Les liens de cette page fournissent des détails sur les interactions entre les objets COM et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4464c-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4464c-110">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="4464c-110">Related Sections</span></span>  
 [<span data-ttu-id="4464c-111">COM Interop</span><span class="sxs-lookup"><span data-stu-id="4464c-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="4464c-112">Fournit des liens vers les rubriques traitant l’interopérabilité COM en Visual Basic, y compris les objets COM, les contrôles ActiveX, les DLL Win32, les objets managés et l’héritage d’objets COM.</span><span class="sxs-lookup"><span data-stu-id="4464c-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="4464c-113">Erreur de Wrapper COM Interop</span><span class="sxs-lookup"><span data-stu-id="4464c-113">COM Interop Wrapper Error</span></span>](/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="4464c-114">Décrit les conséquences et les options si le système de projet ne peut pas créer un wrapper d’interopérabilité COM pour un composant particulier.</span><span class="sxs-lookup"><span data-stu-id="4464c-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="4464c-115">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="4464c-115">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
 <span data-ttu-id="4464c-116">Certains problèmes d’interaction entre du code managé et décrit brièvement et fournit des liens pour approfondir ce sujet.</span><span class="sxs-lookup"><span data-stu-id="4464c-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="4464c-117">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="4464c-117">COM Wrappers</span></span>](../../../framework/interop/com-wrappers.md)  
 <span data-ttu-id="4464c-118">Présente les wrappers RCW, qui permettent au code managé d’appeler les méthodes COM, et par COM, qui permettent aux clients COM d’appeler les méthodes d’objet .NET.</span><span class="sxs-lookup"><span data-stu-id="4464c-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="4464c-119">Interopérabilité COM avancée</span><span class="sxs-lookup"><span data-stu-id="4464c-119">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="4464c-120">Fournit des liens vers les rubriques traitant l’interopérabilité COM en ce qui concerne les wrappers, exceptions, l’héritage, threads, les événements, les conversions et marshaling.</span><span class="sxs-lookup"><span data-stu-id="4464c-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="4464c-121">Tlbimp.exe (importateur de bibliothèques de types)</span><span class="sxs-lookup"><span data-stu-id="4464c-121">Tlbimp.exe (Type Library Importer)</span></span>](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 <span data-ttu-id="4464c-122">Décrit l’outil que vous pouvez utiliser pour convertir les définitions de type trouvées dans une bibliothèque de types COM en définitions équivalentes dans un assembly du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="4464c-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
