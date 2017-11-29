---
title: "Clone (fonction) (référence des API non managées)"
description: "La fonction de clonage retourne un nouvel objet qui est un clone complet de l’objet actuel."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Clone
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Clone
helpviewer_keywords: Clone function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df6a089f66ddd6f8f9a2d5677dd8dd6917fcb719
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="clone-function"></a><span data-ttu-id="a63a8-103">Clone, fonction</span><span class="sxs-lookup"><span data-stu-id="a63a8-103">Clone function</span></span>
<span data-ttu-id="a63a8-104">Retourne un nouvel objet qui est un clone complet de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="a63a8-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a63a8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a63a8-105">Syntax</span></span>  
  
```  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="a63a8-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a63a8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a63a8-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="a63a8-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a63a8-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="a63a8-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`ppCopy`  
<span data-ttu-id="a63a8-109">[out] Un nouvel objet qui est complète isolés de `ptr`.</span><span class="sxs-lookup"><span data-stu-id="a63a8-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="a63a8-110">Cet argument ne peut pas être `null` s’il reçoit la copie de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="a63a8-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="a63a8-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a63a8-111">Return value</span></span>

<span data-ttu-id="a63a8-112">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="a63a8-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a63a8-113">Constante</span><span class="sxs-lookup"><span data-stu-id="a63a8-113">Constant</span></span>  |<span data-ttu-id="a63a8-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="a63a8-114">Value</span></span>  |<span data-ttu-id="a63a8-115">Description</span><span class="sxs-lookup"><span data-stu-id="a63a8-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="a63a8-116">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="a63a8-116">0x80041001</span></span> | <span data-ttu-id="a63a8-117">Il a été un échec général.</span><span class="sxs-lookup"><span data-stu-id="a63a8-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a63a8-118">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="a63a8-118">0x80041008</span></span> | <span data-ttu-id="a63a8-119">`null`a été spécifié en tant que paramètre, et n’est pas autorisé dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="a63a8-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a63a8-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a63a8-120">0x80041006</span></span> | <span data-ttu-id="a63a8-121">Pas assez de mémoire est disponible pour cloner l’objet.</span><span class="sxs-lookup"><span data-stu-id="a63a8-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="a63a8-122">0</span><span class="sxs-lookup"><span data-stu-id="a63a8-122">0</span></span> | <span data-ttu-id="a63a8-123">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="a63a8-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a63a8-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="a63a8-124">Remarks</span></span>

<span data-ttu-id="a63a8-125">Cette fonction encapsule un appel à la [IWbemClassObject::Clone](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="a63a8-125">This function wraps a call to the [IWbemClassObject::Clone](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="a63a8-126">L’objet cloné est un objet COM qui a un nombre de référence de 1.</span><span class="sxs-lookup"><span data-stu-id="a63a8-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="a63a8-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a63a8-127">Requirements</span></span>  
 <span data-ttu-id="a63a8-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a63a8-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a63a8-129">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a63a8-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a63a8-130">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a63a8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63a8-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a63a8-131">See also</span></span>  
[<span data-ttu-id="a63a8-132">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="a63a8-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
