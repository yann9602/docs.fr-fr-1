---
title: "QualifierSet_EndEnumeration (fonction) (référence des API non managées)"
description: "La fonction QualifierSet_EndEnumeration met fin à une énumération."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_EndEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_EndEnumeration
helpviewer_keywords: QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7868a0c0ba5abb880af201ce73b35f5ffed6f223
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetendenumeration-function"></a><span data-ttu-id="e44b9-103">QualifierSet_EndEnumeration (fonction)</span><span class="sxs-lookup"><span data-stu-id="e44b9-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="e44b9-104">Met fin à l’énumération commencée avec un appel à la [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="e44b9-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e44b9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e44b9-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="e44b9-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e44b9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e44b9-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="e44b9-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="e44b9-108">[in] Un pointeur vers un [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="e44b9-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="e44b9-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e44b9-109">Return value</span></span>

<span data-ttu-id="e44b9-110">La valeur suivante est retournée par cette fonction est définie dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez la définir en tant que constante dans votre code :</span><span class="sxs-lookup"><span data-stu-id="e44b9-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="e44b9-111">Constante</span><span class="sxs-lookup"><span data-stu-id="e44b9-111">Constant</span></span>  |<span data-ttu-id="e44b9-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="e44b9-112">Value</span></span>  |<span data-ttu-id="e44b9-113">Description</span><span class="sxs-lookup"><span data-stu-id="e44b9-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e44b9-114">0</span><span class="sxs-lookup"><span data-stu-id="e44b9-114">0</span></span> | <span data-ttu-id="e44b9-115">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="e44b9-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e44b9-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="e44b9-116">Remarks</span></span>

<span data-ttu-id="e44b9-117">Cette fonction encapsule un appel à la [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="e44b9-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="e44b9-118">Cet appel est recommandé, mais pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e44b9-118">This call is recommended, but not required.</span></span> <span data-ttu-id="e44b9-119">Il libère immédiatement les ressources associées à l’énumération.</span><span class="sxs-lookup"><span data-stu-id="e44b9-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="e44b9-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e44b9-120">Requirements</span></span>  

<span data-ttu-id="e44b9-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e44b9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="e44b9-122">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e44b9-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="e44b9-123">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e44b9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e44b9-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e44b9-124">See also</span></span>  
[<span data-ttu-id="e44b9-125">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="e44b9-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
