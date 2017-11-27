---
title: "NextMethod (fonction) (référence des API non managées)"
description: "La fonction NextMethod extrait la méthode suivante dans une énumération."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: NextMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: NextMethod
helpviewer_keywords: NextMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9b14424bb914be3ba127670e1b6490f79854d6e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="nextmethod-function"></a><span data-ttu-id="091ad-103">NextMethod (fonction)</span><span class="sxs-lookup"><span data-stu-id="091ad-103">NextMethod function</span></span>
<span data-ttu-id="091ad-104">Récupère la méthode suivante dans une énumération qui commence par un appel à [BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="091ad-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="091ad-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="091ad-105">Syntax</span></span>  
  
```  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a><span data-ttu-id="091ad-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="091ad-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="091ad-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="091ad-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="091ad-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="091ad-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="091ad-109">[in] Réservé.</span><span class="sxs-lookup"><span data-stu-id="091ad-109">[in] Reserved.</span></span> <span data-ttu-id="091ad-110">Ce paramètre doit être 0.</span><span class="sxs-lookup"><span data-stu-id="091ad-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="091ad-111">[out] Un pointeur qui pointe vers `null` avant l’appel.</span><span class="sxs-lookup"><span data-stu-id="091ad-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="091ad-112">Lorsque la fonction est retournée, l’adresse d’un nouveau `BSTR` qui contient le nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="091ad-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span> 

`ppSignatureIn`  
<span data-ttu-id="091ad-113">[out] Un pointeur qui reçoit un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) qui contient le `in` paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="091ad-113">[out] A pointer that receives a pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) that contains the `in` parameters for the method.</span></span> 

`ppSignatureOut`  
<span data-ttu-id="091ad-114">[out] Un pointeur qui reçoit un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) qui contient le `out` paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="091ad-114">[out] A pointer that receives a pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) that contains the `out` parameters for the method.</span></span> 

## <a name="return-value"></a><span data-ttu-id="091ad-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="091ad-115">Return value</span></span>

<span data-ttu-id="091ad-116">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="091ad-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="091ad-117">Constante</span><span class="sxs-lookup"><span data-stu-id="091ad-117">Constant</span></span>  |<span data-ttu-id="091ad-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="091ad-118">Value</span></span>  |<span data-ttu-id="091ad-119">Description</span><span class="sxs-lookup"><span data-stu-id="091ad-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="091ad-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="091ad-120">0x8004101d</span></span> | <span data-ttu-id="091ad-121">Il n’y avait aucun appel à la [ `BeginEnumeration` ](beginenumeration.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="091ad-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="091ad-122">0</span><span class="sxs-lookup"><span data-stu-id="091ad-122">0</span></span> | <span data-ttu-id="091ad-123">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="091ad-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="091ad-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="091ad-124">0x40005</span></span> | <span data-ttu-id="091ad-125">Il n’y a aucune autre propriété dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="091ad-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="091ad-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="091ad-126">Remarks</span></span>

<span data-ttu-id="091ad-127">Cette fonction encapsule un appel à la [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="091ad-127">This function wraps a call to the [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="091ad-128">L’appelant commence la séquence d’énumération en appelant le [BeginMethodEnumeration](beginmethodenumeration.md) de fonction, puis appelle la fonction [NextMethod] jusqu'à ce que la fonction retourne `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="091ad-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="091ad-129">Si vous le souhaitez, l’appelant termine la séquence en appelant [EndMethodEnumeration](endmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="091ad-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="091ad-130">L’appelant peut terminer l’énumération au début en appelant [EndMethodEnumeration](endmethodenumeration.md) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="091ad-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="091ad-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="091ad-131">Example</span></span>

<span data-ttu-id="091ad-132">Pour obtenir un exemple C++, consultez le [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="091ad-132">For a C++ example, see the [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="091ad-133">Spécifications</span><span class="sxs-lookup"><span data-stu-id="091ad-133">Requirements</span></span>  
 <span data-ttu-id="091ad-134">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="091ad-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="091ad-135">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="091ad-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="091ad-136">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="091ad-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="091ad-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="091ad-137">See also</span></span>  
[<span data-ttu-id="091ad-138">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="091ad-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
