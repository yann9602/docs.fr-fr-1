---
title: "GetCurrentApartmentType (fonction) (référence des API non managées)"
description: "La fonction GetCurrentApartmentType récupère le type de cloisonnement dans lequel l’appelant s’exécute."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetCurrentApartmentType
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetCurrentApartmentType
helpviewer_keywords: GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b250913b55ba59261a666760cc15466b6f9d096e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="d8ab5-103">GetCurrentApartmentType (fonction)</span><span class="sxs-lookup"><span data-stu-id="d8ab5-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="d8ab5-104">Récupère le type de cloisonnement dans lequel l’appelant s’exécute.</span><span class="sxs-lookup"><span data-stu-id="d8ab5-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d8ab5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8ab5-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="d8ab5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8ab5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d8ab5-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="d8ab5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d8ab5-108">[in] Un pointeur vers un [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="d8ab5-108">[in] A pointer to an [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span></span>

`aptType`  
<span data-ttu-id="d8ab5-109">[out] Un pointeur vers un [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) valeur d’énumération qui indique le cloisonnement de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="d8ab5-109">[out] A pointer to an [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="d8ab5-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d8ab5-110">Return value</span></span>


|<span data-ttu-id="d8ab5-111">Constante</span><span class="sxs-lookup"><span data-stu-id="d8ab5-111">Constant</span></span>  |<span data-ttu-id="d8ab5-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="d8ab5-112">Value</span></span>  |<span data-ttu-id="d8ab5-113">Description</span><span class="sxs-lookup"><span data-stu-id="d8ab5-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="d8ab5-114">0</span><span class="sxs-lookup"><span data-stu-id="d8ab5-114">0</span></span> | <span data-ttu-id="d8ab5-115">La fonction s’est terminée correctement.</span><span class="sxs-lookup"><span data-stu-id="d8ab5-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="d8ab5-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="d8ab5-116">0x80000008</span></span> | <span data-ttu-id="d8ab5-117">L’appelant ne s’exécute pas dans un thread cloisonné.</span><span class="sxs-lookup"><span data-stu-id="d8ab5-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d8ab5-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="d8ab5-118">Remarks</span></span>

<span data-ttu-id="d8ab5-119">Cette fonction encapsule un appel à la [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="d8ab5-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8ab5-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d8ab5-120">Requirements</span></span>  
 <span data-ttu-id="d8ab5-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ab5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ab5-122">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d8ab5-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d8ab5-123">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ab5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ab5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8ab5-124">See also</span></span>  
[<span data-ttu-id="d8ab5-125">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="d8ab5-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
