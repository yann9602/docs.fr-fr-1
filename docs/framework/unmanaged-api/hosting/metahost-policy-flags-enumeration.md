---
title: "METAHOST_POLICY_FLAGS, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: METAHOST_POLICY_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: METAHOST_POLICY_FLAGS
helpviewer_keywords: METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80abed08cc7659d4218dce445be81481bb5a665b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="metahostpolicyflags-enumeration"></a><span data-ttu-id="408ba-102">METAHOST_POLICY_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="408ba-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="408ba-103">Fournit des stratégies de liaison qui sont communes à la plupart des hôtes de runtime.</span><span class="sxs-lookup"><span data-stu-id="408ba-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="408ba-104">Cette énumération est utilisée par le [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="408ba-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="408ba-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="408ba-105">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="408ba-106">Membres</span><span class="sxs-lookup"><span data-stu-id="408ba-106">Members</span></span>  
  
|<span data-ttu-id="408ba-107">Membre</span><span class="sxs-lookup"><span data-stu-id="408ba-107">Member</span></span>|<span data-ttu-id="408ba-108">Description</span><span class="sxs-lookup"><span data-stu-id="408ba-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="408ba-109">Définit la stratégie haute compatibilité qui ne tient pas compte un common language runtime (CLR) qui est chargé dans le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="408ba-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="408ba-110">Au lieu de cela, il ne considère que les CLR installés et les préférences du composant, dérivé le fichier d’assembly, la version de génération déclarée ou le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="408ba-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="408ba-111">Applique la stratégie de mise à niveau pour le résultat de la liaison version lorsqu’une correspondance exacte est introuvable, en fonction du contenu de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="408ba-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="408ba-112">Cela a le même effet que [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="408ba-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="408ba-113">Liaison de résultats sont retournés comme si l’image fournie à l’appel a été lancée dans un nouveau processus.</span><span class="sxs-lookup"><span data-stu-id="408ba-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="408ba-114">Actuellement, `GetRequestedRuntime` ignore le jeu de runtime chargeables et lie au jeu de runtime installés.</span><span class="sxs-lookup"><span data-stu-id="408ba-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="408ba-115">Cet indicateur permet à un hôte déterminer à quelle exécution un EXE sera lié lorsqu’elle est lancée.</span><span class="sxs-lookup"><span data-stu-id="408ba-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="408ba-116">Une boîte de dialogue d’erreur s’affiche si `GetRequestedRuntime` ne peut pas trouver un runtime qui est compatible avec les paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="408ba-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="408ba-117">Compter les [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], cette boîte de dialogue d’erreur peut prendre la forme d’une boîte de dialogue fonctionnalités Windows qui vous demande si l’utilisateur souhaite activer la fonctionnalité appropriée.</span><span class="sxs-lookup"><span data-stu-id="408ba-117">Beginning with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="408ba-118">`GetRequestedRuntime`utilise l’image de processus (et tout fichier de configuration correspondant) comme entrée supplémentaire au processus de liaison.</span><span class="sxs-lookup"><span data-stu-id="408ba-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="408ba-119">Par défaut, `GetRequestedRuntime` ne tombe pas dans le chemin d’image de processus (en général, l’EXE qui a été utilisé pour lancer le processus) lors de la détermination du runtime à lier.</span><span class="sxs-lookup"><span data-stu-id="408ba-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="408ba-120">`GetRequestedRuntime`doit vérifier si la référence appropriée est installée lorsque aucune information n’est disponible dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="408ba-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="408ba-121">Cela permet aux applications qui n’ont pas de fichiers de configuration d’échouer correctement sur des références plus petites que l’installation par défaut du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="408ba-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="408ba-122">Par défaut, `GetRequestedRuntime` ne vérifie pas si la référence appropriée est installée, sauf si l’attribut de référence (SKU) est spécifié dans le fichier de configuration `<supportedRuntime />` élément.</span><span class="sxs-lookup"><span data-stu-id="408ba-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="408ba-123">`GetRequestedRuntime`doit vérifier si la référence appropriée est installée lorsque aucune information n’est disponible dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="408ba-123">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="408ba-124">Cela permet aux applications qui n’ont pas de fichiers de configuration d’échouer correctement sur des références plus petites que l’installation par défaut du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="408ba-124">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="408ba-125">Par défaut, `GetRequestedRuntime` ne vérifie pas si la référence appropriée est installée, sauf si l’attribut de référence (SKU) est spécifié dans le fichier de configuration `<supportedRuntime />` élément.</span><span class="sxs-lookup"><span data-stu-id="408ba-125">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="408ba-126">`GetRequestedRuntime`doit ignorer SEM_FAILCRITICALERRORS (qui est défini en appelant le [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) fonction) et afficher la boîte de dialogue d’erreur.</span><span class="sxs-lookup"><span data-stu-id="408ba-126">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="408ba-127">Par défaut, SEM_FAILCRITICALERRORS supprime la boîte de dialogue d’erreur.</span><span class="sxs-lookup"><span data-stu-id="408ba-127">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="408ba-128">Il peut avoir hérité à partir d’un autre processus et l’erreur en mode silencieux est peut-être pas souhaitable dans votre scénario.</span><span class="sxs-lookup"><span data-stu-id="408ba-128">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="408ba-129">Notes</span><span class="sxs-lookup"><span data-stu-id="408ba-129">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="408ba-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="408ba-130">Requirements</span></span>  
 <span data-ttu-id="408ba-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="408ba-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="408ba-132">**En-tête :** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="408ba-132">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="408ba-133">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="408ba-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="408ba-134">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="408ba-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="408ba-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="408ba-135">See Also</span></span>  
 [<span data-ttu-id="408ba-136">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="408ba-136">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="408ba-137">GetRequestedRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="408ba-137">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
