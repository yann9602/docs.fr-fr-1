---
title: GetRequestedRuntimeVersionForCLSID, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeVersionForCLSID
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeVersionForCLSID
helpviewer_keywords: GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a5b9e4b186b6c9b91c1182e8700268f0e1c038f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="40c31-102">GetRequestedRuntimeVersionForCLSID, fonction</span><span class="sxs-lookup"><span data-stu-id="40c31-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="40c31-103">Obtient les informations de version du common language runtime (CLR) approprié pour la classe avec l’objet `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="40c31-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="40c31-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40c31-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c31-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40c31-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40c31-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="40c31-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="40c31-107">[in]  Le `CLSID` du composant.</span><span class="sxs-lookup"><span data-stu-id="40c31-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="40c31-108">[out]  Une mémoire tampon qui contient la chaîne de numéro de version en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="40c31-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="40c31-109">[in]  La taille, en caractères larges, de la `pVersion` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="40c31-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="40c31-110">[out] La longueur, en octets, de la mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="40c31-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="40c31-111">[in]  Une des valeurs CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="40c31-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="40c31-112">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="40c31-112">The following values are supported:</span></span>  
  
-   <span data-ttu-id="40c31-113">CLSID_RESOLUTION_DEFAULT : (0 x 0) spécifie ce comportement d’interopérabilité par défaut doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="40c31-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
-   <span data-ttu-id="40c31-114">CLSID_RESOLUTION_REGISTERED : (0 x 1) Spécifie que le Registre doivent être recherchées et stratégie shim doit être appliquée.</span><span class="sxs-lookup"><span data-stu-id="40c31-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40c31-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="40c31-115">Return Value</span></span>  
  
|<span data-ttu-id="40c31-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40c31-116">HRESULT</span></span>|<span data-ttu-id="40c31-117">Description</span><span class="sxs-lookup"><span data-stu-id="40c31-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40c31-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="40c31-118">S_OK</span></span>|<span data-ttu-id="40c31-119">La fonction a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="40c31-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="40c31-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="40c31-120">E_INVALIDARG</span></span>|<span data-ttu-id="40c31-121">Un des paramètres a un format ou un type non valide.</span><span class="sxs-lookup"><span data-stu-id="40c31-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="40c31-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="40c31-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="40c31-123">Le `pVersion` mémoire tampon n’est pas assez grand pour contenir la chaîne de version entière.</span><span class="sxs-lookup"><span data-stu-id="40c31-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="40c31-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="40c31-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="40c31-125">Aucune classe n’est enregistrée avec l’objet `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="40c31-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="40c31-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="40c31-126">E_POINTER</span></span>|<span data-ttu-id="40c31-127">`dwLength`a la valeur null ou `cchBuffer` est suffisamment grande pour contenir la chaîne de version, mais `pVersion` est null.</span><span class="sxs-lookup"><span data-stu-id="40c31-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40c31-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="40c31-128">Requirements</span></span>  
 <span data-ttu-id="40c31-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40c31-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40c31-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="40c31-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40c31-131">**Versions du .NET framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40c31-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c31-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40c31-132">See Also</span></span>  
 [<span data-ttu-id="40c31-133">Fonctions d’hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="40c31-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
