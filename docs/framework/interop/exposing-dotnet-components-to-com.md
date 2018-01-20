---
title: "Exposition de composants .NET Framework à COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3d34c60a5c2cae5abaa6763b935f6d11a29a39e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="7249d-102">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="7249d-102">Exposing .NET Framework Components to COM</span></span>
<span data-ttu-id="7249d-103">L’écriture d’un type .NET et l’utilisation de ce type à partir de code non managé sont deux activités distinctes pour les développeurs.</span><span class="sxs-lookup"><span data-stu-id="7249d-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="7249d-104">Cette section contient plusieurs conseils pour l’écriture de code managé interagissant avec des clients COM :</span><span class="sxs-lookup"><span data-stu-id="7249d-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>  
  
-   <span data-ttu-id="7249d-105">[Qualification des types .NET pour l’interopérabilité](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="7249d-105">[Qualifying .NET types for interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
     <span data-ttu-id="7249d-106">Tous les types, méthodes, propriétés, champs et événements managés que vous voulez exposer à COM doivent être publics.</span><span class="sxs-lookup"><span data-stu-id="7249d-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="7249d-107">Les types doivent avoir un constructeur public par défaut, qui est le seul constructeur pouvant être appelé dans COM.</span><span class="sxs-lookup"><span data-stu-id="7249d-107">Types must have a public default constructor, which is the only constructor that can be invoked through COM.</span></span>  
  
-   <span data-ttu-id="7249d-108">[Application d’attributs d’interopérabilité](../../../docs/framework/interop/applying-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="7249d-108">[Applying interop attributes](../../../docs/framework/interop/applying-interop-attributes.md).</span></span>  
  
     <span data-ttu-id="7249d-109">Les attributs personnalisés dans du code managé peuvent améliorer l’interopérabilité d’un composant.</span><span class="sxs-lookup"><span data-stu-id="7249d-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>  
  
-   <span data-ttu-id="7249d-110">[Empaquetage d’un assembly pour COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="7249d-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>  
  
     <span data-ttu-id="7249d-111">Les développeurs COM peuvent vous demander de résumer les étapes impliquées dans le référencement et le déploiement de vos assemblys.</span><span class="sxs-lookup"><span data-stu-id="7249d-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>  
  
 <span data-ttu-id="7249d-112">De plus, cette section identifie les tâches relatives à la consommation d’un type managé à partir d’un client COM.</span><span class="sxs-lookup"><span data-stu-id="7249d-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>  
  
#### <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="7249d-113">Pour consommer un type managé à partir de COM</span><span class="sxs-lookup"><span data-stu-id="7249d-113">To consume a managed type from COM</span></span>  
  
1.  <span data-ttu-id="7249d-114">[Inscription d’assemblys auprès de COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="7249d-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>  
  
     <span data-ttu-id="7249d-115">Les types d’un assembly (et des bibliothèques de types) doivent être inscrits au moment du design.</span><span class="sxs-lookup"><span data-stu-id="7249d-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="7249d-116">Si un programme d’installation n’inscrit pas l’assembly, indiquez aux développeurs COM qu’ils doivent utiliser Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="7249d-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>  
  
2.  <span data-ttu-id="7249d-117">[Référencer des types .NET à partir de COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)</span><span class="sxs-lookup"><span data-stu-id="7249d-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>  
  
     <span data-ttu-id="7249d-118">Les développeurs COM peuvent référencer des types dans un assembly en utilisant les mêmes outils et techniques que ceux qu’ils utilisent aujourd’hui.</span><span class="sxs-lookup"><span data-stu-id="7249d-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>  
  
3.  <span data-ttu-id="7249d-119">[Appel d’un objet .NET](http://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33).</span><span class="sxs-lookup"><span data-stu-id="7249d-119">[Call a .NET object](http://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33).</span></span>  
  
     <span data-ttu-id="7249d-120">Les développeurs COM peuvent appeler des méthodes sur l’objet .NET de la même façon qu’ils appellent des méthodes sur un type non managé.</span><span class="sxs-lookup"><span data-stu-id="7249d-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="7249d-121">Par exemple, l’API **CoCreateInstance** de COM active des objets .NET.</span><span class="sxs-lookup"><span data-stu-id="7249d-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>  
  
4.  <span data-ttu-id="7249d-122">[Déploiement d’une application pour accéder à COM](http://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce).</span><span class="sxs-lookup"><span data-stu-id="7249d-122">[Deploy an application for COM access](http://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce).</span></span>  
  
     <span data-ttu-id="7249d-123">Un assembly avec nom fort peut être installé dans le Global Assembly Cache et nécessite une signature de son éditeur.</span><span class="sxs-lookup"><span data-stu-id="7249d-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="7249d-124">Les assemblys qui n’ont pas de nom fort doivent être installés dans le répertoire de l’application du client.</span><span class="sxs-lookup"><span data-stu-id="7249d-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7249d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7249d-125">See Also</span></span>  
 [<span data-ttu-id="7249d-126">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="7249d-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="7249d-127">COM Interop, exemple : client COM et serveur .NET</span><span class="sxs-lookup"><span data-stu-id="7249d-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
