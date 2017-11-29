---
title: "PutInstanceWmi (fonction) (référence des API non managées)"
description: "La fonction PutInstanceWmi crée ou met à jour une instance d’une classe existante."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutInstanceWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutInstanceWmi
helpviewer_keywords: PutInstanceWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7a4ffce4789fb59d84778d02b41910c974216bd
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="6ca26-103">PutInstanceWmi (fonction)</span><span class="sxs-lookup"><span data-stu-id="6ca26-103">PutInstanceWmi function</span></span>
<span data-ttu-id="6ca26-104">Crée ou met à jour une instance d’une classe existante.</span><span class="sxs-lookup"><span data-stu-id="6ca26-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="6ca26-105">L’instance est écrit dans le référentiel WMI.</span><span class="sxs-lookup"><span data-stu-id="6ca26-105">The instance is written to the WMI repository.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="6ca26-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ca26-106">Syntax</span></span>  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="6ca26-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6ca26-107">Parameters</span></span>

`pInst`    
<span data-ttu-id="6ca26-108">[in] Pointeur vers l’instance à être écrits.</span><span class="sxs-lookup"><span data-stu-id="6ca26-108">[in] A pointer to the instance to be writen.</span></span>

`lFlags`   
<span data-ttu-id="6ca26-109">[in] Une combinaison d’indicateurs qui affectent le comportement de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="6ca26-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="6ca26-110">Les valeurs suivantes sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="6ca26-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="6ca26-111">Constante</span><span class="sxs-lookup"><span data-stu-id="6ca26-111">Constant</span></span>  |<span data-ttu-id="6ca26-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="6ca26-112">Value</span></span>  |<span data-ttu-id="6ca26-113">Description</span><span class="sxs-lookup"><span data-stu-id="6ca26-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="6ca26-114">0 x 20000</span><span class="sxs-lookup"><span data-stu-id="6ca26-114">0x20000</span></span> | <span data-ttu-id="6ca26-115">Si la valeur, WMI ne stocke pas les qualificateurs avec la **modifié** flavor.</span><span class="sxs-lookup"><span data-stu-id="6ca26-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> </br> <span data-ttu-id="6ca26-116">Si ce n’est pas ensemble, il est supposé que cet objet n’est pas localisé, et tous les qualificateurs sont storedwith cette instance.</span><span class="sxs-lookup"><span data-stu-id="6ca26-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="6ca26-117">0</span><span class="sxs-lookup"><span data-stu-id="6ca26-117">0</span></span> | <span data-ttu-id="6ca26-118">Créer l’instance si elle n’existe pas, ou remplacer si elle existe déjà.</span><span class="sxs-lookup"><span data-stu-id="6ca26-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="6ca26-119">1</span><span class="sxs-lookup"><span data-stu-id="6ca26-119">1</span></span> | <span data-ttu-id="6ca26-120">Mettre à jour l’instance.</span><span class="sxs-lookup"><span data-stu-id="6ca26-120">Update the instance.</span></span> <span data-ttu-id="6ca26-121">L’instance doit exister pour l’appel réussisse.</span><span class="sxs-lookup"><span data-stu-id="6ca26-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="6ca26-122">2</span><span class="sxs-lookup"><span data-stu-id="6ca26-122">2</span></span> | <span data-ttu-id="6ca26-123">Créer l’instance.</span><span class="sxs-lookup"><span data-stu-id="6ca26-123">Create the instance.</span></span> <span data-ttu-id="6ca26-124">L’appel échoue si l’instance existe déjà.</span><span class="sxs-lookup"><span data-stu-id="6ca26-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="6ca26-125">0 x 10</span><span class="sxs-lookup"><span data-stu-id="6ca26-125">0x10</span></span> | <span data-ttu-id="6ca26-126">L’indicateur provoque un appel semi-synchrone.</span><span class="sxs-lookup"><span data-stu-id="6ca26-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`  
<span data-ttu-id="6ca26-127">[in] En règle générale, cette valeur est `null`.</span><span class="sxs-lookup"><span data-stu-id="6ca26-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="6ca26-128">Dans le cas contraire, il est un pointeur vers un [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance qui peut être utilisé par le fournisseur qui fournit les classes demandées.</span><span class="sxs-lookup"><span data-stu-id="6ca26-128">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="6ca26-129">[out] Si `null`, ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="6ca26-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="6ca26-130">Si `lFlags` contient `WBEM_FLAG_RETURN_IMMEDIATELY`, la fonction retourne immédiatement avec `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="6ca26-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="6ca26-131">Le `ppCallResult` paramètre reçoit un pointeur vers un nouveau [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) objet.</span><span class="sxs-lookup"><span data-stu-id="6ca26-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="6ca26-132">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6ca26-132">Return value</span></span>

