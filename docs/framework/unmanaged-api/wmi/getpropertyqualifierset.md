---
title: "GetPropertyQualifierSet (fonction) (référence des API non managées)"
description: "La fonction GetPropertyQualifierSet récupère le qualificateur d’une propriété."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyQualifierSet
helpviewer_keywords: GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ca2981c8833abaafd5d206b66d6e91f34e2c91d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="f019a-103">GetPropertyQualifierSet (fonction)</span><span class="sxs-lookup"><span data-stu-id="f019a-103">GetPropertyQualifierSet function</span></span>
<span data-ttu-id="f019a-104">Récupère le qualificateur définie pour une propriété particulière.</span><span class="sxs-lookup"><span data-stu-id="f019a-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f019a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f019a-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="f019a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f019a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f019a-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="f019a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f019a-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="f019a-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="f019a-109">[in] Le nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="f019a-109">[in] The property  name.</span></span> <span data-ttu-id="f019a-110">`wszProperty`doit pointer vers un valide `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="f019a-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="f019a-111">[out] Reçoit le pointeur d’interface qui autorise l’accès pour les qualificateurs de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f019a-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="f019a-112">`ppQualSet` ne peut pas avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="f019a-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="f019a-113">Si une erreur se produit, un nouvel objet n’est pas retourné, et le pointeur est défini pour pointer vers `null`.</span><span class="sxs-lookup"><span data-stu-id="f019a-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="f019a-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f019a-114">Return value</span></span>

<span data-ttu-id="f019a-115">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="f019a-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f019a-116">Constante</span><span class="sxs-lookup"><span data-stu-id="f019a-116">Constant</span></span>  |<span data-ttu-id="f019a-117">Value</span><span class="sxs-lookup"><span data-stu-id="f019a-117">Value</span></span>  |<span data-ttu-id="f019a-118">Description</span><span class="sxs-lookup"><span data-stu-id="f019a-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="f019a-119">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="f019a-119">0x80041001</span></span> | <span data-ttu-id="f019a-120">Il a été un échec général.</span><span class="sxs-lookup"><span data-stu-id="f019a-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="f019a-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f019a-121">0x80041002</span></span> | <span data-ttu-id="f019a-122">La méthode spécifiée n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="f019a-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f019a-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f019a-123">0x80041006</span></span> | <span data-ttu-id="f019a-124">Pas assez de mémoire est disponible pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="f019a-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f019a-125">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="f019a-125">0x80041008</span></span> | <span data-ttu-id="f019a-126">Un paramètre est `null`.</span><span class="sxs-lookup"><span data-stu-id="f019a-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="f019a-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="f019a-127">0x80041030</span></span> | <span data-ttu-id="f019a-128">La fonction tente d’obtenir des qualificateurs d’une propriété système.</span><span class="sxs-lookup"><span data-stu-id="f019a-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f019a-129">0</span><span class="sxs-lookup"><span data-stu-id="f019a-129">0</span></span> | <span data-ttu-id="f019a-130">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="f019a-130">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f019a-131">Notes</span><span class="sxs-lookup"><span data-stu-id="f019a-131">Remarks</span></span>

<span data-ttu-id="f019a-132">Cette fonction encapsule un appel à la [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="f019a-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="f019a-133">Un appel à cette fonction est prise en charge uniquement si l’objet actuel est une définition de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="f019a-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="f019a-134">Manipulation de la méthode n’est pas disponible pour [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters qui pointent vers les instances CIM.</span><span class="sxs-lookup"><span data-stu-id="f019a-134">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="f019a-135">Étant donné que chaque méthode peut avoir son propre qualificateurs, le [IWbemQualifierSet pointeur](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) permet d’ajouter, modifier ou supprimer ces qualificateurs de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="f019a-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="f019a-136">Dans la mesure où les propriétés système n’ont des qualificateurs d’aucun, la fonction retourne `WBEM_E_SYSTEM_PROPERTY` si vous tentez d’obtenir un [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) pointeur pour une propriété système.</span><span class="sxs-lookup"><span data-stu-id="f019a-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="f019a-137">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f019a-137">Requirements</span></span>  
<span data-ttu-id="f019a-138">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f019a-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f019a-139">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f019a-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f019a-140">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f019a-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f019a-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f019a-141">See also</span></span>  
[<span data-ttu-id="f019a-142">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="f019a-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
