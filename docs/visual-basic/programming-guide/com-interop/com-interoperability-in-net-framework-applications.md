---
title: "Interopérabilité COM dans les Applications .NET Framework (Visual Basic) | Documents Microsoft"
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
- interoperability, COM and .NET framework objects
- COM interop
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
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
ms.openlocfilehash: 6b68f35c1c63e2d7d229f89336b86c4a062e5ec9
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="a096f-102">Interopérabilité COM dans les applications .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a096f-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="a096f-103">Lorsque vous souhaitez utiliser les objets COM et .NET Framework dans la même application, vous devez résoudre les différences dans la façon dont les objets existent dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="a096f-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="a096f-104">Un objet .NET Framework se trouve dans la mémoire managée, la mémoire contrôlée par le common language runtime et peut être déplacé par le runtime si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a096f-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="a096f-105">Un objet COM se trouve dans la mémoire non managée et n’est pas prévu de passer à un autre emplacement de mémoire.</span><span class="sxs-lookup"><span data-stu-id="a096f-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="a096f-106">et [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fournissent des outils pour contrôler l’interaction de ces composants managés et.</span><span class="sxs-lookup"><span data-stu-id="a096f-106"> and the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="a096f-107">Pour plus d’informations sur le code managé, consultez [Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482).</span><span class="sxs-lookup"><span data-stu-id="a096f-107">For more information about managed code, see [Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482).</span></span>  
  
 <span data-ttu-id="a096f-108">Outre l’utilisation des objets COM dans les applications .NET, vous pouvez également utiliser [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour développer des objets accessibles à partir de code non managé via COM.</span><span class="sxs-lookup"><span data-stu-id="a096f-108">In addition to using COM objects in .NET applications, you may also want to use [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="a096f-109">Les liens de cette page fournissent des détails sur les interactions entre les objets COM et .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a096f-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a096f-110">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a096f-110">Related Sections</span></span>  
 [<span data-ttu-id="a096f-111">COM Interop</span><span class="sxs-lookup"><span data-stu-id="a096f-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="a096f-112">Fournit des liens vers des rubriques traitant de l’interopérabilité COM dans Visual Basic, y compris COM objets ActiveX contrôles, les DLL Win32, les objets managés et l’héritage d’objets COM.</span><span class="sxs-lookup"><span data-stu-id="a096f-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="a096f-113">Erreur de Wrapper COM Interop</span><span class="sxs-lookup"><span data-stu-id="a096f-113">COM Interop Wrapper Error</span></span>](https://docs.microsoft.com/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="a096f-114">Décrit les conséquences et les options si le système de projet ne peut pas créer un wrapper d’interopérabilité COM pour un composant particulier.</span><span class="sxs-lookup"><span data-stu-id="a096f-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="a096f-115">Interopération avec du Code non managé</span><span class="sxs-lookup"><span data-stu-id="a096f-115">Interoperating with Unmanaged Code</span></span>](https://msdn.microsoft.com/library/sd10k43k)  
 <span data-ttu-id="a096f-116">Certains problèmes d’interaction entre du code managé et décrit brièvement et fournit des liens pour approfondir ce sujet.</span><span class="sxs-lookup"><span data-stu-id="a096f-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="a096f-117">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="a096f-117">COM Wrappers</span></span>](http://msdn.microsoft.com/library/e56c485b-6b67-4345-8e66-fd21835a6092)  
 <span data-ttu-id="a096f-118">Traite des wrappers RCW, qui permettent au code managé d’appeler les méthodes COM, et par COM, qui permettent aux clients COM d’appeler les méthodes d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="a096f-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="a096f-119">Interopérabilité COM avancée</span><span class="sxs-lookup"><span data-stu-id="a096f-119">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="a096f-120">Fournit des liens vers des rubriques traitant de l’interopérabilité COM en ce qui concerne les wrappers, exceptions, l’héritage, threads, événements, les conversions et marshaling.</span><span class="sxs-lookup"><span data-stu-id="a096f-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="a096f-121">Tlbimp.exe (Type Library Importer)</span><span class="sxs-lookup"><span data-stu-id="a096f-121">Tlbimp.exe (Type Library Importer)</span></span>](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 <span data-ttu-id="a096f-122">Décrit l’outil que vous pouvez utiliser pour convertir les définitions de type trouvées dans une bibliothèque de types COM en définitions équivalentes dans un assembly du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="a096f-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