<span data-ttu-id="6ca26-133">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="6ca26-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6ca26-134">Constante</span><span class="sxs-lookup"><span data-stu-id="6ca26-134">Constant</span></span>  |<span data-ttu-id="6ca26-135">Valeur</span><span class="sxs-lookup"><span data-stu-id="6ca26-135">Value</span></span>  |<span data-ttu-id="6ca26-136">Description</span><span class="sxs-lookup"><span data-stu-id="6ca26-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="6ca26-137">0 x 80041003</span><span class="sxs-lookup"><span data-stu-id="6ca26-137">0x80041003</span></span> | <span data-ttu-id="6ca26-138">L’utilisateur n’a pas autorisé à mettre à jour une instance de la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6ca26-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="6ca26-139">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="6ca26-139">0x80041001</span></span> | <span data-ttu-id="6ca26-140">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6ca26-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="6ca26-141">0 x 80041010</span><span class="sxs-lookup"><span data-stu-id="6ca26-141">0x80041010</span></span> | <span data-ttu-id="6ca26-142">La classe de prise en charge de cette instance n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="6ca26-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="6ca26-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="6ca26-143">0x80041028</span></span> | <span data-ttu-id="6ca26-144">un `null` a été spécifié pour une propriété qui ne peut pas être `null`, tel que celui qui est marquée par un **indexé** ou **Not_Null** qualificateur.</span><span class="sxs-lookup"><span data-stu-id="6ca26-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="6ca26-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="6ca26-145">0x8004100f</span></span> | <span data-ttu-id="6ca26-146">L’instance spécifiée n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="6ca26-146">The specified instance is not valid.</span></span> <span data-ttu-id="6ca26-147">(Par exemple, l’appel `PutInstanceWmi` avec une classe retourne cette valeur.)</span><span class="sxs-lookup"><span data-stu-id="6ca26-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6ca26-148">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="6ca26-148">0x80041008</span></span> | <span data-ttu-id="6ca26-149">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="6ca26-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="6ca26-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="6ca26-150">0x80041019</span></span> | <span data-ttu-id="6ca26-151">Le `WBEM_FLAG_CREATE_ONLY` indicateur a été spécifié, mais l’instance existe déjà.</span><span class="sxs-lookup"><span data-stu-id="6ca26-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="6ca26-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="6ca26-152">0x80041002</span></span> | <span data-ttu-id="6ca26-153">`WBEM_FLAG_UPDATE_ONLY`a été spécifié dans `lFlags`, mais l’instance n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="6ca26-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6ca26-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6ca26-154">0x80041006</span></span> | <span data-ttu-id="6ca26-155">Pas assez de mémoire est disponible pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="6ca26-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="6ca26-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="6ca26-156">0x80041033</span></span> | <span data-ttu-id="6ca26-157">WMI s’est probablement arrêté, puis redémarrez.</span><span class="sxs-lookup"><span data-stu-id="6ca26-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="6ca26-158">Appelez [ConnectServerWmi](connectserverwmi.md) à nouveau.</span><span class="sxs-lookup"><span data-stu-id="6ca26-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="6ca26-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="6ca26-159">0x80041015</span></span> | <span data-ttu-id="6ca26-160">Le lien de remote procedure call (RPC) entre les processus en cours et WMI a échoué.</span><span class="sxs-lookup"><span data-stu-id="6ca26-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="6ca26-161">0</span><span class="sxs-lookup"><span data-stu-id="6ca26-161">0</span></span> | <span data-ttu-id="6ca26-162">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="6ca26-162">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="6ca26-163">Remarques</span><span class="sxs-lookup"><span data-stu-id="6ca26-163">Remarks</span></span>

