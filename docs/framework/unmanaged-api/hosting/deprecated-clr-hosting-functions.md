---
title: "Fonction d'hébergement du CLR déconseillées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9530fecb4f2ca6f59d165e49c282320966fd2fa8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="51fce-102">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="51fce-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="51fce-103">Cette section décrit les fonctions statiques globales non managées qui utilisées par les versions antérieures de l’API d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="51fce-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="51fce-104">À l’exception des fonctions d’infrastructure (`_Cor*` fonctions), qui sont utilisés uniquement par le .NET Framework, ces fonctions ont été déconseillées dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51fce-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="51fce-105">Fonctions d’activation</span><span class="sxs-lookup"><span data-stu-id="51fce-105">Activation functions</span></span>  
 [<span data-ttu-id="51fce-106">ClrCreateManagedInstance (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-106">ClrCreateManagedInstance Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="51fce-107">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-107">Deprecated.</span></span> <span data-ttu-id="51fce-108">Crée une instance du type managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="51fce-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="51fce-109">CoInitializeCor (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-109">CoInitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 <span data-ttu-id="51fce-110">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-110">Obsolete.</span></span> <span data-ttu-id="51fce-111">Pour initialiser le common language runtime (CLR), utilisez [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="51fce-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="51fce-112">CoInitializeEE (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-112">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 <span data-ttu-id="51fce-113">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-113">Deprecated.</span></span> <span data-ttu-id="51fce-114">Garantit que le moteur d’exécution de CLR est chargé dans un processus.</span><span class="sxs-lookup"><span data-stu-id="51fce-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="51fce-115">Utilisez le [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="51fce-115">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="51fce-116">CorBindToCurrentRuntime (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-116">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 <span data-ttu-id="51fce-117">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-117">Deprecated.</span></span> <span data-ttu-id="51fce-118">Charge le common language runtime (CLR) dans un processus à l’aide des informations de version stockées dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="51fce-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="51fce-119">CorBindToRuntime (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-119">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 <span data-ttu-id="51fce-120">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-120">Deprecated.</span></span> <span data-ttu-id="51fce-121">Permet aux hôtes non managés de charger le CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="51fce-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="51fce-122">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="51fce-122">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="51fce-123">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-123">Deprecated.</span></span> <span data-ttu-id="51fce-124">Charge le CLR dans un processus à l’aide des informations de version qui sont lu à partir d’un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="51fce-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="51fce-125">CorBindToRuntimeEx (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-125">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 <span data-ttu-id="51fce-126">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-126">Deprecated.</span></span> <span data-ttu-id="51fce-127">Permet les hôtes non managés de charger le CLR dans un processus et vous permet de définir des indicateurs pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="51fce-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="51fce-128">CorBindToRuntimeHost (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 <span data-ttu-id="51fce-129">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-129">Deprecated.</span></span> <span data-ttu-id="51fce-130">Permet aux hôtes de charger une version spécifiée du CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="51fce-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="51fce-131">GetCORRequiredVersion (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-131">GetCORRequiredVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 <span data-ttu-id="51fce-132">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-132">Deprecated.</span></span> <span data-ttu-id="51fce-133">Obtient le numéro de version CLR requis.</span><span class="sxs-lookup"><span data-stu-id="51fce-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="51fce-134">GetCORSystemDirectory (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-134">GetCORSystemDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 <span data-ttu-id="51fce-135">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-135">Deprecated.</span></span> <span data-ttu-id="51fce-136">Retourne le répertoire d’installation du CLR qui est chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="51fce-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="51fce-137">GetRealProcAddress (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-137">GetRealProcAddress Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 <span data-ttu-id="51fce-138">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-138">Deprecated.</span></span> <span data-ttu-id="51fce-139">Obtient l’adresse de la fonction spécifiée qui est exportée à partir de la dernière version installée du CLR.</span><span class="sxs-lookup"><span data-stu-id="51fce-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="51fce-140">GetRequestedRuntimeInfo (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-140">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="51fce-141">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-141">Deprecated.</span></span> <span data-ttu-id="51fce-142">Obtient les informations de version et au répertoire sur le CLR demandé par une application.</span><span class="sxs-lookup"><span data-stu-id="51fce-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="51fce-143">Fonctions de version CLR</span><span class="sxs-lookup"><span data-stu-id="51fce-143">CLR version functions</span></span>  
 <span data-ttu-id="51fce-144">Les fonctions de cette section retournent de la version CLR ; ils ne pas activent le CLR.</span><span class="sxs-lookup"><span data-stu-id="51fce-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="51fce-145">GetCORVersion (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-145">GetCORVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 <span data-ttu-id="51fce-146">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-146">Deprecated.</span></span> <span data-ttu-id="51fce-147">Retourne le numéro de version du CLR qui s’exécute dans le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="51fce-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="51fce-148">GetFileVersion (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-148">GetFileVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 <span data-ttu-id="51fce-149">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-149">Deprecated.</span></span> <span data-ttu-id="51fce-150">Obtient les informations de version CLR du fichier spécifié, à l’aide de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="51fce-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="51fce-151">GetRequestedRuntimeVersion (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-151">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 <span data-ttu-id="51fce-152">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-152">Deprecated.</span></span> <span data-ttu-id="51fce-153">Obtient le numéro de version du CLR demandé par l’application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="51fce-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="51fce-154">Si cette version n’est pas installée, obtient la version la plus récente qui est installée avant la version demandée.</span><span class="sxs-lookup"><span data-stu-id="51fce-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="51fce-155">GetRequestedRuntimeVersionForCLSID (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="51fce-156">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-156">Deprecated.</span></span> <span data-ttu-id="51fce-157">Obtient les informations de version CLR appropriées pour la classe avec le CLSID spécifié.</span><span class="sxs-lookup"><span data-stu-id="51fce-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="51fce-158">GetVersionFromProcess (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-158">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 <span data-ttu-id="51fce-159">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-159">Deprecated.</span></span> <span data-ttu-id="51fce-160">Obtient le numéro de version du CLR qui est associé au handle de processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="51fce-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="51fce-161">LockClrVersion (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-161">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 <span data-ttu-id="51fce-162">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-162">Deprecated.</span></span> <span data-ttu-id="51fce-163">Permet à l’hôte déterminer quelle version du CLR sera utilisée au sein du processus avant d’initialiser le CLR explicitement.</span><span class="sxs-lookup"><span data-stu-id="51fce-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="51fce-164">Fonctions d’hébergement</span><span class="sxs-lookup"><span data-stu-id="51fce-164">Hosting functions</span></span>  
 [<span data-ttu-id="51fce-165">CallFunctionShim (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-165">CallFunctionShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 <span data-ttu-id="51fce-166">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-166">Deprecated.</span></span> <span data-ttu-id="51fce-167">Effectue un appel à la fonction qui porte le nom spécifié et les paramètres dans la bibliothèque spécifiée.</span><span class="sxs-lookup"><span data-stu-id="51fce-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="51fce-168">CoEEShutDownCOM (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-168">CoEEShutDownCOM Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 <span data-ttu-id="51fce-169">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-169">Deprecated.</span></span> <span data-ttu-id="51fce-170">Décharge un assembly COM du processus.</span><span class="sxs-lookup"><span data-stu-id="51fce-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="51fce-171">CorExitProcess (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-171">CorExitProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 <span data-ttu-id="51fce-172">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-172">Deprecated.</span></span> <span data-ttu-id="51fce-173">Arrête le processus non managé en cours.</span><span class="sxs-lookup"><span data-stu-id="51fce-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="51fce-174">CorLaunchApplication (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-174">CorLaunchApplication Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 <span data-ttu-id="51fce-175">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-175">Deprecated.</span></span> <span data-ttu-id="51fce-176">Démarre l’application sur le chemin d’accès réseau spécifié, à l’aide des manifestes spécifiés et autres données d’application.</span><span class="sxs-lookup"><span data-stu-id="51fce-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="51fce-177">CorMarkThreadInThreadPool (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-177">CorMarkThreadInThreadPool Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="51fce-178">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-178">Deprecated.</span></span> <span data-ttu-id="51fce-179">Marque le thread de pool de threads en cours d’exécution pour l’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="51fce-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="51fce-180">À compter de .NET Framework version 2.0, cette fonction n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="51fce-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="51fce-181">Il n’est pas nécessaire et peut être supprimé de votre code.</span><span class="sxs-lookup"><span data-stu-id="51fce-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="51fce-182">CoUninitializeCor (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-182">CoUninitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 <span data-ttu-id="51fce-183">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-183">Obsolete.</span></span> <span data-ttu-id="51fce-184">Le CLR ne peut pas être déchargé d’un processus.</span><span class="sxs-lookup"><span data-stu-id="51fce-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="51fce-185">CoUninitializeEE (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-185">CoUninitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 <span data-ttu-id="51fce-186">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="51fce-187">CreateDebuggingInterfaceFromVersion (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-187">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="51fce-188">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-188">Deprecated.</span></span> <span data-ttu-id="51fce-189">Crée un [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objet basé sur les informations de version spécifié.</span><span class="sxs-lookup"><span data-stu-id="51fce-189">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="51fce-190">CreateICeeFileGen (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-190">CreateICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 <span data-ttu-id="51fce-191">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-191">Deprecated.</span></span> <span data-ttu-id="51fce-192">Crée un [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objet.</span><span class="sxs-lookup"><span data-stu-id="51fce-192">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="51fce-193">DestroyICeeFileGen (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-193">DestroyICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 <span data-ttu-id="51fce-194">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-194">Deprecated.</span></span> <span data-ttu-id="51fce-195">Détruit un [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objet.</span><span class="sxs-lookup"><span data-stu-id="51fce-195">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="51fce-196">Pointeur de FExecuteInAppDomainCallback (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-196">FExecuteInAppDomainCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="51fce-197">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-197">Deprecated.</span></span> <span data-ttu-id="51fce-198">Pointe vers une fonction que le CLR appelle pour exécuter le code managé.</span><span class="sxs-lookup"><span data-stu-id="51fce-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="51fce-199">Pointeur de FLockClrVersionCallback (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-199">FLockClrVersionCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="51fce-200">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-200">Deprecated.</span></span> <span data-ttu-id="51fce-201">Pointe vers une fonction que le CLR appelle pour notifier l’hôte que l’initialisation a démarré ou s’est terminée.</span><span class="sxs-lookup"><span data-stu-id="51fce-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="51fce-202">GetCLRIdentityManager (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-202">GetCLRIdentityManager Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 <span data-ttu-id="51fce-203">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-203">Deprecated.</span></span> <span data-ttu-id="51fce-204">Obtient un pointeur vers une interface qui permet au CLR de gérer les identités.</span><span class="sxs-lookup"><span data-stu-id="51fce-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="51fce-205">LoadLibraryShim (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-205">LoadLibraryShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 <span data-ttu-id="51fce-206">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-206">Deprecated.</span></span> <span data-ttu-id="51fce-207">Charge une version spécifiée d’une DLL .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51fce-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="51fce-208">LoadStringRC (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-208">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 <span data-ttu-id="51fce-209">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-209">Deprecated.</span></span> <span data-ttu-id="51fce-210">Traduit une valeur HRESULT dans un message d’erreur à l’aide de la culture par défaut du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="51fce-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="51fce-211">LoadStringRCEx (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-211">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 <span data-ttu-id="51fce-212">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-212">Deprecated.</span></span> <span data-ttu-id="51fce-213">Traduit une valeur HRESULT à un message d’erreur approprié pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="51fce-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="51fce-214">Pointeur de fonction LPOVERLAPPED_COMPLETION_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="51fce-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="51fce-215">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-215">Deprecated.</span></span> <span data-ttu-id="51fce-216">Pointe vers une fonction qui avertit l’hôte lorsqu’un chevauchement (autrement dit, asynchrone) e/s sur un périphérique est terminée.</span><span class="sxs-lookup"><span data-stu-id="51fce-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="51fce-217">Pointeur de fonction LPTHREAD_START_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="51fce-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="51fce-218">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-218">Deprecated.</span></span> <span data-ttu-id="51fce-219">Pointe vers une fonction qui avertit l’hôte qu’un thread a commencé à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="51fce-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="51fce-220">RunDll32ShimW (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-220">RunDll32ShimW Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 <span data-ttu-id="51fce-221">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-221">Deprecated.</span></span> <span data-ttu-id="51fce-222">Exécute la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="51fce-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="51fce-223">Pointeur de fonction WAITORTIMERCALLBACK</span><span class="sxs-lookup"><span data-stu-id="51fce-223">WAITORTIMERCALLBACK Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 <span data-ttu-id="51fce-224">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="51fce-224">Deprecated.</span></span> <span data-ttu-id="51fce-225">Pointe vers une fonction qui avertit l’hôte qu’un handle d’attente a été signalé ou a expiré.</span><span class="sxs-lookup"><span data-stu-id="51fce-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="51fce-226">Fonctions d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="51fce-226">Infrastructure functions</span></span>  
 <span data-ttu-id="51fce-227">Les fonctions de cette section sont utilisés par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51fce-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="51fce-228">_CorDllMain (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-228">_CorDllMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 <span data-ttu-id="51fce-229">Initialise le CLR recherche le point d’entrée managé dans l’en-tête CLR de l’assembly DLL et commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="51fce-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="51fce-230">_CorExeMain (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-230">_CorExeMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 <span data-ttu-id="51fce-231">Initialise le CLR recherche le point d’entrée managé dans l’en-tête CLR de l’assembly exécutable et commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="51fce-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="51fce-232">_CorExeMain2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-232">_CorExeMain2 Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 <span data-ttu-id="51fce-233">Exécute le point d’entrée dans le code mappé en mémoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="51fce-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="51fce-234">Cette fonction est appelée par le chargeur du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="51fce-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="51fce-235">_CorImageUnloading (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-235">_CorImageUnloading Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 <span data-ttu-id="51fce-236">Notifie le chargeur lorsque les images de modules managés sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="51fce-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="51fce-237">_CorValidateImage (fonction)</span><span class="sxs-lookup"><span data-stu-id="51fce-237">_CorValidateImage Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 <span data-ttu-id="51fce-238">Valide les images de modules managés et notifie le chargeur du système d’exploitation après avoir été chargés.</span><span class="sxs-lookup"><span data-stu-id="51fce-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51fce-239">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51fce-239">See Also</span></span>  
 [<span data-ttu-id="51fce-240">.NET framework 4 hébergement fonctions statiques globales</span><span class="sxs-lookup"><span data-stu-id="51fce-240">.NET Framework 4 Hosting Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md) 
