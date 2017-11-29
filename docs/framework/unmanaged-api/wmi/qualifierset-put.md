---
title: "QualifierSet_Put (fonction) (référence des API non managées)"
description: "La fonction QualifierSet_Put écrit qualificateur nommé et sa valeur."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Put
helpviewer_keywords: QualifierSet_Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7fdb6759d4e39ad9ab6bd6da2c2a0e2abfbe5d56
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="1e695-103">QualifierSet_Put (fonction)</span><span class="sxs-lookup"><span data-stu-id="1e695-103">QualifierSet_Put function</span></span>
<span data-ttu-id="1e695-104">Écrit la valeur et le qualificateur nommé.</span><span class="sxs-lookup"><span data-stu-id="1e695-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="1e695-105">Le nouveau qualificateur remplace la valeur précédente du même nom.</span><span class="sxs-lookup"><span data-stu-id="1e695-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="1e695-106">Si le qualificateur n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="1e695-106">If the qualifier does not exist, it is created.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1e695-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e695-107">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="1e695-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1e695-108">Parameters</span></span>

`vFunc`   
<span data-ttu-id="1e695-109">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="1e695-109">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="1e695-110">[in] Un pointeur vers un [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="1e695-110">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="1e695-111">[in] Le nom du qualificateur à écrire.</span><span class="sxs-lookup"><span data-stu-id="1e695-111">[in] The name of the qualifier to write.</span></span>

<span data-ttu-id="1e695-112">`pVal`[in] Un pointeur vers un élément valide `VARIANT` qui contient le qualificateur à écrire.</span><span class="sxs-lookup"><span data-stu-id="1e695-112">`pVal` [in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="1e695-113">Ce paramètre ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="1e695-113">This parameter cannot be `null`.</span></span>

<span data-ttu-id="1e695-114">`lFlavor`[in] Une des constantes suivantes qui définit les versions de qualificateur souhaité pour ce qualificateur.</span><span class="sxs-lookup"><span data-stu-id="1e695-114">`lFlavor` [in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="1e695-115">La valeur par défaut est `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="1e695-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="1e695-116">Constante</span><span class="sxs-lookup"><span data-stu-id="1e695-116">Constant</span></span>  |<span data-ttu-id="1e695-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="1e695-117">Value</span></span>  |<span data-ttu-id="1e695-118">Description</span><span class="sxs-lookup"><span data-stu-id="1e695-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="1e695-119">0</span><span class="sxs-lookup"><span data-stu-id="1e695-119">0</span></span> | <span data-ttu-id="1e695-120">Le qualificateur peut être substitué dans une classe dérivée ou une instance.</span><span class="sxs-lookup"><span data-stu-id="1e695-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="1e695-121">**Il s’agit de la valeur par défaut.**</span><span class="sxs-lookup"><span data-stu-id="1e695-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="1e695-122">1</span><span class="sxs-lookup"><span data-stu-id="1e695-122">1</span></span> | <span data-ttu-id="1e695-123">Le qualificateur est propagé aux instances.</span><span class="sxs-lookup"><span data-stu-id="1e695-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="1e695-124">2</span><span class="sxs-lookup"><span data-stu-id="1e695-124">2</span></span> | <span data-ttu-id="1e695-125">Le qualificateur est propagé aux classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="1e695-125">The qualifier is propagated to derived classes.</span></span> |
| <span data-ttu-id="1e695-126">' WBEM_FLAVOR_NOT_OVERRIDABLE</span><span class="sxs-lookup"><span data-stu-id="1e695-126">\`WBEM_FLAVOR_NOT_OVERRIDABLE</span></span> | <span data-ttu-id="1e695-127">0 x 10</span><span class="sxs-lookup"><span data-stu-id="1e695-127">0x10</span></span> | <span data-ttu-id="1e695-128">Le qualificateur ne peut pas être écrasé dans une classe ou une instance dérivée.</span><span class="sxs-lookup"><span data-stu-id="1e695-128">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| <span data-ttu-id="1e695-129">' WBEM_FLAVOR_AMENDED</span><span class="sxs-lookup"><span data-stu-id="1e695-129">\`WBEM_FLAVOR_AMENDED</span></span> | <span data-ttu-id="1e695-130">0 x 80</span><span class="sxs-lookup"><span data-stu-id="1e695-130">0x80</span></span> | <span data-ttu-id="1e695-131">Le qualificateur est localisé.</span><span class="sxs-lookup"><span data-stu-id="1e695-131">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="1e695-132">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1e695-132">Return value</span></span>

<span data-ttu-id="1e695-133">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="1e695-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1e695-134">Constante</span><span class="sxs-lookup"><span data-stu-id="1e695-134">Constant</span></span>  |<span data-ttu-id="1e695-135">Valeur</span><span class="sxs-lookup"><span data-stu-id="1e695-135">Value</span></span>  |<span data-ttu-id="1e695-136">Description</span><span class="sxs-lookup"><span data-stu-id="1e695-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="1e695-137">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="1e695-137">0x8004101f</span></span> | <span data-ttu-id="1e695-138">Une tentative non conforme pour spécifier le **clé** qualificateur sur une propriété qui ne peut pas être une clé.</span><span class="sxs-lookup"><span data-stu-id="1e695-138">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="1e695-139">Les clés sont spécifiées om c ; définition ass d’un objet et ne peut pas être modifié sur chaque instance.</span><span class="sxs-lookup"><span data-stu-id="1e695-139">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1e695-140">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="1e695-140">0x80041008</span></span> | <span data-ttu-id="1e695-141">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="1e695-141">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="1e695-142">0x80041029</span><span class="sxs-lookup"><span data-stu-id="1e695-142">0x80041029</span></span> | <span data-ttu-id="1e695-143">Le `pVal` paramètre n’est pas un type de qualificateur autorisé.</span><span class="sxs-lookup"><span data-stu-id="1e695-143">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="1e695-144">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="1e695-144">0x8004101a</span></span> | <span data-ttu-id="1e695-145">Il n’est pas possible d’appeler le `QualifierSet_Put` méthode sur le qualificateur, car l’objet propriétaire n’autorise pas les remplacements.</span><span class="sxs-lookup"><span data-stu-id="1e695-145">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="1e695-146">0</span><span class="sxs-lookup"><span data-stu-id="1e695-146">0</span></span> | <span data-ttu-id="1e695-147">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="1e695-147">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1e695-148">Remarques</span><span class="sxs-lookup"><span data-stu-id="1e695-148">Remarks</span></span>

<span data-ttu-id="1e695-149">Cette fonction encapsule un appel à la [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="1e695-149">This function wraps a call to the [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1e695-150">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1e695-150">Requirements</span></span>  
 <span data-ttu-id="1e695-151">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e695-151">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e695-152">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1e695-152">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1e695-153">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1e695-153">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e695-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e695-154">See also</span></span>  
[<span data-ttu-id="1e695-155">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="1e695-155">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
