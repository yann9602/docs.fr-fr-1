---
title: "IMetaDataDispenserEx::OpenScopeOnITypeInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e13211a43c42d66fccd88473c8f881b9edd071d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="c6331-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="c6331-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="c6331-103">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="c6331-103">This method is not implemented.</span></span> <span data-ttu-id="c6331-104">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="c6331-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6331-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6331-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6331-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c6331-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="c6331-107">[in] Pointeur vers un [ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680) interface qui fournit les informations de type sur lequel ouvrir la portée.</span><span class="sxs-lookup"><span data-stu-id="c6331-107">[in] Pointer to an [ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="c6331-108">[in] Les indicateurs de mode d’ouverture.</span><span class="sxs-lookup"><span data-stu-id="c6331-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="c6331-109">[in] L’interface souhaitée.</span><span class="sxs-lookup"><span data-stu-id="c6331-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="c6331-110">[out] Pointeur vers un pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="c6331-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6331-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c6331-111">Requirements</span></span>  
 <span data-ttu-id="c6331-112">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6331-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6331-113">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c6331-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6331-114">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6331-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6331-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6331-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6331-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6331-116">See Also</span></span>  
 [<span data-ttu-id="c6331-117">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="c6331-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="c6331-118">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="c6331-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
