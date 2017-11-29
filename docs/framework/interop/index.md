---
title: "Interopération avec du code non managé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2db5b8c2425637e24086f54e8ef69b0e5aac3633
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="d5727-102">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="d5727-102">Interoperating with Unmanaged Code</span></span>
<span data-ttu-id="d5727-103">Le .NET Framework assure l’interaction avec les composants COM, les services COM+, les bibliothèques de types externes et de nombreux services de systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="d5727-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="d5727-104">Les types de données, les signatures de méthode et les mécanismes de gestion des erreurs varient selon les modèles objet managés et non managés.</span><span class="sxs-lookup"><span data-stu-id="d5727-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="d5727-105">Pour simplifier l’interopérabilité entre les composants .NET Framework et le code non managé ainsi que pour faciliter la migration, le common language runtime dissimule à la fois aux clients et aux serveurs les différences entre ces modèles objet.</span><span class="sxs-lookup"><span data-stu-id="d5727-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>  
  
 <span data-ttu-id="d5727-106">Le code qui s’exécute sous le contrôle du runtime est appelé code managé.</span><span class="sxs-lookup"><span data-stu-id="d5727-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="d5727-107">Inversement, le code qui s’exécute en dehors du runtime est appelé code non managé.</span><span class="sxs-lookup"><span data-stu-id="d5727-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="d5727-108">Les composants COM, les interfaces ActiveX et les fonctions API Win32 sont des exemples de code non managé.</span><span class="sxs-lookup"><span data-stu-id="d5727-108">COM components, ActiveX interfaces, and Win32 API functions are examples of unmanaged code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5727-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d5727-109">In This Section</span></span>  
 [<span data-ttu-id="d5727-110">Rubriques Comment sur l’interopérabilité avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="d5727-110">Interoperating with Unmanaged Code How-to Topics</span></span>](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 <span data-ttu-id="d5727-111">Fournit des liens vers toutes les rubriques de guide pratique qui se trouvent dans la documentation conceptuelle relative à l’interopérabilité avec du code non managé.</span><span class="sxs-lookup"><span data-stu-id="d5727-111">Provides links to all How-to topics found in the conceptual documentation for interoperating with unmanaged code.</span></span>  
  
 [<span data-ttu-id="d5727-112">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d5727-112">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 <span data-ttu-id="d5727-113">Explique comment utiliser des composants COM à partir d’applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5727-113">Describes how to use COM components from .NET Framework applications.</span></span>  
  
 [<span data-ttu-id="d5727-114">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="d5727-114">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="d5727-115">Explique comment utiliser des composants .NET Framework à partir d’applications COM.</span><span class="sxs-lookup"><span data-stu-id="d5727-115">Describes how to use .NET Framework components from COM applications.</span></span>  
  
 [<span data-ttu-id="d5727-116">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="d5727-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="d5727-117">Décrit comment appeler des fonctions DLL non managées à l’aide de l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="d5727-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="d5727-118">Considérations de design pour l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="d5727-118">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 <span data-ttu-id="d5727-119">Fournit des conseils pour l'écriture de composants COM intégrés.</span><span class="sxs-lookup"><span data-stu-id="d5727-119">Provides tips for writing integrated COM components.</span></span>  
  
 [<span data-ttu-id="d5727-120">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="d5727-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 <span data-ttu-id="d5727-121">Décrit le marshaling de COM Interop et de l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="d5727-121">Describes marshaling for COM interop and platform invoke.</span></span>  
  
 [<span data-ttu-id="d5727-122">Guide pratique pour mapper des HRESULT et des exceptions</span><span class="sxs-lookup"><span data-stu-id="d5727-122">How to: Map HRESULTs and Exceptions</span></span>](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 <span data-ttu-id="d5727-123">Décrit le mappage entre les exceptions et les valeurs HRESULT.</span><span class="sxs-lookup"><span data-stu-id="d5727-123">Describes the mapping between exceptions and HRESULTs.</span></span>  
  
 [<span data-ttu-id="d5727-124">Interopérabilité à l’aide de types génériques</span><span class="sxs-lookup"><span data-stu-id="d5727-124">Interoperating Using Generic Types</span></span>](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 <span data-ttu-id="d5727-125">Décrit le comportement de types génériques en cas d’utilisation dans COM Interop.</span><span class="sxs-lookup"><span data-stu-id="d5727-125">Describes the behavior of generic types when used in COM interop.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d5727-126">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d5727-126">Related Sections</span></span>  
 [<span data-ttu-id="d5727-127">Interopérabilité COM avancée</span><span class="sxs-lookup"><span data-stu-id="d5727-127">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="d5727-128">Fournit des liens vers des informations sur l'incorporation de composants COM dans une application .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5727-128">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>
