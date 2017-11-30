---
title: "EndEnumeration (fonction) (référence des API non managées)"
description: "La fonction EndEnumeration met fin à une énumération."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: EndEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: EndEnumeration
helpviewer_keywords: EndEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 043fce26870e5af2850b9f2e91e7e97c7bee6c90
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="endenumeration-function"></a><span data-ttu-id="3565c-103">EndEnumeration (fonction)</span><span class="sxs-lookup"><span data-stu-id="3565c-103">EndEnumeration function</span></span>
<span data-ttu-id="3565c-104">Met fin à une séquence d’énumération démarrée avec un appel à la [BeginEnumeration fonction](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="3565c-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="3565c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3565c-105">Syntax</span></span>  
  
```  
HRESULT EndEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="3565c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3565c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3565c-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="3565c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3565c-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="3565c-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>


## <a name="return-value"></a><span data-ttu-id="3565c-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3565c-109">Return value</span></span>

<span data-ttu-id="3565c-110">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="3565c-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3565c-111">Constante</span><span class="sxs-lookup"><span data-stu-id="3565c-111">Constant</span></span>  |<span data-ttu-id="3565c-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="3565c-112">Value</span></span>  |<span data-ttu-id="3565c-113">Description</span><span class="sxs-lookup"><span data-stu-id="3565c-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="3565c-114">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="3565c-114">0x80041001</span></span> | <span data-ttu-id="3565c-115">Il a été un échec général.</span><span class="sxs-lookup"><span data-stu-id="3565c-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3565c-116">0</span><span class="sxs-lookup"><span data-stu-id="3565c-116">0</span></span> | <span data-ttu-id="3565c-117">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="3565c-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3565c-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="3565c-118">Remarks</span></span>

<span data-ttu-id="3565c-119">Cette fonction encapsule un appel à la [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="3565c-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="3565c-120">Un appel à la `EndEnumeration` fonction n’est pas obligatoire, mais il est recommandé, car elle libère les ressources associées à l’énumération.</span><span class="sxs-lookup"><span data-stu-id="3565c-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="3565c-121">Toutefois, les resoruces sont libérées automatiquement lors de l’énumération suivante est démarrée ou l’objet est libéré.</span><span class="sxs-lookup"><span data-stu-id="3565c-121">However, the resoruces are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="3565c-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3565c-122">Requirements</span></span>  
 <span data-ttu-id="3565c-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3565c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3565c-124">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3565c-124">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3565c-125">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3565c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3565c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3565c-126">See also</span></span>  
[<span data-ttu-id="3565c-127">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="3565c-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
