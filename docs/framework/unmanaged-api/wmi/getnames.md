---
title: "GetNames (fonction) (référence des API non managées)"
description: "La fonction GetNames récupère les noms des propriétés d’un objet."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetNames
helpviewer_keywords: GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2ba2530dd43e6924187c80214d5efa13ebc548de
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="getnames-function"></a><span data-ttu-id="d0723-103">GetNames (fonction)</span><span class="sxs-lookup"><span data-stu-id="d0723-103">GetNames function</span></span>
<span data-ttu-id="d0723-104">Récupère un sous-ensemble ou tous les noms des propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="d0723-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="d0723-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0723-105">Syntax</span></span>  
  
```  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="d0723-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d0723-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d0723-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="d0723-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d0723-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="d0723-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="d0723-109">[in] Un pointeur vers un élément valide `LPCWSTR` qui spécifie un nom du qualificateur qui fonctionne en tant que partie d’un filtre.</span><span class="sxs-lookup"><span data-stu-id="d0723-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="d0723-110">Pour plus d’informations, consultez la [notes](#remarks) section.</span><span class="sxs-lookup"><span data-stu-id="d0723-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="d0723-111">Ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="d0723-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="d0723-112">[in] Une combinaison des champs de bits.</span><span class="sxs-lookup"><span data-stu-id="d0723-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="d0723-113">Pour plus d’informations, consultez la [notes](#remarks) section.</span><span class="sxs-lookup"><span data-stu-id="d0723-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="d0723-114">[in] Un pointeur vers un élément valide `VARIANT` structure initialisé à une valeur de filtre.</span><span class="sxs-lookup"><span data-stu-id="d0723-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="d0723-115">Ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="d0723-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="d0723-116">[out] A `SAFEARRAY` structure qui contient les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="d0723-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="d0723-117">À l’entrée, ce paramètre doit toujours être un pointeur vers `null`.</span><span class="sxs-lookup"><span data-stu-id="d0723-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="d0723-118">Consultez le [notes](#remarks) section pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="d0723-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="d0723-119">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d0723-119">Return value</span></span>

<span data-ttu-id="d0723-120">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="d0723-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d0723-121">Constante</span><span class="sxs-lookup"><span data-stu-id="d0723-121">Constant</span></span>  |<span data-ttu-id="d0723-122">Valeur</span><span class="sxs-lookup"><span data-stu-id="d0723-122">Value</span></span>  |<span data-ttu-id="d0723-123">Description</span><span class="sxs-lookup"><span data-stu-id="d0723-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="d0723-124">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="d0723-124">0x80041001</span></span> | <span data-ttu-id="d0723-125">Il a été un échec général.</span><span class="sxs-lookup"><span data-stu-id="d0723-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d0723-126">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="d0723-126">0x80041008</span></span> | <span data-ttu-id="d0723-127">Un ou plusieurs paramètres ne sont pas valides, ou une combinaison incorrecte d’indicateurs et de paramètres a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d0723-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d0723-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d0723-128">0x80041006</span></span> | <span data-ttu-id="d0723-129">Pas assez de mémoire est disponible pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="d0723-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d0723-130">0</span><span class="sxs-lookup"><span data-stu-id="d0723-130">0</span></span> | <span data-ttu-id="d0723-131">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="d0723-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d0723-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="d0723-132">Remarks</span></span>

<span data-ttu-id="d0723-133">Cette fonction encapsule un appel à la [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="d0723-133">This function wraps a call to the [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="d0723-134">Nommé retourné est contrôlé par une combinaison d’indicateurs et de paramètres.</span><span class="sxs-lookup"><span data-stu-id="d0723-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="d0723-135">Par exemple, la fonction peut retourner les noms de toutes les propriétés ou uniquement les noms des propriétés de clé.</span><span class="sxs-lookup"><span data-stu-id="d0723-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="d0723-136">Le filtre principal est spécifié dans le `lFlags` paramètre et les autres paramètres varient selon qu’il.</span><span class="sxs-lookup"><span data-stu-id="d0723-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="d0723-137">Valeurs de l’indicateur de `lFlags` sont des champs de bits</span><span class="sxs-lookup"><span data-stu-id="d0723-137">The flag values in `lFlags` are bit fields</span></span>


<span data-ttu-id="d0723-138">Les indicateurs qui peuvent être passés en tant que le `lEnumFlags` argument sont des champs de bits sont définis dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="d0723-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="d0723-139">Vous pouvez combiner un indicateur de chaque groupe de tout indicateur de tout autre groupe.</span><span class="sxs-lookup"><span data-stu-id="d0723-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="d0723-140">Toutefois, les indicateurs à partir du même groupe sont mutuellement exclusifs.</span><span class="sxs-lookup"><span data-stu-id="d0723-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="d0723-141">Indicateurs de groupe 1</span><span class="sxs-lookup"><span data-stu-id="d0723-141">Group 1 flags</span></span> |<span data-ttu-id="d0723-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="d0723-142">Value</span></span>  |<span data-ttu-id="d0723-143">Description</span><span class="sxs-lookup"><span data-stu-id="d0723-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="d0723-144">0</span><span class="sxs-lookup"><span data-stu-id="d0723-144">0</span></span> | <span data-ttu-id="d0723-145">Retourner tous les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="d0723-145">Return all property names.</span></span> <span data-ttu-id="d0723-146">`strQualifierName`et `pQualifierVal` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="d0723-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="d0723-147">1</span><span class="sxs-lookup"><span data-stu-id="d0723-147">1</span></span> | <span data-ttu-id="d0723-148">Retourner uniquement les propriétés qui ont un qualificateur du nom spécifié par le `strQualifierName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="d0723-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="d0723-149">Si cet indicateur est utilisé, vous devez spécifier `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="d0723-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="d0723-150">2</span><span class="sxs-lookup"><span data-stu-id="d0723-150">2</span></span> |  <span data-ttu-id="d0723-151">Retourner uniquement des propriétés qui n’ont pas d’un qualificateur du nom spécifié par le `strQualifierName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="d0723-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="d0723-152">Si cet indicateur est utilisé, vous devez spécifier `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="d0723-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="d0723-153">3</span><span class="sxs-lookup"><span data-stu-id="d0723-153">3</span></span> | <span data-ttu-id="d0723-154">Retourne uniquement les propriétés qui ont un qualificateur du nom spécifié par le `wszQualifierName` paramètre et également avoir une valeur identique à celle spécifiée par la `pQualifierVal` structure.</span><span class="sxs-lookup"><span data-stu-id="d0723-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="d0723-155">Si cet indicateur est utilisé, vous devez spécifier à la fois un `wszQualifierName` et un `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="d0723-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="d0723-156">Indicateurs de groupe 2</span><span class="sxs-lookup"><span data-stu-id="d0723-156">Group 2 flags</span></span> |<span data-ttu-id="d0723-157">Valeur</span><span class="sxs-lookup"><span data-stu-id="d0723-157">Value</span></span>  |<span data-ttu-id="d0723-158">Description</span><span class="sxs-lookup"><span data-stu-id="d0723-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="d0723-159">0 x 4</span><span class="sxs-lookup"><span data-stu-id="d0723-159">0x4</span></span> | <span data-ttu-id="d0723-160">Retourner uniquement les noms des propriétés qui définissent les clés.</span><span class="sxs-lookup"><span data-stu-id="d0723-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="d0723-161">0 x 8</span><span class="sxs-lookup"><span data-stu-id="d0723-161">0x8</span></span> | <span data-ttu-id="d0723-162">Retour uniquement noms de propriétés qui sont des références d’objet.</span><span class="sxs-lookup"><span data-stu-id="d0723-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="d0723-163">Indicateurs de groupe 3</span><span class="sxs-lookup"><span data-stu-id="d0723-163">Group 3 flags</span></span> |<span data-ttu-id="d0723-164">Valeur</span><span class="sxs-lookup"><span data-stu-id="d0723-164">Value</span></span>  |<span data-ttu-id="d0723-165">Description</span><span class="sxs-lookup"><span data-stu-id="d0723-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="d0723-166">0 x 10</span><span class="sxs-lookup"><span data-stu-id="d0723-166">0x10</span></span> | <span data-ttu-id="d0723-167">Retourner uniquement les noms de propriété qui appartiennent à la classe la plus dérivée.</span><span class="sxs-lookup"><span data-stu-id="d0723-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="d0723-168">Exclure les propriétés des classes parentes.</span><span class="sxs-lookup"><span data-stu-id="d0723-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="d0723-169">0 x 20</span><span class="sxs-lookup"><span data-stu-id="d0723-169">0x20</span></span> | <span data-ttu-id="d0723-170">Retourner uniquement les noms de propriété qui appartiennent à des classes parentes.</span><span class="sxs-lookup"><span data-stu-id="d0723-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="d0723-171">0 x 30</span><span class="sxs-lookup"><span data-stu-id="d0723-171">0x30</span></span> | <span data-ttu-id="d0723-172">Retourner uniquement les noms des propriétés système.</span><span class="sxs-lookup"><span data-stu-id="d0723-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="d0723-173">0 x 40</span><span class="sxs-lookup"><span data-stu-id="d0723-173">0x40</span></span> | <span data-ttu-id="d0723-174">Retourner uniquement les noms des propriétés de non système.</span><span class="sxs-lookup"><span data-stu-id="d0723-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="d0723-175">La fonction alloue une nouvelle toujours `SAFEARRAY` si elle retourne `WBEM_S_NO_ERROR`, et `pstrNames` est toujours défini à pointer sur elle.</span><span class="sxs-lookup"><span data-stu-id="d0723-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="d0723-176">Le tableau retourné peut avoir des éléments, 0 si aucune propriété correspondent aux filtres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d0723-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="d0723-177">Si la fonction retourne une valeur autre que `WBM_S_NO_ERROR`, un nouveau `SAFEARRAY` structure n’est pas retournée.</span><span class="sxs-lookup"><span data-stu-id="d0723-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="d0723-178">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d0723-178">Requirements</span></span>  
 <span data-ttu-id="d0723-179">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0723-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0723-180">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d0723-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d0723-181">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d0723-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0723-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0723-182">See also</span></span>  
[<span data-ttu-id="d0723-183">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="d0723-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
