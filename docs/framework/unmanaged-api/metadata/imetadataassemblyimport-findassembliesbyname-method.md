---
title: "IMetaDataAssemblyImport::FindAssembliesByName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindAssembliesByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3b957430e66e4381a9be33ceb687d7aecba53a4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="bb499-102">IMetaDataAssemblyImport::FindAssembliesByName, méthode</span><span class="sxs-lookup"><span data-stu-id="bb499-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="bb499-103">Obtient un tableau d’assemblys avec l’objet `szAssemblyName` paramètre, à l’aide de règles standard employées par le common language runtime (CLR) pour la résolution des références.</span><span class="sxs-lookup"><span data-stu-id="bb499-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb499-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb499-104">Syntax</span></span>  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb499-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bb499-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="bb499-106">[in] Le répertoire racine dans lequel rechercher l’assembly donné.</span><span class="sxs-lookup"><span data-stu-id="bb499-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="bb499-107">Si cette valeur est définie sur `null`, `FindAssembliesByName` recherche uniquement dans le global assembly cache de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bb499-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="bb499-108">[in] Liste des sous-répertoires délimitée par des points-virgules (par exemple, « bin ; bin2 »), sous le répertoire racine, dans laquelle effectuer la recherche de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bb499-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="bb499-109">Ces répertoires sont détectés en plus de celles spécifiées dans la valeur par défaut, les règles de détection.</span><span class="sxs-lookup"><span data-stu-id="bb499-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="bb499-110">[in] Le nom de l’assembly à rechercher.</span><span class="sxs-lookup"><span data-stu-id="bb499-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="bb499-111">Le format de cette chaîne est défini dans la page de référence de classe pour <xref:System.Reflection.AssemblyName>.</span><span class="sxs-lookup"><span data-stu-id="bb499-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="bb499-112">[in] Un tableau de type <<!--zzxref:IUnknown --> `IUnknown`> dans lequel placer le `IMetadataAssemblyImport` des pointeurs d’interface.</span><span class="sxs-lookup"><span data-stu-id="bb499-112">[in] An array of type <<!--zzxref:IUnknown --> `IUnknown`> in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bb499-113">[out] Le nombre maximal de pointeurs d’interface qui peut être placée dans `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="bb499-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="bb499-114">[out] Le nombre de pointeurs d’interface retourné.</span><span class="sxs-lookup"><span data-stu-id="bb499-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="bb499-115">Autrement dit, le nombre de pointeurs d’interface réellement placés dans `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="bb499-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb499-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bb499-116">Return Value</span></span>  
  
|<span data-ttu-id="bb499-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb499-117">HRESULT</span></span>|<span data-ttu-id="bb499-118">Description</span><span class="sxs-lookup"><span data-stu-id="bb499-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bb499-119">`FindAssembliesByName`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="bb499-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bb499-120">Il n’existe aucun assembly.</span><span class="sxs-lookup"><span data-stu-id="bb499-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb499-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="bb499-121">Remarks</span></span>  
 <span data-ttu-id="bb499-122">Un nom d’assembly, le `FindAssembliesByName` méthode trouve l’assembly en suivant les règles standards pour résoudre les références d’assembly.</span><span class="sxs-lookup"><span data-stu-id="bb499-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="bb499-123">(Pour plus d’informations, consultez [méthode de localisation des assemblys par le Runtime](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permet à l’appelant de configurer différents aspects du contexte de résolution assembly, tels qu’application chemin de recherche de base et privées.</span><span class="sxs-lookup"><span data-stu-id="bb499-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="bb499-124">Le `FindAssembliesByName` méthode requiert que le CLR soit initialisé dans le processus pour appeler la logique de résolution d’assembly.</span><span class="sxs-lookup"><span data-stu-id="bb499-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="bb499-125">Par conséquent, vous devez appeler [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (en passant COINITEE_DEFAULT) avant d’appeler `FindAssembliesByName`, puis suivez avec un appel à [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="bb499-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="bb499-126">`FindAssembliesByName`Retourne un [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointeur vers le fichier contenant le manifeste d’assembly pour le nom de l’assembly qui est passé.</span><span class="sxs-lookup"><span data-stu-id="bb499-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="bb499-127">Si le nom de l’assembly donné n’est pas complètement spécifié (par exemple, si elle n’inclut pas de version), plusieurs assemblys peuvent être retournés.</span><span class="sxs-lookup"><span data-stu-id="bb499-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="bb499-128">`FindAssembliesByName`est couramment utilisé par un compilateur qui tente de trouver un assembly référencé au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="bb499-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb499-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bb499-129">Requirements</span></span>  
 <span data-ttu-id="bb499-130">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb499-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb499-131">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bb499-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb499-132">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb499-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb499-133">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb499-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb499-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb499-134">See Also</span></span>  
 [<span data-ttu-id="bb499-135">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="bb499-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="bb499-136">IMetaDataAssemblyImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="bb499-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
