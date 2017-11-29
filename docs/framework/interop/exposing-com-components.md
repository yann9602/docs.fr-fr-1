---
title: Exposition de composants COM au .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26efd43a05252e657626063d7dd04b1020dace18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="94687-102">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="94687-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="94687-103">Cette section résume le processus nécessaire pour exposer un composant COM existant à du code managé.</span><span class="sxs-lookup"><span data-stu-id="94687-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="94687-104">Pour plus d’informations sur l’écriture de serveurs COM qui s’intègrent étroitement au .NET Framework, consultez [Considérations de design pour l’interopérabilité](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689).</span><span class="sxs-lookup"><span data-stu-id="94687-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689).</span></span>  
  
 <span data-ttu-id="94687-105">Les composants COM existants sont des ressources importantes dans le code managé, en tant qu’applications métier de couche intermédiaire ou en tant que fonctionnalités isolées.</span><span class="sxs-lookup"><span data-stu-id="94687-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="94687-106">Un composant idéal a un assembly PIA et se conforme étroitement aux normes de programmation imposées par COM.</span><span class="sxs-lookup"><span data-stu-id="94687-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="94687-107">Pour exposer des composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="94687-107">To expose COM components to the .NET Framework</span></span>  
  
1.  <span data-ttu-id="94687-108">[Importation d’une bibliothèque de types sous la forme d’un assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="94687-108">[Import a type library as an assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="94687-109">Le common language runtime nécessite des métadonnées pour tous les types, y compris les types COM.</span><span class="sxs-lookup"><span data-stu-id="94687-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="94687-110">Il existe plusieurs manières d’obtenir un assembly contenant des types COM importés en tant que métadonnées.</span><span class="sxs-lookup"><span data-stu-id="94687-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2.  <span data-ttu-id="94687-111">[Création de types COM dans du code managé](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).</span><span class="sxs-lookup"><span data-stu-id="94687-111">[Create COM types in managed Code](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).</span></span>  
  
     <span data-ttu-id="94687-112">Vous pouvez inspecter des types COM, activer des instances et appeler des méthodes sur l’objet COM de la même façon que vous le feriez pour n’importe quel type managé.</span><span class="sxs-lookup"><span data-stu-id="94687-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3.  <span data-ttu-id="94687-113">[Compilation d’un projet d’interopérabilité](../../../docs/framework/interop/compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="94687-113">[Compile an interop project](../../../docs/framework/interop/compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="94687-114">Le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] fournit des compilateurs pour plusieurs langages conformes à la Common Language Specification (CLS), notamment [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# et C++.</span><span class="sxs-lookup"><span data-stu-id="94687-114">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides compilers for several languages compliant with the Common Language Specification (CLS), including [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++.</span></span>  
  
4.  <span data-ttu-id="94687-115">[Déploiement d’une application d’interopérabilité](../../../docs/framework/interop/deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="94687-115">[Deploy an interop application](../../../docs/framework/interop/deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="94687-116">La meilleure façon de déployer des applications d’interopérabilité est de le faire en tant qu’assemblys signés [avec nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md) dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="94687-116">Interop applications are best deployed as [strong-named](../../../docs/framework/app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94687-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94687-117">See Also</span></span>  
 [<span data-ttu-id="94687-118">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="94687-118">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="94687-119">Considérations de design pour l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="94687-119">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 [<span data-ttu-id="94687-120">Exemple COM Interop : client .NET et serveur COM</span><span class="sxs-lookup"><span data-stu-id="94687-120">COM Interop Sample: .NET Client and COM Server</span></span>](../../../docs/framework/interop/com-interop-sample-net-client-and-com-server.md)  
 [<span data-ttu-id="94687-121">Indépendance du langage et composants indépendants du langage</span><span class="sxs-lookup"><span data-stu-id="94687-121">Language Independence and Language-Independent Components</span></span>](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="94687-122">Gacutil.exe (outil Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="94687-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
