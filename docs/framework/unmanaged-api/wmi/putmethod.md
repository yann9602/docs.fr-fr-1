---
title: "PutMethod (fonction) (référence des API non managées)"
description: "La fonction PutMethod crée une méthode."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutMethod
helpviewer_keywords: PutMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e97ffcf44a738234f67d9736382c46c42e5b61e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="putmethod-function"></a><span data-ttu-id="65ef1-103">PutMethod (fonction)</span><span class="sxs-lookup"><span data-stu-id="65ef1-103">PutMethod function</span></span>
<span data-ttu-id="65ef1-104">Crée une méthode.</span><span class="sxs-lookup"><span data-stu-id="65ef1-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="65ef1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65ef1-105">Syntax</span></span>  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="65ef1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="65ef1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="65ef1-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="65ef1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="65ef1-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="65ef1-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="65ef1-109">[in] Le nom de la méthode à créer.</span><span class="sxs-lookup"><span data-stu-id="65ef1-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="65ef1-110">[in] Réservé.</span><span class="sxs-lookup"><span data-stu-id="65ef1-110">[in] Reserved.</span></span> <span data-ttu-id="65ef1-111">Ce paramètre doit être 0.</span><span class="sxs-lookup"><span data-stu-id="65ef1-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="65ef1-112">[in] Un pointeur vers une copie de la [classe __Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) qui contient le `in` paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="65ef1-112">[in] A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="65ef1-113">Ce paramètre est ignoré si la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="65ef1-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="65ef1-114">[in]  Un pointeur vers une copie de la [classe __Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) qui contient le `out` paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="65ef1-114">[in]  A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="65ef1-115">Ce paramètre est ignoré si la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="65ef1-115">This parameter is ignored if set to `null`.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="65ef1-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="65ef1-116">Return value</span></span>

<span data-ttu-id="65ef1-117">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="65ef1-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="65ef1-118">Constante</span><span class="sxs-lookup"><span data-stu-id="65ef1-118">Constant</span></span>  |<span data-ttu-id="65ef1-119">Value</span><span class="sxs-lookup"><span data-stu-id="65ef1-119">Value</span></span>  |<span data-ttu-id="65ef1-120">Description</span><span class="sxs-lookup"><span data-stu-id="65ef1-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="65ef1-121">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="65ef1-121">0x80041008</span></span> | <span data-ttu-id="65ef1-122">Un ou plusieurs paramètres ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="65ef1-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="65ef1-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="65ef1-123">0x80041043</span></span> | <span data-ttu-id="65ef1-124">Le `[in, out]` paramètre de méthode spécifié à la fois dans le *pInSignature* et *pOutSignature* objets ont des qualificateurs différents.</span><span class="sxs-lookup"><span data-stu-id="65ef1-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="65ef1-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="65ef1-125">0x80041036</span></span> | <span data-ttu-id="65ef1-126">Il manque la spécification d’un paramètre de méthode le **ID** qualificateur.</span><span class="sxs-lookup"><span data-stu-id="65ef1-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="65ef1-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="65ef1-127">0x80041038</span></span> | <span data-ttu-id="65ef1-128">La série d’ID qui est attribuée aux paramètres de méthode n’est pas consécutif ou n’a pas été commencent à 0.</span><span class="sxs-lookup"><span data-stu-id="65ef1-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="65ef1-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="65ef1-129">0x80041039</span></span> | <span data-ttu-id="65ef1-130">La valeur de retour pour une méthode a un **ID** qualificateur.</span><span class="sxs-lookup"><span data-stu-id="65ef1-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="65ef1-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="65ef1-131">0x80041034</span></span> | <span data-ttu-id="65ef1-132">Une tentative a été effectuée pour réutiliser un nom de méthode existant à partir d’une classe parente, et les signatures ne correspondent pas.</span><span class="sxs-lookup"><span data-stu-id="65ef1-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="65ef1-133">0</span><span class="sxs-lookup"><span data-stu-id="65ef1-133">0</span></span> | <span data-ttu-id="65ef1-134">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="65ef1-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="65ef1-135">Notes</span><span class="sxs-lookup"><span data-stu-id="65ef1-135">Remarks</span></span>

<span data-ttu-id="65ef1-136">Cette fonction encapsule un appel à la [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="65ef1-136">This function wraps a call to the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="65ef1-137">Cet appel de méthode n’est possible que si `ptr` est une définition de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="65ef1-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="65ef1-138">Manipulation de la méthode n’est pas disponible à partir de [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) pointeurs qui pointent vers les instances CIM.</span><span class="sxs-lookup"><span data-stu-id="65ef1-138">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) pointers that point to CIM instances.</span></span>

<span data-ttu-id="65ef1-139">Les utilisateurs ne peuvent pas créer des méthodes dont les noms commencent ou finir par un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="65ef1-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="65ef1-140">Cela est réservé pour les propriétés et les classes du système.</span><span class="sxs-lookup"><span data-stu-id="65ef1-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="65ef1-141">Pour une méthode, le `in` et `out` paramètres sont décrits en tant que propriétés dans [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objets.</span><span class="sxs-lookup"><span data-stu-id="65ef1-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objects.</span></span>

<span data-ttu-id="65ef1-142">Un `[in/out]` paramètre peut être défini par l’ajout de la même propriété pour les deux objets pointés par le `pInSignature` et `pOutSignature` paramètres.</span><span class="sxs-lookup"><span data-stu-id="65ef1-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="65ef1-143">Dans ce cas, les propriétés de partagent le même **ID** valeur du qualificateur.</span><span class="sxs-lookup"><span data-stu-id="65ef1-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="65ef1-144">Chaque propriété dans un [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) objet de classe autre que `ReturnValue` doit avoir un **ID** qualificateur, une valeur numérique de base zéro qui identifie l’ordre dans lequel les paramètres apparaissent.</span><span class="sxs-lookup"><span data-stu-id="65ef1-144">Each property in a [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="65ef1-145">Aucun deux paramètres ne peuvent avoir le même **ID** valeur et non **ID** valeur peut être ignorée.</span><span class="sxs-lookup"><span data-stu-id="65ef1-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="65ef1-146">Si des conditions se produit, le `PutMethod` fonction renvoie `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="65ef1-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="65ef1-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="65ef1-147">Example</span></span>

<span data-ttu-id="65ef1-148">Pour obtenir un exemple, consultez la [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="65ef1-148">For an example, see the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="65ef1-149">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="65ef1-149">Requirements</span></span>  
 <span data-ttu-id="65ef1-150">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ef1-150">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ef1-151">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="65ef1-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="65ef1-152">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="65ef1-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ef1-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65ef1-153">See also</span></span>  
[<span data-ttu-id="65ef1-154">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="65ef1-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
