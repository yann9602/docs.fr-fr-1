---
title: "Get, fonction (référence des API non managées)"
description: "La fonction Get récupère la valeur de propriété spécifiée."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Get
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Get
helpviewer_keywords: Get function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75329ee4ee925f4eb74d96d8ce7ef3145eb4a966
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="get-function"></a><span data-ttu-id="99625-103">Get, fonction</span><span class="sxs-lookup"><span data-stu-id="99625-103">Get function</span></span>
<span data-ttu-id="99625-104">Récupère la valeur de propriété spécifiée si elle existe.</span><span class="sxs-lookup"><span data-stu-id="99625-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="99625-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99625-105">Syntax</span></span>  
  
```  
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="99625-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="99625-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="99625-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="99625-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="99625-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="99625-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="99625-109">[in] Le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="99625-109">[in] The name of the property.</span></span>

<span data-ttu-id="99625-110">`lFlags`[in] Réservé.</span><span class="sxs-lookup"><span data-stu-id="99625-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="99625-111">Ce paramètre doit être 0.</span><span class="sxs-lookup"><span data-stu-id="99625-111">This parameter must be 0.</span></span>

<span data-ttu-id="99625-112">`pVal`[out] Si la fonction réussit, contient la valeur de la `wszName` propriété.</span><span class="sxs-lookup"><span data-stu-id="99625-112">`pVal` [out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="99625-113">Le `pval` argument reçoit le type correct et la valeur du qualificateur.</span><span class="sxs-lookup"><span data-stu-id="99625-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

<span data-ttu-id="99625-114">`pvtType`[out] Si la fonction réussit, contient un [constante de type CIM](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) qui indique le type de propriété.</span><span class="sxs-lookup"><span data-stu-id="99625-114">`pvtType` [out] If the function returns successfully, contains a [CIM-type constant](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) that indicates the property type.</span></span> <span data-ttu-id="99625-115">Sa valeur peut également être `null`.</span><span class="sxs-lookup"><span data-stu-id="99625-115">Its value can also be `null`.</span></span> 

<span data-ttu-id="99625-116">`plFlavor`[out] Si la fonction est retournée avec succès, reçoit des informations sur l’origine de la propriété.</span><span class="sxs-lookup"><span data-stu-id="99625-116">`plFlavor` [out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="99625-117">Sa valeur peut être `null`, ou l’une des constantes WBEM_FLAVOR_TYPE suivantes définies dans le *WbemCli.h* fichier d’en-tête :</span><span class="sxs-lookup"><span data-stu-id="99625-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="99625-118">Constante</span><span class="sxs-lookup"><span data-stu-id="99625-118">Constant</span></span>  |<span data-ttu-id="99625-119">Valeur</span><span class="sxs-lookup"><span data-stu-id="99625-119">Value</span></span>  |<span data-ttu-id="99625-120">Description</span><span class="sxs-lookup"><span data-stu-id="99625-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="99625-121">0 x 40</span><span class="sxs-lookup"><span data-stu-id="99625-121">0x40</span></span> | <span data-ttu-id="99625-122">La propriété est une propriété système standard.</span><span class="sxs-lookup"><span data-stu-id="99625-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="99625-123">0 x 20</span><span class="sxs-lookup"><span data-stu-id="99625-123">0x20</span></span> | <span data-ttu-id="99625-124">Pour une classe : la propriété est héritée de la classe parente.</span><span class="sxs-lookup"><span data-stu-id="99625-124">For a class: The property is inherited from the parent class.</span></span> </br> <span data-ttu-id="99625-125">Pour une instance : la propriété, tandis que héritée de la classe parente, n'a pas été modifiée par l’instance.</span><span class="sxs-lookup"><span data-stu-id="99625-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="99625-126">0</span><span class="sxs-lookup"><span data-stu-id="99625-126">0</span></span> | <span data-ttu-id="99625-127">Pour une classe : la propriété appartient à la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="99625-127">For a class: The property belongs to the derived class.</span></span> </br> <span data-ttu-id="99625-128">Pour une instance : cette propriété est modifiée par l’instance ; Autrement dit, une valeur a été fournie, ou un qualificateur a été ajouté ou modifié.</span><span class="sxs-lookup"><span data-stu-id="99625-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="99625-129">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="99625-129">Return value</span></span>

<span data-ttu-id="99625-130">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="99625-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="99625-131">Constante</span><span class="sxs-lookup"><span data-stu-id="99625-131">Constant</span></span>  |<span data-ttu-id="99625-132">Valeur</span><span class="sxs-lookup"><span data-stu-id="99625-132">Value</span></span>  |<span data-ttu-id="99625-133">Description</span><span class="sxs-lookup"><span data-stu-id="99625-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="99625-134">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="99625-134">0x80041001</span></span> | <span data-ttu-id="99625-135">Il a été un échec général.</span><span class="sxs-lookup"><span data-stu-id="99625-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="99625-136">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="99625-136">0x80041008</span></span> | <span data-ttu-id="99625-137">Un ou plusieurs paramètres ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="99625-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="99625-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="99625-138">0x80041002</span></span> | <span data-ttu-id="99625-139">La propriété spécifiée est introuvable.</span><span class="sxs-lookup"><span data-stu-id="99625-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="99625-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="99625-140">0x80041006</span></span> | <span data-ttu-id="99625-141">Pas assez de mémoire est disponible pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="99625-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="99625-142">0</span><span class="sxs-lookup"><span data-stu-id="99625-142">0</span></span> | <span data-ttu-id="99625-143">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="99625-143">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="99625-144">Remarques</span><span class="sxs-lookup"><span data-stu-id="99625-144">Remarks</span></span>

<span data-ttu-id="99625-145">Cette fonction encapsule un appel à la [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="99625-145">This function wraps a call to the [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="99625-146">Le `Get` fonction peut également renvoyer les propriétés système.</span><span class="sxs-lookup"><span data-stu-id="99625-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="99625-147">Le `pVal` argument reçoit le type correct et la valeur pour le qualificateur et le modèle COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) (fonction)</span><span class="sxs-lookup"><span data-stu-id="99625-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) function</span></span>

## <a name="requirements"></a><span data-ttu-id="99625-148">Spécifications</span><span class="sxs-lookup"><span data-stu-id="99625-148">Requirements</span></span>  
 <span data-ttu-id="99625-149">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99625-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99625-150">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="99625-150">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="99625-151">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="99625-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99625-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99625-152">See also</span></span>  
[<span data-ttu-id="99625-153">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="99625-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
