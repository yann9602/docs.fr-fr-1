---
title: "FormatFromRawValue (fonction) (référence des API non managées)"
description: "La fonction FormatFromRawValue convertit les données de performances brutes dans un format spécifié."
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: FormatFromRawValue
api_location: PerfCounter.dll
api_type: DLLExport
f1_keywords: FormatFromRawValue
helpviewer_keywords: FormatFromRawValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3daa89ec0b40bb9c08898ecd682f05f0f0ce09a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="18f83-103">FormatFromRawValue (fonction)</span><span class="sxs-lookup"><span data-stu-id="18f83-103">FormatFromRawValue function</span></span>
<span data-ttu-id="18f83-104">Convertit une valeur de données de performances brutes au format spécifié, ou les deux valeurs de données de performances brutes si la conversion de format est basé sur le temps.</span><span class="sxs-lookup"><span data-stu-id="18f83-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="18f83-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18f83-105">Syntax</span></span>  
  
```  
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```  

## <a name="parameters"></a><span data-ttu-id="18f83-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="18f83-106">Parameters</span></span>

`dwCounterType`  
<span data-ttu-id="18f83-107">[in] Le type de compteur.</span><span class="sxs-lookup"><span data-stu-id="18f83-107">[in] The counter type.</span></span> <span data-ttu-id="18f83-108">Pour obtenir la liste des types de compteurs, consultez [WMI Performance Counter Types](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="18f83-108">For a list of counter types, see [WMI Performance Counter Types](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx).</span></span> <span data-ttu-id="18f83-109">`dwCounterType`peut être n’importe quel type de compteur à l’exception de `PERF_LARGE_RAW_FRACTION` et `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="18f83-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`  
<span data-ttu-id="18f83-110">[in] Le format dans lequel convertir les données de performances brutes.</span><span class="sxs-lookup"><span data-stu-id="18f83-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="18f83-111">Il peut prendre l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="18f83-111">It can be one of the following values:</span></span>

|<span data-ttu-id="18f83-112">Constante</span><span class="sxs-lookup"><span data-stu-id="18f83-112">Constant</span></span>  |<span data-ttu-id="18f83-113">Value</span><span class="sxs-lookup"><span data-stu-id="18f83-113">Value</span></span>  |<span data-ttu-id="18f83-114">Description</span><span class="sxs-lookup"><span data-stu-id="18f83-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="18f83-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="18f83-115">0x00000200</span></span> | <span data-ttu-id="18f83-116">Retourne la valeur calculée comme une valeur à virgule flottante double précision.</span><span class="sxs-lookup"><span data-stu-id="18f83-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="18f83-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="18f83-117">0x00000400</span></span> | <span data-ttu-id="18f83-118">Retourne la valeur calculée sous forme d’entier 64 bits.</span><span class="sxs-lookup"><span data-stu-id="18f83-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="18f83-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="18f83-119">0x00000100</span></span> | <span data-ttu-id="18f83-120">Retourne la valeur calculée sous forme d’entier 32 bits.</span><span class="sxs-lookup"><span data-stu-id="18f83-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="18f83-121">Une des valeurs précédentes peut être dissocié avec l’un des indicateurs de mise à l’échelle suivants :</span><span class="sxs-lookup"><span data-stu-id="18f83-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="18f83-122">Constante</span><span class="sxs-lookup"><span data-stu-id="18f83-122">Constant</span></span>  |<span data-ttu-id="18f83-123">Value</span><span class="sxs-lookup"><span data-stu-id="18f83-123">Value</span></span>  |<span data-ttu-id="18f83-124">Description</span><span class="sxs-lookup"><span data-stu-id="18f83-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="18f83-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="18f83-125">0x00001000</span></span> | <span data-ttu-id="18f83-126">Ne pas appliquer les facteurs d’échelle du compteur.</span><span class="sxs-lookup"><span data-stu-id="18f83-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="18f83-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="18f83-127">0x00002000</span></span> | <span data-ttu-id="18f83-128">Multipliez la valeur finale par 1 000.</span><span class="sxs-lookup"><span data-stu-id="18f83-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`  
<span data-ttu-id="18f83-129">[in] Pointeur vers la base de temps, si nécessaire pour la conversion de format.</span><span class="sxs-lookup"><span data-stu-id="18f83-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="18f83-130">Si les informations de base de temps ne sont pas nécessaires pour la conversion de format, la valeur de ce paramètre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="18f83-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="18f83-131">`pRawValue1`[in] Un pointeur vers un [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure qui représente une valeur de performance brute.</span><span class="sxs-lookup"><span data-stu-id="18f83-131">`pRawValue1` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a raw performance value.</span></span>

<span data-ttu-id="18f83-132">`pRawValue2`[in] Un pointeur vers un [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure qui représente une seconde valeur de performance brute.</span><span class="sxs-lookup"><span data-stu-id="18f83-132">`pRawValue2` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a second raw performance value.</span></span> <span data-ttu-id="18f83-133">Si une seconde valeur de performance brute n’est pas nécessaire, ce paramètre doit être `null`.</span><span class="sxs-lookup"><span data-stu-id="18f83-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

<span data-ttu-id="18f83-134">`pFmtValue`[out] Un pointeur vers un [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) structure qui reçoit la valeur de performance de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="18f83-134">`pFmtValue` [out] A pointer to a [`PDH_FMT_COUNTERVALUE`](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="18f83-135">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="18f83-135">Return value</span></span>

<span data-ttu-id="18f83-136">Les valeurs suivantes sont retournées par cette fonction :</span><span class="sxs-lookup"><span data-stu-id="18f83-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="18f83-137">Constante</span><span class="sxs-lookup"><span data-stu-id="18f83-137">Constant</span></span>  |<span data-ttu-id="18f83-138">Value</span><span class="sxs-lookup"><span data-stu-id="18f83-138">Value</span></span>  |<span data-ttu-id="18f83-139">Description</span><span class="sxs-lookup"><span data-stu-id="18f83-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="18f83-140">0</span><span class="sxs-lookup"><span data-stu-id="18f83-140">0</span></span> | <span data-ttu-id="18f83-141">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="18f83-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="18f83-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="18f83-142">0xC0000BBD</span></span> | <span data-ttu-id="18f83-143">Un argument requis est manquant ou incorrect.</span><span class="sxs-lookup"><span data-stu-id="18f83-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="18f83-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="18f83-144">0xC0000BBC</span></span> | <span data-ttu-id="18f83-145">Le handle n’est pas un objet PDH valide.</span><span class="sxs-lookup"><span data-stu-id="18f83-145">The handle is not a valid PDH object.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="18f83-146">Notes</span><span class="sxs-lookup"><span data-stu-id="18f83-146">Remarks</span></span>

<span data-ttu-id="18f83-147">Cette fonction encapsule un appel à la [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) (fonction).</span><span class="sxs-lookup"><span data-stu-id="18f83-147">This function wraps a call to the [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="18f83-148">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="18f83-148">Requirements</span></span>  
 <span data-ttu-id="18f83-149">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18f83-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18f83-150">**Bibliothèque :** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="18f83-150">**Library:** PerfCounter.dll</span></span>  
  
 <span data-ttu-id="18f83-151">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="18f83-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18f83-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18f83-152">See also</span></span>  
[<span data-ttu-id="18f83-153">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="18f83-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
