---
title: "Fonction Next (référence des API non managées)"
description: "La fonction suivante retireves la propriété suivante dans une énumération."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Next
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Next
helpviewer_keywords: Next function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e59ef3f65b75a91708dc65f7d4e3d811dc2d3f9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="next-function"></a><span data-ttu-id="44b4b-103">Fonction Next</span><span class="sxs-lookup"><span data-stu-id="44b4b-103">Next function</span></span>
<span data-ttu-id="44b4b-104">Récupère la propriété suivante dans une énumération qui commence par un appel à [BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="44b4b-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="44b4b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44b4b-105">Syntax</span></span>  
  
```  
HRESULT Next (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor     
); 
```  

## <a name="parameters"></a><span data-ttu-id="44b4b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="44b4b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="44b4b-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="44b4b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="44b4b-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="44b4b-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="44b4b-109">[in] Réservé.</span><span class="sxs-lookup"><span data-stu-id="44b4b-109">[in] Reserved.</span></span> <span data-ttu-id="44b4b-110">Ce paramètre doit être 0.</span><span class="sxs-lookup"><span data-stu-id="44b4b-110">This parameter must be 0.</span></span>

`pstrName`  
<span data-ttu-id="44b4b-111">[out] Un nouveau `BSTR` qui contient le nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="44b4b-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="44b4b-112">Vous pouvez définir ce paramètre `null` si le nom n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="44b4b-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`  
<span data-ttu-id="44b4b-113">[out] A `VARIANT` renseigné avec la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="44b4b-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="44b4b-114">Vous pouvez définir ce paramètre `null` si la valeur n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="44b4b-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="44b4b-115">Si la fonction retourne un code d’erreur, le `VARIANT` passé à `pVal` non de gauche est modifié.</span><span class="sxs-lookup"><span data-stu-id="44b4b-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span> 

`pvtType`  
<span data-ttu-id="44b4b-116">[out] Un pointeur vers un `CIMTYPE` variable (un `LONG` dans lequel le type de la propriété est placé).</span><span class="sxs-lookup"><span data-stu-id="44b4b-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="44b4b-117">La valeur de cette propriété peut être un `VT_NULL_VARIANT`, auquel cas il est nécessaire de déterminer le type réel de la propriété.</span><span class="sxs-lookup"><span data-stu-id="44b4b-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="44b4b-118">Ce paramètre peut également être `null`.</span><span class="sxs-lookup"><span data-stu-id="44b4b-118">This parameter can also be `null`.</span></span> 

`plFlavor`  
<span data-ttu-id="44b4b-119">[out] `null`, ou une valeur qui reçoit des informations sur l’origine de la propriété.</span><span class="sxs-lookup"><span data-stu-id="44b4b-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="44b4b-120">Consultez la section [Notes] pour les valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="44b4b-120">See the [Remarks] section for possible values.</span></span> 

## <a name="return-value"></a><span data-ttu-id="44b4b-121">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="44b4b-121">Return value</span></span>

<span data-ttu-id="44b4b-122">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="44b4b-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="44b4b-123">Constante</span><span class="sxs-lookup"><span data-stu-id="44b4b-123">Constant</span></span>  |<span data-ttu-id="44b4b-124">Value</span><span class="sxs-lookup"><span data-stu-id="44b4b-124">Value</span></span>  |<span data-ttu-id="44b4b-125">Description</span><span class="sxs-lookup"><span data-stu-id="44b4b-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="44b4b-126">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="44b4b-126">0x80041001</span></span> | <span data-ttu-id="44b4b-127">Il a été un échec général.</span><span class="sxs-lookup"><span data-stu-id="44b4b-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="44b4b-128">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="44b4b-128">0x80041008</span></span> | <span data-ttu-id="44b4b-129">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="44b4b-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="44b4b-130">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="44b4b-130">0x8004101d</span></span> | <span data-ttu-id="44b4b-131">Il n’y avait aucun appel à la [ `BeginEnumeration` ](beginenumeration.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="44b4b-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="44b4b-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="44b4b-132">0x80041006</span></span> | <span data-ttu-id="44b4b-133">Pas assez de mémoire est disponible pour commencer une nouvelle énumération.</span><span class="sxs-lookup"><span data-stu-id="44b4b-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="44b4b-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="44b4b-134">0x80041015</span></span> | <span data-ttu-id="44b4b-135">La procédure distante appeler comprise entre le processus en cours et la gestion de Windows a échoué.</span><span class="sxs-lookup"><span data-stu-id="44b4b-135">The remote procedure call betweeen the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="44b4b-136">0</span><span class="sxs-lookup"><span data-stu-id="44b4b-136">0</span></span> | <span data-ttu-id="44b4b-137">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="44b4b-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="44b4b-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="44b4b-138">0x40005</span></span> | <span data-ttu-id="44b4b-139">Il n’y a aucune autre propriété dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="44b4b-139">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="44b4b-140">Notes</span><span class="sxs-lookup"><span data-stu-id="44b4b-140">Remarks</span></span>

<span data-ttu-id="44b4b-141">Cette fonction encapsule un appel à la [IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="44b4b-141">This function wraps a call to the [IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="44b4b-142">Cette méthode retourne également les propriétés système.</span><span class="sxs-lookup"><span data-stu-id="44b4b-142">This method also returns system properties.</span></span>

<span data-ttu-id="44b4b-143">Si le type sous-jacent de la propriété est un chemin d’accès de l’objet, une date ou heure ou un autre type particulier, le type retourné ne contient pas suffisamment d’informations.</span><span class="sxs-lookup"><span data-stu-id="44b4b-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="44b4b-144">L’appelant doit examiner le `CIMTYPE` pour la propriété spécifiée déterminer si la propriété est une référence d’objet, une date ou heure ou un autre type spécial.</span><span class="sxs-lookup"><span data-stu-id="44b4b-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="44b4b-145">Si `plFlavor` n’est pas `null`, le `LONG` valeur reçoit des informations sur l’origine de la propriété, comme suit :</span><span class="sxs-lookup"><span data-stu-id="44b4b-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="44b4b-146">Constante</span><span class="sxs-lookup"><span data-stu-id="44b4b-146">Constant</span></span>  |<span data-ttu-id="44b4b-147">Value</span><span class="sxs-lookup"><span data-stu-id="44b4b-147">Value</span></span>  |<span data-ttu-id="44b4b-148">Description</span><span class="sxs-lookup"><span data-stu-id="44b4b-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="44b4b-149">0 x 40</span><span class="sxs-lookup"><span data-stu-id="44b4b-149">0x40</span></span> | <span data-ttu-id="44b4b-150">La propriété est une propriété système standard.</span><span class="sxs-lookup"><span data-stu-id="44b4b-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="44b4b-151">0 x 20</span><span class="sxs-lookup"><span data-stu-id="44b4b-151">0x20</span></span> | <span data-ttu-id="44b4b-152">Pour une classe : la propriété est héritée de la classe parente.</span><span class="sxs-lookup"><span data-stu-id="44b4b-152">For a class: The property is inherited from the parent class.</span></span> </br> <span data-ttu-id="44b4b-153">Pour une instance : la propriété, tandis que héritée de la classe parente, n'a pas été modifiée par l’instance.</span><span class="sxs-lookup"><span data-stu-id="44b4b-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="44b4b-154">0</span><span class="sxs-lookup"><span data-stu-id="44b4b-154">0</span></span> | <span data-ttu-id="44b4b-155">Pour une classe : la propriété appartient à la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="44b4b-155">For a class: The property belongs to the derived class.</span></span> </br> <span data-ttu-id="44b4b-156">Pour une instance : cette propriété est modifiée par l’instance ; Autrement dit, une valeur a été fournie, ou un qualificateur a été ajouté ou modifié.</span><span class="sxs-lookup"><span data-stu-id="44b4b-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="44b4b-157">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="44b4b-157">Requirements</span></span>  
 <span data-ttu-id="44b4b-158">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44b4b-158">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44b4b-159">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="44b4b-159">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="44b4b-160">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="44b4b-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b4b-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44b4b-161">See also</span></span>  
[<span data-ttu-id="44b4b-162">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="44b4b-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
