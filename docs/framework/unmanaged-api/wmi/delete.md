---
title: "Supprimer la fonction (référence des API non managées)"
description: "La fonction Delete supprime la propriété spécifiée et tous ses qualificateurs à partir d’une définition de classe CIM."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Delete
helpviewer_keywords: Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30f5bf651990cafe06811019cf2b3d92f866f646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="delete-function"></a><span data-ttu-id="866b1-103">Supprimer (fonction)</span><span class="sxs-lookup"><span data-stu-id="866b1-103">Delete function</span></span>
<span data-ttu-id="866b1-104">Supprime la propriété spécifiée et tous ses qualificateurs d’une définition de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="866b1-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="866b1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="866b1-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="866b1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="866b1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="866b1-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="866b1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="866b1-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="866b1-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="866b1-109">[in] Le nom de la propriété à supprimer.</span><span class="sxs-lookup"><span data-stu-id="866b1-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="866b1-110">`wszName`doit être un pointeur vers une valide `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="866b1-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="866b1-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="866b1-111">Return value</span></span>

<span data-ttu-id="866b1-112">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="866b1-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="866b1-113">Constante</span><span class="sxs-lookup"><span data-stu-id="866b1-113">Constant</span></span>  |<span data-ttu-id="866b1-114">Value</span><span class="sxs-lookup"><span data-stu-id="866b1-114">Value</span></span>  |<span data-ttu-id="866b1-115">Description</span><span class="sxs-lookup"><span data-stu-id="866b1-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="866b1-116">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="866b1-116">0x80041001</span></span> | <span data-ttu-id="866b1-117">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="866b1-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="866b1-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="866b1-118">0x80041016</span></span> | <span data-ttu-id="866b1-119">La propriété ne peut pas être supprimée.</span><span class="sxs-lookup"><span data-stu-id="866b1-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="866b1-120">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="866b1-120">0x80041008</span></span> | <span data-ttu-id="866b1-121">`wszzName` n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="866b1-121">`wszzName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="866b1-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="866b1-122">0x80041002</span></span> | <span data-ttu-id="866b1-123">La propriété spécifiée n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="866b1-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="866b1-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="866b1-124">0x80041006</span></span> | <span data-ttu-id="866b1-125">Il n’est pas suffisamment de mémoire pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="866b1-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="866b1-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="866b1-126">0x8004101c</span></span> | <span data-ttu-id="866b1-127">La propriété est héritée d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="866b1-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="866b1-128">La propriété est une propriété système.</span><span class="sxs-lookup"><span data-stu-id="866b1-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="866b1-129">0</span><span class="sxs-lookup"><span data-stu-id="866b1-129">0</span></span> | <span data-ttu-id="866b1-130">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="866b1-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="866b1-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="866b1-131">0x80041030</span></span> | <span data-ttu-id="866b1-132">La fonction supprimée d’une valeur par défaut de remplacement pour la classe actuelle.</span><span class="sxs-lookup"><span data-stu-id="866b1-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="866b1-133">La valeur par défaut pour cette propriété dans la classe parente a été reactiviated.</span><span class="sxs-lookup"><span data-stu-id="866b1-133">The default value for this property in the parent class has been reactiviated.</span></span> | 

## <a name="remarks"></a><span data-ttu-id="866b1-134">Notes</span><span class="sxs-lookup"><span data-stu-id="866b1-134">Remarks</span></span>

<span data-ttu-id="866b1-135">Cette fonction encapsule un appel à la [IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="866b1-135">This function wraps a call to the [IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="866b1-136">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="866b1-136">Requirements</span></span>  
 <span data-ttu-id="866b1-137">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="866b1-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="866b1-138">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="866b1-138">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="866b1-139">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="866b1-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="866b1-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="866b1-140">See also</span></span>  
[<span data-ttu-id="866b1-141">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="866b1-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
