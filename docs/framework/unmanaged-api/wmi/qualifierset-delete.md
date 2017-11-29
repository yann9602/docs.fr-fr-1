---
title: "QualifierSet_Delete (fonction) (référence des API non managées)"
description: La fonction QualifierSet_Delete supprime un qualificateur par nom.
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Delete
helpviewer_keywords: QualifierSet_Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9245fc0ee109837249f1f3df400385c117a2f2d7
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetdelete-function"></a><span data-ttu-id="7e6ef-103">QualifierSet_Delete (fonction)</span><span class="sxs-lookup"><span data-stu-id="7e6ef-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="7e6ef-104">Supprime un qualificateur spécifié par nom.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7e6ef-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e6ef-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="7e6ef-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7e6ef-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7e6ef-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="7e6ef-108">[in] Un pointeur vers un [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="7e6ef-109">[in] Le nom du qualificateur de la suppression.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="7e6ef-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7e6ef-110">Return value</span></span>

<span data-ttu-id="7e6ef-111">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="7e6ef-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7e6ef-112">Constante</span><span class="sxs-lookup"><span data-stu-id="7e6ef-112">Constant</span></span>  |<span data-ttu-id="7e6ef-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="7e6ef-113">Value</span></span>  |<span data-ttu-id="7e6ef-114">Description</span><span class="sxs-lookup"><span data-stu-id="7e6ef-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7e6ef-115">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="7e6ef-115">0x80041008</span></span> | <span data-ttu-id="7e6ef-116">Le `wszName` paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="7e6ef-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="7e6ef-117">0x80041016</span></span> | <span data-ttu-id="7e6ef-118">La suppression de ce qualificateur est non conforme.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="7e6ef-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="7e6ef-119">0x80041002</span></span> | <span data-ttu-id="7e6ef-120">Le qualificateur spécifié est introuvable.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7e6ef-121">0</span><span class="sxs-lookup"><span data-stu-id="7e6ef-121">0</span></span> | <span data-ttu-id="7e6ef-122">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="7e6ef-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="7e6ef-123">0x40002</span></span> | <span data-ttu-id="7e6ef-124">Le remplacement local a été supprimé et le qualificateur d’origine de l’objet parent a repris l’étendue.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7e6ef-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="7e6ef-125">Remarks</span></span>

<span data-ttu-id="7e6ef-126">Cette fonction encapsule un appel à la [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="7e6ef-126">This function wraps a call to the [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="7e6ef-127">En raison des règles de propagation de qualificateur, un qualificateur particulier peut ont été hérité d’un autre objet et simplement remplacé dans l’instance ou la classe actuelle.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="7e6ef-128">Dans ce cas, le `QualifierSet_Delete` méthode rétablit le qualificateur de la valeur héritée d’origine.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="7e6ef-129">Dans ce cas, la fonction retourne le code d’état `WBEM_S_RESET_TO_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="7e6ef-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e6ef-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7e6ef-130">Requirements</span></span>  
 <span data-ttu-id="7e6ef-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e6ef-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e6ef-132">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7e6ef-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7e6ef-133">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7e6ef-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e6ef-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e6ef-134">See also</span></span>  
[<span data-ttu-id="7e6ef-135">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="7e6ef-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
