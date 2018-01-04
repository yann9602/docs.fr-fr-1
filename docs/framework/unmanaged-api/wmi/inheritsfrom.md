---
title: "InheritsFrom (fonction) (référence des API non managées)"
description: "La fonction InheritsFrom détermine si une classe ou une instance dérivée d’une classe parente particulier."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: InheritsFrom
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: InheritsFrom
helpviewer_keywords: InheritsFrom function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dce964829399e6761152a8ff424671b47cc6eb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="581bf-103">InheritsFrom (fonction)</span><span class="sxs-lookup"><span data-stu-id="581bf-103">InheritsFrom function</span></span>
<span data-ttu-id="581bf-104">Détermine si l’instance ou la classe actuelle dérive d’une classe parente spécifiée.</span><span class="sxs-lookup"><span data-stu-id="581bf-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="581bf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="581bf-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="581bf-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="581bf-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="581bf-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="581bf-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="581bf-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="581bf-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="581bf-109">[in] Le nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="581bf-109">[in] The name of the class.</span></span> <span data-ttu-id="581bf-110">`wszAncestor`doit pointer vers un valide `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="581bf-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="581bf-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="581bf-111">Return value</span></span>

<span data-ttu-id="581bf-112">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="581bf-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="581bf-113">Constante</span><span class="sxs-lookup"><span data-stu-id="581bf-113">Constant</span></span>  |<span data-ttu-id="581bf-114">Value</span><span class="sxs-lookup"><span data-stu-id="581bf-114">Value</span></span>  |<span data-ttu-id="581bf-115">Description</span><span class="sxs-lookup"><span data-stu-id="581bf-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="581bf-116">0</span><span class="sxs-lookup"><span data-stu-id="581bf-116">0</span></span> | <span data-ttu-id="581bf-117">L’objet actuel hérite `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="581bf-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="581bf-118">1</span><span class="sxs-lookup"><span data-stu-id="581bf-118">1</span></span> | <span data-ttu-id="581bf-119">L’objet actuel n’hérite pas de `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="581bf-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="581bf-120">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="581bf-120">0x80041008</span></span> | <span data-ttu-id="581bf-121">`wszAncestor` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="581bf-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="581bf-122">Notes</span><span class="sxs-lookup"><span data-stu-id="581bf-122">Remarks</span></span>

<span data-ttu-id="581bf-123">Cette fonction encapsule un appel à la [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="581bf-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="581bf-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="581bf-124">Requirements</span></span>  
 <span data-ttu-id="581bf-125">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="581bf-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="581bf-126">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="581bf-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="581bf-127">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="581bf-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="581bf-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="581bf-128">See also</span></span>  
[<span data-ttu-id="581bf-129">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="581bf-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