<span data-ttu-id="6ca26-164">Cette fonction encapsule un appel à la [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="6ca26-164">This function wraps a call to the [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="6ca26-165">Le `PutInstanceWmi` fonction prend en charge la création d’instances et de mise à jour des instances de classes existantes uniquement.</span><span class="sxs-lookup"><span data-stu-id="6ca26-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="6ca26-166">Selon la façon dont le `pCtx` est affectée, certaines ou toutes les propriétés de l’instance sont mis à jour.</span><span class="sxs-lookup"><span data-stu-id="6ca26-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span> 

<span data-ttu-id="6ca26-167">Lorsque l’instance vers laquelle pointe `pInst` appartient à une sous-classe, gestion de Windows appelle tous les fournisseurs de responsables pour les classes à partir de laquelle dérive la sous-classe.</span><span class="sxs-lookup"><span data-stu-id="6ca26-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="6ca26-168">Tous ces fournisseurs doivent réussir pour que l’original `PutInstanceWmi` demande réussisse.</span><span class="sxs-lookup"><span data-stu-id="6ca26-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="6ca26-169">Le fournisseur de prise en charge de la classe au premier plan dans la hiérarchie est appelé en premier.</span><span class="sxs-lookup"><span data-stu-id="6ca26-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="6ca26-170">L’ordre d’appel continue avec la sous-classe de la classe au premier plan et se poursuit à partir du haut vers le bas jusqu'à ce que Windows Management atteigne le fournisseur pour la classe propriétaire de l’instance vers laquelle pointé `pInst`.</span><span class="sxs-lookup"><span data-stu-id="6ca26-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="6ca26-171">Gestion de Windows n’appelle pas les fournisseurs pour toutes les classes enfants d’une instance.</span><span class="sxs-lookup"><span data-stu-id="6ca26-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span> 

<span data-ttu-id="6ca26-172">Lorsqu’une application doit mettre à jour une instance qui appartient à une hiérarchie de classes, les `pInst` paramètre doit pointer vers l’instance qui contient les propriétés à modifier.</span><span class="sxs-lookup"><span data-stu-id="6ca26-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="6ca26-173">Autrement dit, considérez une instance cible qui appartienne à **classeB**.</span><span class="sxs-lookup"><span data-stu-id="6ca26-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="6ca26-174">Le **classeB** instance dérive **ClassA**, et **ClassA** définit la propriété **PropA**.</span><span class="sxs-lookup"><span data-stu-id="6ca26-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="6ca26-175">Si une application souhaite apporter une modification à la valeur de **PropA** dans les **classeB** instance, il doit définir `pInst` à cette instance, plutôt qu’à une instance de **ClassA** .</span><span class="sxs-lookup"><span data-stu-id="6ca26-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="6ca26-176">Appel de `PutInstanceWmi` sur une instance d’une classe abstraite n’est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="6ca26-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="6ca26-177">Si l’appel de fonction échoue, vous pouvez obtenir des informations d’erreur supplémentaires en appelant le [GetErrorInfo](geterrorinfo.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="6ca26-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="6ca26-178">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6ca26-178">Requirements</span></span>  
 <span data-ttu-id="6ca26-179">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ca26-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ca26-180">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6ca26-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6ca26-181">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6ca26-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca26-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ca26-182">See also</span></span>  
[<span data-ttu-id="6ca26-183">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="6ca26-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
