---
title: "GetMethodQualifierSet (fonction) (référence des API non managées)"
description: "La fonction GetMethodQualifierSet récupère le jeu de qualificateurs d’une méthode."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodQualifierSet
helpviewer_keywords: GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79a19d3bb40dd4d435bd7cf97eb0b4071020648e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="42de3-103">GetMethodQualifierSet (fonction)</span><span class="sxs-lookup"><span data-stu-id="42de3-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="42de3-104">Récupère le qualificateur défini pour une méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="42de3-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="42de3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42de3-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="42de3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42de3-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="42de3-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="42de3-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="42de3-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="42de3-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="42de3-109">[in] Le nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="42de3-109">[in] The method  name.</span></span> <span data-ttu-id="42de3-110">`wszMethod`doit pointer vers un valide `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="42de3-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="42de3-111">[out] Reçoit le pointeur d’interface qui autorise l’accès pour les qualificateurs de la méthode.</span><span class="sxs-lookup"><span data-stu-id="42de3-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="42de3-112">`ppQualSet` ne peut pas avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="42de3-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="42de3-113">Si une erreur se produit, un nouvel objet n’est pas retourné, et le pointeur est défini pour pointer vers `null`.</span><span class="sxs-lookup"><span data-stu-id="42de3-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="42de3-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="42de3-114">Return value</span></span>

<span data-ttu-id="42de3-115">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="42de3-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="42de3-116">Constante</span><span class="sxs-lookup"><span data-stu-id="42de3-116">Constant</span></span>  |<span data-ttu-id="42de3-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="42de3-117">Value</span></span>  |<span data-ttu-id="42de3-118">Description</span><span class="sxs-lookup"><span data-stu-id="42de3-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="42de3-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="42de3-119">0x80041002</span></span> | <span data-ttu-id="42de3-120">La méthode spécifiée n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="42de3-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="42de3-121">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="42de3-121">0x80041008</span></span> | <span data-ttu-id="42de3-122">Un paramètre est `null`.</span><span class="sxs-lookup"><span data-stu-id="42de3-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="42de3-123">0</span><span class="sxs-lookup"><span data-stu-id="42de3-123">0</span></span> | <span data-ttu-id="42de3-124">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="42de3-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="42de3-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="42de3-125">Remarks</span></span>

<span data-ttu-id="42de3-126">Cette fonction encapsule un appel à la [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="42de3-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="42de3-127">Un appel à cette fonction est prise en charge uniquement si l’objet actuel est une définition de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="42de3-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="42de3-128">Manipulation de la méthode n’est pas disponible pour [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters qui pointent vers les instances CIM.</span><span class="sxs-lookup"><span data-stu-id="42de3-128">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="42de3-129">Étant donné que chaque méthode peut avoir son propre qualificateurs, le [IWbemQualifierSet pointeur](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) permet d’ajouter, modifier ou supprimer ces qualificateurs de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="42de3-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="42de3-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="42de3-130">Requirements</span></span>  
<span data-ttu-id="42de3-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42de3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42de3-132">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="42de3-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="42de3-133">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="42de3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42de3-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42de3-134">See also</span></span>  
[<span data-ttu-id="42de3-135">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="42de3-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
