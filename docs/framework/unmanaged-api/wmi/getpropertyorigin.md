---
title: "GetPropertyOrigin (fonction) (référence des API Unmnaged)"
description: "La fonction GetPropertyOrigin détermine la classe dans laquelle une propriété est déclarée."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyOrigin
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyOrigin
helpviewer_keywords: GetPropertyOrigin function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a79bfc62ad776cb2bfab2c143d19761d64358bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="9c1ad-103">GetPropertyOrigin (fonction)</span><span class="sxs-lookup"><span data-stu-id="9c1ad-103">GetPropertyOrigin function</span></span>
<span data-ttu-id="9c1ad-104">Détermine la classe dans laquelle une propriété est déclarée.</span><span class="sxs-lookup"><span data-stu-id="9c1ad-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="9c1ad-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c1ad-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="9c1ad-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9c1ad-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="9c1ad-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="9c1ad-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="9c1ad-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="9c1ad-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="9c1ad-109">[in] Le nom de la propriété de l’objet dont la classe propriétaire est demandée.</span><span class="sxs-lookup"><span data-stu-id="9c1ad-109">[in] The name of the property for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="9c1ad-110">[out] Reçoit le nom de la classe qui possède la propriété.</span><span class="sxs-lookup"><span data-stu-id="9c1ad-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="9c1ad-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9c1ad-111">Return value</span></span>

<span data-ttu-id="9c1ad-112">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="9c1ad-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9c1ad-113">Constante</span><span class="sxs-lookup"><span data-stu-id="9c1ad-113">Constant</span></span>  |<span data-ttu-id="9c1ad-114">Value</span><span class="sxs-lookup"><span data-stu-id="9c1ad-114">Value</span></span>  |<span data-ttu-id="9c1ad-115">Description</span><span class="sxs-lookup"><span data-stu-id="9c1ad-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="9c1ad-116">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="9c1ad-116">0x80041001</span></span> | <span data-ttu-id="9c1ad-117">Il a été un échec général.</span><span class="sxs-lookup"><span data-stu-id="9c1ad-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="9c1ad-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="9c1ad-118">0x80041002</span></span> | <span data-ttu-id="9c1ad-119">La propriété spécifiée est introuvable.</span><span class="sxs-lookup"><span data-stu-id="9c1ad-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9c1ad-120">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="9c1ad-120">0x80041008</span></span> | <span data-ttu-id="9c1ad-121">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="9c1ad-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9c1ad-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9c1ad-122">0x80041006</span></span> | <span data-ttu-id="9c1ad-123">Pas assez de mémoire est disponible pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="9c1ad-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="9c1ad-124">0</span><span class="sxs-lookup"><span data-stu-id="9c1ad-124">0</span></span> | <span data-ttu-id="9c1ad-125">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="9c1ad-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9c1ad-126">Notes</span><span class="sxs-lookup"><span data-stu-id="9c1ad-126">Remarks</span></span>

<span data-ttu-id="9c1ad-127">Cette fonction encapsule un appel à la [IWbemClassObject::GetPropertyOrigin](https://msdn.microsoft.com/library/aa391449(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="9c1ad-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](https://msdn.microsoft.com/library/aa391449(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="9c1ad-128">Car une classe peut hériter des propriétés d’un ou plusieurs classes de base, les développeurs souhaitent souvent de déterminer la propriété dans lequel une méthode donnée est définie.</span><span class="sxs-lookup"><span data-stu-id="9c1ad-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="9c1ad-129">Le `pstrClassName` paramètre ne doit pas pointer vers un valide `BSTR` avant l’appel de la fonction, car il s’agit d’un `out` paramètre ; ce pointeur n’est pas libéré une fois que la fonction retourne.</span><span class="sxs-lookup"><span data-stu-id="9c1ad-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="9c1ad-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9c1ad-130">Requirements</span></span>  
<span data-ttu-id="9c1ad-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c1ad-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c1ad-132">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9c1ad-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9c1ad-133">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9c1ad-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1ad-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c1ad-134">See also</span></span>  
[<span data-ttu-id="9c1ad-135">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="9c1ad-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
