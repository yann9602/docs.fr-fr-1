---
title: "SpawnDerivedClass (fonction) (référence des API non managées)"
description: "La fonction SpawnDerivedClass crée un nouvel objet qui dérive d’un objet."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SpawnDerivedClass
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SpawnDerivedClass
helpviewer_keywords: SpawnDerivedClass function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16f9a762c87e1e181202739b70cd978a80864f04
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="5adf1-103">SpawnDerivedClass (fonction)</span><span class="sxs-lookup"><span data-stu-id="5adf1-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="5adf1-104">Crée un objet de classe qui vient d’être dérivée d’un objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="5adf1-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5adf1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5adf1-105">Syntax</span></span>  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="5adf1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5adf1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5adf1-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="5adf1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5adf1-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="5adf1-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="5adf1-109">[in] Réservé.</span><span class="sxs-lookup"><span data-stu-id="5adf1-109">[in] Reserved.</span></span> <span data-ttu-id="5adf1-110">Ce paramètre doit être 0.</span><span class="sxs-lookup"><span data-stu-id="5adf1-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="5adf1-111">[out] Reçoit le pointeur vers le nouvel objet de définition de classe.</span><span class="sxs-lookup"><span data-stu-id="5adf1-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="5adf1-112">Si une erreur se produit, un nouvel objet n’est pas renvoyé, et `ppNewClass` non de gauche est modifié.</span><span class="sxs-lookup"><span data-stu-id="5adf1-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="5adf1-113">Sa valeur ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="5adf1-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="5adf1-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5adf1-114">Return value</span></span>

<span data-ttu-id="5adf1-115">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="5adf1-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5adf1-116">Constante</span><span class="sxs-lookup"><span data-stu-id="5adf1-116">Constant</span></span>  |<span data-ttu-id="5adf1-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="5adf1-117">Value</span></span>  |<span data-ttu-id="5adf1-118">Description</span><span class="sxs-lookup"><span data-stu-id="5adf1-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="5adf1-119">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="5adf1-119">0x80041001</span></span> | <span data-ttu-id="5adf1-120">Il a été un échec général.</span><span class="sxs-lookup"><span data-stu-id="5adf1-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="5adf1-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="5adf1-121">0x80041016</span></span> | <span data-ttu-id="5adf1-122">Une opération non valide, telles que la génération d’une classe à partir d’une instance, a été demandée.</span><span class="sxs-lookup"><span data-stu-id="5adf1-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="5adf1-123">La classe source n’a pas complètement a été définie ou inscrits avec la gestion de Windows, pour une nouvelle classe dérivée n’est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="5adf1-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5adf1-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5adf1-124">0x80041006</span></span> | <span data-ttu-id="5adf1-125">Pas assez de mémoire est disponible pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="5adf1-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5adf1-126">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="5adf1-126">0x80041008</span></span> | <span data-ttu-id="5adf1-127">`ppNewClass` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="5adf1-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5adf1-128">0</span><span class="sxs-lookup"><span data-stu-id="5adf1-128">0</span></span> | <span data-ttu-id="5adf1-129">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="5adf1-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5adf1-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="5adf1-130">Remarks</span></span>

<span data-ttu-id="5adf1-131">Cette fonction encapsule un appel à la [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5adf1-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="5adf1-132">`ptr`doit être une définition de classe qui devient la classe parente de l’objet généré.</span><span class="sxs-lookup"><span data-stu-id="5adf1-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="5adf1-133">L’objet retourné est une sous-classe de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="5adf1-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="5adf1-134">Le nouvel objet retourné dans `ppNewClass` devient automatiquement une sous-classe de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="5adf1-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="5adf1-135">Ce comportement ne peut pas être substitué.</span><span class="sxs-lookup"><span data-stu-id="5adf1-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="5adf1-136">Il n’existe aucune autre méthode par laquelle les sous-classes (classes dérivées) peuvent être créés.</span><span class="sxs-lookup"><span data-stu-id="5adf1-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="5adf1-137">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5adf1-137">Requirements</span></span>  
 <span data-ttu-id="5adf1-138">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5adf1-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5adf1-139">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5adf1-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5adf1-140">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5adf1-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5adf1-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5adf1-141">See also</span></span>  
[<span data-ttu-id="5adf1-142">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="5adf1-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
