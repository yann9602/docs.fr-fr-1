---
title: "ICorDebugAppDomain2::GetArrayOrPointerType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2.GetArrayOrPointerType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c08a56ff7f6bd109c5568a7f992850708a22a4b0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="9f81f-102">ICorDebugAppDomain2::GetArrayOrPointerType, méthode</span><span class="sxs-lookup"><span data-stu-id="9f81f-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="9f81f-103">Obtient un tableau du type spécifié, ou un pointeur ou une référence au type spécifié.</span><span class="sxs-lookup"><span data-stu-id="9f81f-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f81f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f81f-104">Syntax</span></span>  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f81f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9f81f-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="9f81f-106">[in] Valeur de l’énumération CorElementType qui spécifie le type natif sous-jacent (tableau, pointeur ou référence) à créer.</span><span class="sxs-lookup"><span data-stu-id="9f81f-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="9f81f-107">[in] Le rang (autrement dit, le nombre de dimensions) du tableau.</span><span class="sxs-lookup"><span data-stu-id="9f81f-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="9f81f-108">Cette valeur doit être 0 si `elementType` spécifie un pointeur ou type référence.</span><span class="sxs-lookup"><span data-stu-id="9f81f-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="9f81f-109">[in] Un pointeur vers un objet ICorDebugType qui représente le type de tableau, pointeur ou référence à créer.</span><span class="sxs-lookup"><span data-stu-id="9f81f-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="9f81f-110">[out] Un pointeur vers l’adresse d’un `ICorDebugType` type d’objet qui représente le tableau construit, type pointeur ou référence.</span><span class="sxs-lookup"><span data-stu-id="9f81f-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f81f-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="9f81f-111">Remarks</span></span>  
 <span data-ttu-id="9f81f-112">La valeur de *elementType* doit être une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9f81f-112">The value of *elementType* must be one of the following:</span></span>  
  
-   <span data-ttu-id="9f81f-113">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="9f81f-113">ELEMENT_TYPE_PTR</span></span>  
  
-   <span data-ttu-id="9f81f-114">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="9f81f-114">ELEMENT_TYPE_BYREF</span></span>  
  
-   <span data-ttu-id="9f81f-115">ELEMENT_TYPE_ARRAY ou ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="9f81f-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="9f81f-116">Si la valeur de *elementType* est ELEMENT_TYPE_PTR ou ELEMENT_TYPE_BYREF, *nRank* doit être égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="9f81f-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f81f-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9f81f-117">Requirements</span></span>  
 <span data-ttu-id="9f81f-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f81f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f81f-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f81f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f81f-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f81f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f81f-121">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f81f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
