---
title: "Interfaces de débogage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de2469d15eef40b9ef283d67aeca429d9d96a7ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-interfaces"></a><span data-ttu-id="0f863-102">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0f863-102">Debugging Interfaces</span></span>
<span data-ttu-id="0f863-103">Cette section décrit les interfaces non managées qui gèrent le débogage d'un programme s'exécutant dans le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="0f863-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f863-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0f863-104">In This Section</span></span>  
 [<span data-ttu-id="0f863-105">ICLRDataEnumMemoryRegions (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-105">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 <span data-ttu-id="0f863-106">Fournit une méthode pour énumérer les régions de mémoire qui sont spécifiées par les appelants.</span><span class="sxs-lookup"><span data-stu-id="0f863-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 [<span data-ttu-id="0f863-107">ICLRDataEnumMemoryRegionsCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-107">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 <span data-ttu-id="0f863-108">Fournit une méthode de rappel pour que `EnumMemoryRegions` rapporte au débogueur le résultat d'une tentative d'énumération d'une région spécifiée de mémoire.</span><span class="sxs-lookup"><span data-stu-id="0f863-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 [<span data-ttu-id="0f863-109">ICLRDataTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-109">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 <span data-ttu-id="0f863-110">Fournit des méthodes pour l'interaction avec un processus CLR cible.</span><span class="sxs-lookup"><span data-stu-id="0f863-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 [<span data-ttu-id="0f863-111">ICLRDataTarget2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-111">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 <span data-ttu-id="0f863-112">Sous-classe de `ICLRDataTarget` qui est utilisée par la couche des services d'accès aux données pour manipuler les régions de la mémoire virtuelle dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="0f863-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 [<span data-ttu-id="0f863-113">Iclrdatatarget3, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-113">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 <span data-ttu-id="0f863-114">Une sous-classe de [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) qui fournit l’accès aux informations sur l’exception.</span><span class="sxs-lookup"><span data-stu-id="0f863-114">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 [<span data-ttu-id="0f863-115">ICLRDebugging (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-115">ICLRDebugging Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 <span data-ttu-id="0f863-116">Fournit des méthodes qui gèrent le chargement et le déchargement des modules pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="0f863-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 [<span data-ttu-id="0f863-117">ICLRDebuggingLibraryProvider (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-117">ICLRDebuggingLibraryProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 <span data-ttu-id="0f863-118">Inclut le [ProvideLibrary, méthode](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) méthode, qui obtient un fournisseur de bibliothèque interface de rappel qui permet de common language runtime des bibliothèques de débogage spécifiques à la version à la demande et le chargement.</span><span class="sxs-lookup"><span data-stu-id="0f863-118">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 [<span data-ttu-id="0f863-119">ICLRMetadataLocator (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-119">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 <span data-ttu-id="0f863-120">Interface utilisée par la couche des services d'accès aux données pour localiser les métadonnées des assemblys dans un processus cible.</span><span class="sxs-lookup"><span data-stu-id="0f863-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 [<span data-ttu-id="0f863-121">ICorDebug (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 <span data-ttu-id="0f863-122">Fournit des méthodes qui permettent aux développeurs de déboguer des applications dans l'environnement du CLR.</span><span class="sxs-lookup"><span data-stu-id="0f863-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="0f863-123">ICorDebugAppDomain Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-123">ICorDebugAppDomain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 <span data-ttu-id="0f863-124">Fournit des méthodes pour le débogage de domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="0f863-124">Provides methods for debugging application domains.</span></span>  
  
 [<span data-ttu-id="0f863-125">ICorDebugAppDomain2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-125">ICorDebugAppDomain2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 <span data-ttu-id="0f863-126">Fournit des méthodes destinées au travail avec les tableaux, les pointeurs, les pointeurs fonction et les types ByRef.</span><span class="sxs-lookup"><span data-stu-id="0f863-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="0f863-127">Cette interface est une extension de l'interface `ICorDebugAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="0f863-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 [<span data-ttu-id="0f863-128">ICorDebugAppDomain3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-128">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 <span data-ttu-id="0f863-129">Fournit des méthodes pour utiliser [!INCLUDE[wrt](../../../../includes/wrt-md.md)] dans un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="0f863-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="0f863-130">Cette interface est une extension des interfaces `ICorDebugAppDomain` et `ICorDebugAppDomain2`.</span><span class="sxs-lookup"><span data-stu-id="0f863-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 [<span data-ttu-id="0f863-131">Icordebugappdomain4, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-131">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 <span data-ttu-id="0f863-132">Étend logiquement le [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface à obtenir un objet managé à partir d’un wrapper CCW.</span><span class="sxs-lookup"><span data-stu-id="0f863-132">Logically extends the [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 [<span data-ttu-id="0f863-133">ICorDebugAppDomainEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-133">ICorDebugAppDomainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 <span data-ttu-id="0f863-134">Fournit une méthode qui retourne un nombre spécifié de valeurs `ICorDebugAppDomain` qui démarrent à l'emplacement suivant dans l'énumération.</span><span class="sxs-lookup"><span data-stu-id="0f863-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 [<span data-ttu-id="0f863-135">ICorDebugArrayValue Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-135">ICorDebugArrayValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 <span data-ttu-id="0f863-136">Sous-classe de `ICorDebugHeapValue` qui représente un tableau unidimensionnel ou multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="0f863-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 [<span data-ttu-id="0f863-137">ICorDebugAssembly Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-137">ICorDebugAssembly Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 <span data-ttu-id="0f863-138">Représente un assembly.</span><span class="sxs-lookup"><span data-stu-id="0f863-138">Represents an assembly.</span></span>  
  
 [<span data-ttu-id="0f863-139">ICorDebugAssembly2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-139">ICorDebugAssembly2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 <span data-ttu-id="0f863-140">Représente un assembly.</span><span class="sxs-lookup"><span data-stu-id="0f863-140">Represents an assembly.</span></span> <span data-ttu-id="0f863-141">Cette interface est une extension de l'interface `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="0f863-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 [<span data-ttu-id="0f863-142">Icordebugassembly3, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-142">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 <span data-ttu-id="0f863-143">Étend logiquement le [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface afin de fournir la prise en charge pour les assemblys conteneurs et les assemblys.</span><span class="sxs-lookup"><span data-stu-id="0f863-143">Logically extends the [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="0f863-144">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-144">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-145">ICorDebugAssemblyEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-145">ICorDebugAssemblyEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 <span data-ttu-id="0f863-146">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="0f863-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 [<span data-ttu-id="0f863-147">ICorDebugBlockingObjectEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-147">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 <span data-ttu-id="0f863-148">Fournit un énumérateur pour une liste de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span><span class="sxs-lookup"><span data-stu-id="0f863-148">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
 [<span data-ttu-id="0f863-149">ICorDebugBoxValue Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-149">ICorDebugBoxValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 <span data-ttu-id="0f863-150">Sous-classe de `ICorDebugHeapValue` qui représente un objet classe de valeur boxed.</span><span class="sxs-lookup"><span data-stu-id="0f863-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 [<span data-ttu-id="0f863-151">ICorDebugBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-151">ICorDebugBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 <span data-ttu-id="0f863-152">Représente un point d'arrêt dans une fonction ou un point de contrôle sur une valeur.</span><span class="sxs-lookup"><span data-stu-id="0f863-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 [<span data-ttu-id="0f863-153">ICorDebugBreakpointEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-153">ICorDebugBreakpointEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 <span data-ttu-id="0f863-154">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="0f863-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 [<span data-ttu-id="0f863-155">ICorDebugChain Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-155">ICorDebugChain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 <span data-ttu-id="0f863-156">Représente un segment d'une pile des appels physique ou logique.</span><span class="sxs-lookup"><span data-stu-id="0f863-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 [<span data-ttu-id="0f863-157">ICorDebugChainEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-157">ICorDebugChainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 <span data-ttu-id="0f863-158">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugChain`.</span><span class="sxs-lookup"><span data-stu-id="0f863-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 [<span data-ttu-id="0f863-159">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-159">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 <span data-ttu-id="0f863-160">Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur).</span><span class="sxs-lookup"><span data-stu-id="0f863-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="0f863-161">Si le type est générique, `ICorDebugClass` représente le type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="0f863-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 [<span data-ttu-id="0f863-162">ICorDebugClass2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-162">ICorDebugClass2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 <span data-ttu-id="0f863-163">Représente une classe générique ou une classe avec un paramètre de méthode de type <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="0f863-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="0f863-164">Cette interface étend `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="0f863-164">This interface extends `ICorDebugClass`.</span></span>  
  
 [<span data-ttu-id="0f863-165">ICorDebugCode Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-165">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 <span data-ttu-id="0f863-166">Représente un segment de code MSIL ou de code natif.</span><span class="sxs-lookup"><span data-stu-id="0f863-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 [<span data-ttu-id="0f863-167">ICorDebugCode2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-167">ICorDebugCode2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 <span data-ttu-id="0f863-168">Fournit des méthodes qui étendent les fonctions de `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="0f863-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 [<span data-ttu-id="0f863-169">Icordebugcode3, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-169">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 <span data-ttu-id="0f863-170">Fournit une méthode qui étend [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) et [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) pour fournir des informations sur une valeur de retournée managée.</span><span class="sxs-lookup"><span data-stu-id="0f863-170">Provides a method that extends [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) and [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 [<span data-ttu-id="0f863-171">Interface de ICorDebugCode4</span><span class="sxs-lookup"><span data-stu-id="0f863-171">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 <span data-ttu-id="0f863-172">Fournit une méthode qui permet à un débogueur énumérer les variables locales et les arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="0f863-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="0f863-173">ICorDebugCodeEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-173">ICorDebugCodeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 <span data-ttu-id="0f863-174">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="0f863-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 [<span data-ttu-id="0f863-175">ICorDebugComObjectValue (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-175">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 <span data-ttu-id="0f863-176">Fournit des méthodes pour récupérer des objets d'interface mis en cache.</span><span class="sxs-lookup"><span data-stu-id="0f863-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 [<span data-ttu-id="0f863-177">ICorDebugContext Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-177">ICorDebugContext Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 <span data-ttu-id="0f863-178">Représente un objet de contexte.</span><span class="sxs-lookup"><span data-stu-id="0f863-178">Represents a context object.</span></span> <span data-ttu-id="0f863-179">Cette interface n'a pas encore été implémentée.</span><span class="sxs-lookup"><span data-stu-id="0f863-179">This interface has not been implemented yet.</span></span>  
  
 [<span data-ttu-id="0f863-180">ICorDebugController Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-180">ICorDebugController Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 <span data-ttu-id="0f863-181">Représente une portée, un <xref:System.Diagnostics.Process> ou un <xref:System.AppDomain>, où le contexte d'exécution du code peut être contrôlé.</span><span class="sxs-lookup"><span data-stu-id="0f863-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 [<span data-ttu-id="0f863-182">ICorDebugDataTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-182">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 <span data-ttu-id="0f863-183">Fournit une interface de rappel qui permet d'accéder à un processus cible particulier.</span><span class="sxs-lookup"><span data-stu-id="0f863-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 [<span data-ttu-id="0f863-184">Icordebugdatatarget2, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-184">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 <span data-ttu-id="0f863-185">Étend logiquement le [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="0f863-185">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="0f863-186">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-186">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-187">Icordebugdatatarget3, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-187">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 <span data-ttu-id="0f863-188">Étend logiquement le [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface pour fournir des informations sur les modules chargés.</span><span class="sxs-lookup"><span data-stu-id="0f863-188">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="0f863-189">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-189">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-190">Icordebugdebugevent, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-190">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 <span data-ttu-id="0f863-191">Définit l'interface de base de laquelle dérivent tous les événements de débogage `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="0f863-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="0f863-192">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-192">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-193">ICorDebugEditAndContinueErrorInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-193">ICorDebugEditAndContinueErrorInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 <span data-ttu-id="0f863-194">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="0f863-194">Obsolete.</span></span> <span data-ttu-id="0f863-195">N'utilisez pas cette interface.</span><span class="sxs-lookup"><span data-stu-id="0f863-195">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="0f863-196">ICorDebugEditAndContinueSnapshot Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-196">ICorDebugEditAndContinueSnapshot Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 <span data-ttu-id="0f863-197">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="0f863-197">Obsolete.</span></span> <span data-ttu-id="0f863-198">N'utilisez pas cette interface.</span><span class="sxs-lookup"><span data-stu-id="0f863-198">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="0f863-199">ICorDebugEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-199">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 <span data-ttu-id="0f863-200">Sert d’interface de base abstraite pour déboguer des énumérateurs.</span><span class="sxs-lookup"><span data-stu-id="0f863-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 [<span data-ttu-id="0f863-201">ICorDebugErrorInfoEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-201">ICorDebugErrorInfoEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 <span data-ttu-id="0f863-202">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="0f863-202">Obsolete.</span></span> <span data-ttu-id="0f863-203">N'utilisez pas cette interface.</span><span class="sxs-lookup"><span data-stu-id="0f863-203">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="0f863-204">ICorDebugEval Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-204">ICorDebugEval Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 <span data-ttu-id="0f863-205">Fournit des méthodes pour permettre au débogueur d'exécuter le code à l'intérieur du contexte du code en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="0f863-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 [<span data-ttu-id="0f863-206">ICorDebugEval2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-206">ICorDebugEval2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 <span data-ttu-id="0f863-207">Étend `ICorDebugEval` pour offrir une prise en charge pour les types génériques.</span><span class="sxs-lookup"><span data-stu-id="0f863-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 [<span data-ttu-id="0f863-208">Icordebugexceptiondebugevent, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-208">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 <span data-ttu-id="0f863-209">Étend la [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface pour prendre en charge les événements d’exception.</span><span class="sxs-lookup"><span data-stu-id="0f863-209">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="0f863-210">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-210">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-211">ICorDebugExceptionObjectCallStackEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-211">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 <span data-ttu-id="0f863-212">Fournit un énumérateur pour les informations de la pile des appels qui sont incorporées dans un objet exception.</span><span class="sxs-lookup"><span data-stu-id="0f863-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 [<span data-ttu-id="0f863-213">ICorDebugExceptionObjectValue (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-213">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 <span data-ttu-id="0f863-214">Étend la [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface pour fournir des informations de trace de pile à partir d’un objet d’exception managée.</span><span class="sxs-lookup"><span data-stu-id="0f863-214">Extends the [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 [<span data-ttu-id="0f863-215">ICorDebugFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-215">ICorDebugFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 <span data-ttu-id="0f863-216">Représente un frame sur la pile en cours.</span><span class="sxs-lookup"><span data-stu-id="0f863-216">Represents a frame on the current stack.</span></span>  
  
 [<span data-ttu-id="0f863-217">ICorDebugFrameEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-217">ICorDebugFrameEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 <span data-ttu-id="0f863-218">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="0f863-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 [<span data-ttu-id="0f863-219">ICorDebugFunction Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-219">ICorDebugFunction Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 <span data-ttu-id="0f863-220">Représente une fonction ou une méthode managée.</span><span class="sxs-lookup"><span data-stu-id="0f863-220">Represents a managed function or method.</span></span>  
  
 [<span data-ttu-id="0f863-221">ICorDebugFunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-221">ICorDebugFunction2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 <span data-ttu-id="0f863-222">Étend logiquement `ICorDebugFunction` pour prendre en charge le débogage pas à pas pour « Uniquement mon code ».</span><span class="sxs-lookup"><span data-stu-id="0f863-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 [<span data-ttu-id="0f863-223">Icordebugfunction3, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-223">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 <span data-ttu-id="0f863-224">Étend logiquement le [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface pour fournir l’accès au code à partir d’une demande ReJIT.</span><span class="sxs-lookup"><span data-stu-id="0f863-224">Logically extends the [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 [<span data-ttu-id="0f863-225">ICorDebugFunctionBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-225">ICorDebugFunctionBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 <span data-ttu-id="0f863-226">Étend `ICorDebugBreakpoint` pour prendre en charge les points d'arrêt au sein de fonctions.</span><span class="sxs-lookup"><span data-stu-id="0f863-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 [<span data-ttu-id="0f863-227">ICorDebugGCReferenceEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-227">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 <span data-ttu-id="0f863-228">Fournit un énumérateur pour les objets qui sont récupérés par le récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="0f863-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 [<span data-ttu-id="0f863-229">ICorDebugGenericValue Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-229">ICorDebugGenericValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 <span data-ttu-id="0f863-230">Sous-classe de `ICorDebugValue` qui s'applique à toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="0f863-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="0f863-231">Cette interface fournit les méthodes Get et Set pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="0f863-231">This interface provides Get and Set methods for the value.</span></span>  
  
 [<span data-ttu-id="0f863-232">ICorDebugGuidToTypeEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-232">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 <span data-ttu-id="0f863-233">Fournit un énumérateur pour un objet qui mappe les GUID et leurs objets `ICorDebugType` correspondants.</span><span class="sxs-lookup"><span data-stu-id="0f863-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 [<span data-ttu-id="0f863-234">ICorDebugHandleValue Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-234">ICorDebugHandleValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 <span data-ttu-id="0f863-235">Sous-classe de `ICorDebugReferenceValue` qui représente une valeur de référence dans laquelle le débogueur a créé un handle pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0f863-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 [<span data-ttu-id="0f863-236">ICorDebugHeapEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-236">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 <span data-ttu-id="0f863-237">Fournit un énumérateur pour les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="0f863-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 [<span data-ttu-id="0f863-238">ICorDebugHeapSegmentEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-238">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 <span data-ttu-id="0f863-239">Fournit un énumérateur pour les régions de mémoire du tas managé.</span><span class="sxs-lookup"><span data-stu-id="0f863-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 [<span data-ttu-id="0f863-240">ICorDebugHeapValue Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-240">ICorDebugHeapValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 <span data-ttu-id="0f863-241">Sous-classe de `ICorDebugValue` qui représente un objet qui a été collecté par le garbage collector du CLR.</span><span class="sxs-lookup"><span data-stu-id="0f863-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 [<span data-ttu-id="0f863-242">ICorDebugHeapValue2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-242">ICorDebugHeapValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 <span data-ttu-id="0f863-243">Extension de `ICorDebugHeapValue` qui fournit la prise en charge des handles d'exécution.</span><span class="sxs-lookup"><span data-stu-id="0f863-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 [<span data-ttu-id="0f863-244">ICorDebugHeapValue3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-244">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 <span data-ttu-id="0f863-245">Expose les propriétés du verrou du moniteur d'objets.</span><span class="sxs-lookup"><span data-stu-id="0f863-245">Exposes the monitor lock properties of objects.</span></span>  
  
 [<span data-ttu-id="0f863-246">Icordebugilcode, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-246">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 <span data-ttu-id="0f863-247">Représente un segment de code en langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="0f863-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 [<span data-ttu-id="0f863-248">Icordebugilcode2, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-248">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 <span data-ttu-id="0f863-249">Étend logiquement le [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface pour fournir des méthodes qui retournent le jeton de signature de variable locale d’une fonction et qui mappent le langage intermédiaire instrumenté d’un profileur (il Intermediate Language) aux offsets IL de méthode d’origine décalages.</span><span class="sxs-lookup"><span data-stu-id="0f863-249">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 [<span data-ttu-id="0f863-250">ICorDebugILFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-250">ICorDebugILFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 <span data-ttu-id="0f863-251">Représente un frame de pile de code MSIL.</span><span class="sxs-lookup"><span data-stu-id="0f863-251">Represents a stack frame of MSIL code.</span></span>  
  
 [<span data-ttu-id="0f863-252">ICorDebugILFrame2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-252">ICorDebugILFrame2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 <span data-ttu-id="0f863-253">Extension logique de `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="0f863-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 [<span data-ttu-id="0f863-254">Icordebugilframe3, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-254">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 <span data-ttu-id="0f863-255">Fournit une méthode qui encapsule la valeur de retour d'une fonction.</span><span class="sxs-lookup"><span data-stu-id="0f863-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 [<span data-ttu-id="0f863-256">Icordebugilframe4, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-256">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 <span data-ttu-id="0f863-257">Fournit des méthodes qui vous permettent d'accéder aux variables locales et au code dans un frame de pile de code de langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="0f863-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="0f863-258">Un paramètre spécifie si le débogueur a accès aux variables et au code ajoutés dans l'instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="0f863-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="0f863-259">Icordebuginstancefieldsymbol, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-259">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 <span data-ttu-id="0f863-260">Représente les informations sur les symboles de débogage pour un champ d’instance.</span><span class="sxs-lookup"><span data-stu-id="0f863-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="0f863-261">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-261">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-262">ICorDebugInternalFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-262">ICorDebugInternalFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 <span data-ttu-id="0f863-263">Identifie les types de frame pour le débogueur.</span><span class="sxs-lookup"><span data-stu-id="0f863-263">Identifies frame types for the debugger.</span></span>  
  
 [<span data-ttu-id="0f863-264">ICorDebugInternalFrame2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-264">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 <span data-ttu-id="0f863-265">Fournit des informations sur les frames internes, notamment l’adresse de la pile et la position par rapport à [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objets.</span><span class="sxs-lookup"><span data-stu-id="0f863-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objects.</span></span>  
  
 [<span data-ttu-id="0f863-266">Icordebugloadedmodule, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-266">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 <span data-ttu-id="0f863-267">Fournit des informations sur un module chargé.</span><span class="sxs-lookup"><span data-stu-id="0f863-267">Provides information about a loaded module.</span></span> <span data-ttu-id="0f863-268">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-268">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-269">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-269">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 <span data-ttu-id="0f863-270">Fournit des méthodes pour traiter les rappels de débogueur.</span><span class="sxs-lookup"><span data-stu-id="0f863-270">Provides methods to process debugger callbacks.</span></span>  
  
 [<span data-ttu-id="0f863-271">ICorDebugManagedCallback2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-271">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 <span data-ttu-id="0f863-272">Fournit des méthodes pour prendre en charge la gestion des exceptions et les Assistants Débogage managé (MDA) du débogueur.</span><span class="sxs-lookup"><span data-stu-id="0f863-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="0f863-273">`ICorDebugManagedCallback2` est une extension logique de `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="0f863-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 [<span data-ttu-id="0f863-274">ICorDebugManagedCallback3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-274">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 <span data-ttu-id="0f863-275">Fournit une méthode de rappel indiquant qu'une notification de débogueur personnalisée active a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="0f863-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 [<span data-ttu-id="0f863-276">ICorDebugMDA (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-276">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 <span data-ttu-id="0f863-277">Représente un message d'Assistant Débogage managé (MDA).</span><span class="sxs-lookup"><span data-stu-id="0f863-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 [<span data-ttu-id="0f863-278">Icordebugmemorybuffer, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-278">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 <span data-ttu-id="0f863-279">Représente une mémoire tampon en mémoire.</span><span class="sxs-lookup"><span data-stu-id="0f863-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="0f863-280">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-280">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-281">Icordebugmergedassemblyrecord, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-281">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 <span data-ttu-id="0f863-282">Fournit des informations sur un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="0f863-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="0f863-283">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-283">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-284">ICorDebugMetaDataLocator (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-284">ICorDebugMetaDataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 <span data-ttu-id="0f863-285">Fournit des informations de métadonnées au débogueur.</span><span class="sxs-lookup"><span data-stu-id="0f863-285">Provides metadata information to the debugger.</span></span>  
  
 [<span data-ttu-id="0f863-286">ICorDebugModule Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-286">ICorDebugModule Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 <span data-ttu-id="0f863-287">Représente un module CLR qui est un fichier exécutable ou une bibliothèque de liens dynamiques (DLL).</span><span class="sxs-lookup"><span data-stu-id="0f863-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 [<span data-ttu-id="0f863-288">ICorDebugModule2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-288">ICorDebugModule2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 <span data-ttu-id="0f863-289">Sert d'extension logique de `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="0f863-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 [<span data-ttu-id="0f863-290">ICorDebugModule3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-290">ICorDebugModule3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 <span data-ttu-id="0f863-291">Crée un lecteur de symboles pour un module dynamique.</span><span class="sxs-lookup"><span data-stu-id="0f863-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 [<span data-ttu-id="0f863-292">ICorDebugModuleBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-292">ICorDebugModuleBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 <span data-ttu-id="0f863-293">Étend `ICorDebugBreakpoint` pour fournir l'accès aux modules spécifiques.</span><span class="sxs-lookup"><span data-stu-id="0f863-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 [<span data-ttu-id="0f863-294">Icordebugmoduledebugevent, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-294">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 <span data-ttu-id="0f863-295">Étend la [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface pour prendre en charge les événements au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="0f863-295">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="0f863-296">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-296">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-297">ICorDebugModuleEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-297">ICorDebugModuleEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 <span data-ttu-id="0f863-298">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="0f863-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 [<span data-ttu-id="0f863-299">Icordebugmutabledatatarget, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-299">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 <span data-ttu-id="0f863-300">Étend la [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface pour prendre en charge des cibles de données mutables.</span><span class="sxs-lookup"><span data-stu-id="0f863-300">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 [<span data-ttu-id="0f863-301">ICorDebugNativeFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-301">ICorDebugNativeFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 <span data-ttu-id="0f863-302">Implémentation spécialisée de `ICorDebugFrame` utilisée pour les frames natifs.</span><span class="sxs-lookup"><span data-stu-id="0f863-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 [<span data-ttu-id="0f863-303">ICorDebugNativeFrame2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-303">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 <span data-ttu-id="0f863-304">Fournit des méthodes qui testent les relations entre frames enfant et parent.</span><span class="sxs-lookup"><span data-stu-id="0f863-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 [<span data-ttu-id="0f863-305">ICorDebugObjectEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-305">ICorDebugObjectEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 <span data-ttu-id="0f863-306">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux d'objets par leurs adresses virtuelles relatives.</span><span class="sxs-lookup"><span data-stu-id="0f863-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 [<span data-ttu-id="0f863-307">ICorDebugObjectValue Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-307">ICorDebugObjectValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 <span data-ttu-id="0f863-308">Sous-classe de `ICorDebugValue` qui représente une valeur contenant un objet.</span><span class="sxs-lookup"><span data-stu-id="0f863-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 [<span data-ttu-id="0f863-309">ICorDebugObjectValue2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-309">ICorDebugObjectValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 <span data-ttu-id="0f863-310">Étend `ICorDebugObjectValue` pour prendre en charge l'héritage et les substitutions.</span><span class="sxs-lookup"><span data-stu-id="0f863-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 [<span data-ttu-id="0f863-311">ICorDebugProcess Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-311">ICorDebugProcess Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 <span data-ttu-id="0f863-312">Représente un processus qui exécute le code managé.</span><span class="sxs-lookup"><span data-stu-id="0f863-312">Represents a process that is executing managed code.</span></span>  
  
 [<span data-ttu-id="0f863-313">ICorDebugProcess2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-313">ICorDebugProcess2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 <span data-ttu-id="0f863-314">Extension logique de `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="0f863-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 [<span data-ttu-id="0f863-315">ICorDebugProcess3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-315">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 <span data-ttu-id="0f863-316">Contrôle les notifications de débogueur personnalisées.</span><span class="sxs-lookup"><span data-stu-id="0f863-316">Controls custom debugger notifications.</span></span>  
  
 [<span data-ttu-id="0f863-317">Icordebugprocess5, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-317">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 <span data-ttu-id="0f863-318">Étend la [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) local de l’interface pour prendre en charge l’accès au tas managé, pour fournir des informations sur le garbage collection d’objets gérés et pour déterminer si un débogueur charge des images à partir de l’application cache des images natives.</span><span class="sxs-lookup"><span data-stu-id="0f863-318">Extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 [<span data-ttu-id="0f863-319">Icordebugprocess6, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-319">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 <span data-ttu-id="0f863-320">Étend logiquement le [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface pour activer des fonctionnalités telles que le décodage des événements de débogage managés qui sont codés dans les événements de débogage d’exception native et fractionnement de module virtuel.</span><span class="sxs-lookup"><span data-stu-id="0f863-320">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="0f863-321">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-321">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-322">Icordebugprocess7, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-322">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 <span data-ttu-id="0f863-323">Fournit une méthode qui configure le débogueur afin de gérer les mises à jour des métadonnées en mémoire dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="0f863-323">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 [<span data-ttu-id="0f863-324">Icordebugprocess8, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-324">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 <span data-ttu-id="0f863-325">Étend logiquement le [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface pour activer ou désactiver certains types de [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) rappels d’exception.</span><span class="sxs-lookup"><span data-stu-id="0f863-325">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 [<span data-ttu-id="0f863-326">ICorDebugProcessEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-326">ICorDebugProcessEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 <span data-ttu-id="0f863-327">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="0f863-327">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 [<span data-ttu-id="0f863-328">ICorDebugReferenceValue Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-328">ICorDebugReferenceValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 <span data-ttu-id="0f863-329">Sous-classe de `ICorDebugValue` qui prend en charge les types référence.</span><span class="sxs-lookup"><span data-stu-id="0f863-329">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 [<span data-ttu-id="0f863-330">ICorDebugRegisterSet (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-330">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 <span data-ttu-id="0f863-331">Représente le jeu de registres disponible sur l'ordinateur qui exécute actuellement le code.</span><span class="sxs-lookup"><span data-stu-id="0f863-331">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 [<span data-ttu-id="0f863-332">ICorDebugRegisterSet2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-332">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 <span data-ttu-id="0f863-333">Étend les fonctionnalités de `ICorDebugRegisterSet` pour les plateformes matérielles qui possèdent plus de 64 registres.</span><span class="sxs-lookup"><span data-stu-id="0f863-333">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 [<span data-ttu-id="0f863-334">ICorDebugRemote (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-334">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 <span data-ttu-id="0f863-335">Fournit la possibilité de lancer ou de joindre un débogueur managé à un processus distant cible.</span><span class="sxs-lookup"><span data-stu-id="0f863-335">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 [<span data-ttu-id="0f863-336">ICorDebugRemoteTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-336">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 <span data-ttu-id="0f863-337">Fournit des méthodes qui vous permettent de déboguer les applications Silverlight dans l'environnement du CLR.</span><span class="sxs-lookup"><span data-stu-id="0f863-337">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="0f863-338">ICorDebugRuntimeUnwindableFrame, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-338">ICorDebugRuntimeUnwindableFrame Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 <span data-ttu-id="0f863-339">Fournit un support technique pour les méthodes non managées qui requièrent que le Common Language Runtime (CLR) déroule un frame.</span><span class="sxs-lookup"><span data-stu-id="0f863-339">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 [<span data-ttu-id="0f863-340">ICorDebugStackWalk (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-340">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 <span data-ttu-id="0f863-341">Fournit des méthodes pour obtenir les méthodes managées, ou frames, sur la pile d'un thread.</span><span class="sxs-lookup"><span data-stu-id="0f863-341">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 [<span data-ttu-id="0f863-342">Icordebugstaticfieldsymbol, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-342">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 <span data-ttu-id="0f863-343">Représente les informations sur les symboles de débogage pour un champ static.</span><span class="sxs-lookup"><span data-stu-id="0f863-343">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="0f863-344">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-344">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-345">ICorDebugStepper Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-345">ICorDebugStepper Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 <span data-ttu-id="0f863-346">Représente dans l'exécution du code une étape qui est effectuée par un débogueur, et qui sert d'identificateur entre l'émission et l'achèvement d'une commande tout en offrant un moyen d'annuler une étape.</span><span class="sxs-lookup"><span data-stu-id="0f863-346">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 [<span data-ttu-id="0f863-347">ICorDebugStepper2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-347">ICorDebugStepper2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 <span data-ttu-id="0f863-348">Prend en charge le débogage « Uniquement mon code ».</span><span class="sxs-lookup"><span data-stu-id="0f863-348">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 [<span data-ttu-id="0f863-349">ICorDebugStepperEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-349">ICorDebugStepperEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 <span data-ttu-id="0f863-350">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugStepper`.</span><span class="sxs-lookup"><span data-stu-id="0f863-350">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 [<span data-ttu-id="0f863-351">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-351">ICorDebugStringValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 <span data-ttu-id="0f863-352">Sous-classe de `ICorDebugHeapValue` qui s'applique aux valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="0f863-352">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 [<span data-ttu-id="0f863-353">Icordebugsymbolprovider, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-353">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 <span data-ttu-id="0f863-354">Fournit des méthodes pouvant être utilisées pour récupérer des informations sur les symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="0f863-354">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="0f863-355">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-355">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-356">Icordebugsymbolprovider2, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-356">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 <span data-ttu-id="0f863-357">Étend logiquement le [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface pour récupérer des informations sur les symboles de débogage supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="0f863-357">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="0f863-358">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-358">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-359">ICorDebugThread Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-359">ICorDebugThread Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 <span data-ttu-id="0f863-360">Représente un thread de processus.</span><span class="sxs-lookup"><span data-stu-id="0f863-360">Represents a thread in a process.</span></span> <span data-ttu-id="0f863-361">La durée de vie d'une instance `ICorDebugThread` est la même que la durée de vie du thread qu'elle représente.</span><span class="sxs-lookup"><span data-stu-id="0f863-361">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 [<span data-ttu-id="0f863-362">ICorDebugThread2 Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-362">ICorDebugThread2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 <span data-ttu-id="0f863-363">Sert d'extension logique de `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="0f863-363">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 [<span data-ttu-id="0f863-364">ICorDebugThread3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-364">ICorDebugThread3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 <span data-ttu-id="0f863-365">Fournit le point d’entrée pour le [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) et les interfaces correspondantes.</span><span class="sxs-lookup"><span data-stu-id="0f863-365">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 [<span data-ttu-id="0f863-366">ICorDebugThread4 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-366">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 <span data-ttu-id="0f863-367">Fournit des informations sur le blocage des threads.</span><span class="sxs-lookup"><span data-stu-id="0f863-367">Provides thread blocking information.</span></span>  
  
 [<span data-ttu-id="0f863-368">ICorDebugThreadEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-368">ICorDebugThreadEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 <span data-ttu-id="0f863-369">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="0f863-369">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 [<span data-ttu-id="0f863-370">ICorDebugType Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-370">ICorDebugType Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 <span data-ttu-id="0f863-371">Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur).</span><span class="sxs-lookup"><span data-stu-id="0f863-371">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="0f863-372">Si le type est générique, `ICorDebugType` représente le type générique instancié.</span><span class="sxs-lookup"><span data-stu-id="0f863-372">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 [<span data-ttu-id="0f863-373">Interface de ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="0f863-373">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 <span data-ttu-id="0f863-374">Étend la [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface pour récupérer l’identificateur de type d’un type de base ou complexe (défini par l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="0f863-374">Extends the [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 [<span data-ttu-id="0f863-375">ICorDebugTypeEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0f863-375">ICorDebugTypeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 <span data-ttu-id="0f863-376">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="0f863-376">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 [<span data-ttu-id="0f863-377">ICorDebugUnmanagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-377">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 <span data-ttu-id="0f863-378">Fournit une notification des événements natifs qui ne sont pas mis directement en rapport avec le CLR.</span><span class="sxs-lookup"><span data-stu-id="0f863-378">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="0f863-379">« ICorDebugValue »</span><span class="sxs-lookup"><span data-stu-id="0f863-379">"ICorDebugValue"</span></span>  
 <span data-ttu-id="0f863-380">Représente une valeur de lecture ou d'écriture dans le processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="0f863-380">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="0f863-381">« ICorDebugValue2 »</span><span class="sxs-lookup"><span data-stu-id="0f863-381">"ICorDebugValue2"</span></span>  
 <span data-ttu-id="0f863-382">Étend `ICorDebugValue` pour prendre en charge `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="0f863-382">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 [<span data-ttu-id="0f863-383">ICorDebugValue3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-383">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 <span data-ttu-id="0f863-384">Étend les interfaces « ICorDebugValue » et « ICorDebugValue2 » pour prendre en charge pour les tableaux supérieurs à 2 Go.</span><span class="sxs-lookup"><span data-stu-id="0f863-384">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="0f863-385">« ICorDebugValueBreakpoint »</span><span class="sxs-lookup"><span data-stu-id="0f863-385">"ICorDebugValueBreakpoint"</span></span>  
 <span data-ttu-id="0f863-386">Étend `ICorDebugBreakpoint` pour fournir l'accès aux valeurs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="0f863-386">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="0f863-387">« ICorDebugValueEnum »</span><span class="sxs-lookup"><span data-stu-id="0f863-387">"ICorDebugValueEnum"</span></span>  
 <span data-ttu-id="0f863-388">Implémente les méthodes `ICorDebugEnum` et énumère des tableaux `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="0f863-388">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 [<span data-ttu-id="0f863-389">Interface de ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="0f863-389">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 <span data-ttu-id="0f863-390">Représente une variable locale ou un argument d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="0f863-390">Represents a local variable or argument of a function.</span></span>  
  
 [<span data-ttu-id="0f863-391">Interface de ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="0f863-391">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 <span data-ttu-id="0f863-392">Fournit un énumérateur pour les variables locales et les arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="0f863-392">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="0f863-393">Icordebugvariablesymbol, Interface</span><span class="sxs-lookup"><span data-stu-id="0f863-393">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 <span data-ttu-id="0f863-394">Récupère les informations de symbole de débogage pour une variable.</span><span class="sxs-lookup"><span data-stu-id="0f863-394">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="0f863-395">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-395">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-396">ICorDebugVirtualUnwinder (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-396">ICorDebugVirtualUnwinder Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 <span data-ttu-id="0f863-397">Fournit des méthodes pour faciliter le déroulement de la pile.</span><span class="sxs-lookup"><span data-stu-id="0f863-397">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="0f863-398">**Disponible sur .NET Native uniquement.**</span><span class="sxs-lookup"><span data-stu-id="0f863-398">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="0f863-399">ICorPublish (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-399">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 <span data-ttu-id="0f863-400">Sert d'interface générale pour les processus de publication.</span><span class="sxs-lookup"><span data-stu-id="0f863-400">Serves as the general interface for the publishing processes.</span></span>  
  
 [<span data-ttu-id="0f863-401">ICorPublishAppDomain (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-401">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 <span data-ttu-id="0f863-402">Représente et fournit des informations à propos d'un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="0f863-402">Represents and provides information about an application domain.</span></span>  
  
 [<span data-ttu-id="0f863-403">ICorPublishAppDomainEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-403">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 <span data-ttu-id="0f863-404">Fournit des méthodes qui parcourent une collection d'objets `ICorPublishAppDomain` qui existent actuellement dans un processus.</span><span class="sxs-lookup"><span data-stu-id="0f863-404">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 [<span data-ttu-id="0f863-405">ICorPublishEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-405">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 <span data-ttu-id="0f863-406">Sert comme base abstraite pour la publication des énumérateurs.</span><span class="sxs-lookup"><span data-stu-id="0f863-406">Serves as the abstract base for publishing enumerators.</span></span>  
  
 [<span data-ttu-id="0f863-407">ICorPublishProcess (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-407">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 <span data-ttu-id="0f863-408">Fournit des méthodes qui permettent d'accéder aux informations sur un processus.</span><span class="sxs-lookup"><span data-stu-id="0f863-408">Provides methods that access information about a process.</span></span>  
  
 [<span data-ttu-id="0f863-409">ICorPublishProcessEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="0f863-409">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 <span data-ttu-id="0f863-410">Fournit des méthodes qui parcourent une collection d'objets `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="0f863-410">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0f863-411">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="0f863-411">Related Sections</span></span>  
 [<span data-ttu-id="0f863-412">Débogage des Coclasses</span><span class="sxs-lookup"><span data-stu-id="0f863-412">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="0f863-413">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="0f863-413">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="0f863-414">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="0f863-414">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="0f863-415">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="0f863-415">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
