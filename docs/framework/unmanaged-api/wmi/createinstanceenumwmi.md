---
title: "CreateInstanceEnumWmi (fonction) (référence des API non managées)"
description: "La fonction CreateInstanceEnumWmi retourne un énumérateur qui contient les instances d’une classe spécifiée qui répondent aux critères de sélection."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CreateInstanceEnumWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CreateInstanceEnumWmi
helpviewer_keywords: CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b796771b07dee28470d37ca3e4292c0a244e056b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="60592-103">CreateInstanceEnumWmi (fonction)</span><span class="sxs-lookup"><span data-stu-id="60592-103">CreateInstanceEnumWmi function</span></span>
<span data-ttu-id="60592-104">Retourne un énumérateur qui retourne les instances d’une classe spécifiée qui répondent aux critères de sélection spécifiés.</span><span class="sxs-lookup"><span data-stu-id="60592-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="60592-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60592-105">Syntax</span></span>  
  
```  
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
); 
```  

## <a name="parameters"></a><span data-ttu-id="60592-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="60592-106">Parameters</span></span>

`strFilter`    
<span data-ttu-id="60592-107">[in] Le nom de la classe pour laquelle des instances sont souhaitées.</span><span class="sxs-lookup"><span data-stu-id="60592-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="60592-108">Ce paramètre ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="60592-108">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="60592-109">[in] Une combinaison d’indicateurs qui affectent le comportement de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="60592-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="60592-110">Les valeurs suivantes sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="60592-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="60592-111">Constante</span><span class="sxs-lookup"><span data-stu-id="60592-111">Constant</span></span>  |<span data-ttu-id="60592-112">Value</span><span class="sxs-lookup"><span data-stu-id="60592-112">Value</span></span>  |<span data-ttu-id="60592-113">Description</span><span class="sxs-lookup"><span data-stu-id="60592-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="60592-114">0 x 20000</span><span class="sxs-lookup"><span data-stu-id="60592-114">0x20000</span></span> | <span data-ttu-id="60592-115">Si l’ensemble, la fonction récupère les qualificateurs stockées dans l’espace de noms localisé des paramètres régionaux de la connexion actuelle.</span><span class="sxs-lookup"><span data-stu-id="60592-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="60592-116">Si ce n’est pas le cas, ensemble, la fonction récupère uniquement les qualificateurs stockées dans l’espace de noms immédiate.</span><span class="sxs-lookup"><span data-stu-id="60592-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="60592-117">0</span><span class="sxs-lookup"><span data-stu-id="60592-117">0</span></span> | <span data-ttu-id="60592-118">L’énumération inclut cette et toutes les sous-classes de la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="60592-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="60592-119">1</span><span class="sxs-lookup"><span data-stu-id="60592-119">1</span></span> | <span data-ttu-id="60592-120">L’énumération inclut uniquement les instances de cette classe pures et exclut toutes les instances de sous-classes qui fournissent des propriétés non trouvées dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="60592-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="60592-121">0 x 10</span><span class="sxs-lookup"><span data-stu-id="60592-121">0x10</span></span> | <span data-ttu-id="60592-122">L’indicateur provoque un appel semi-synchrone.</span><span class="sxs-lookup"><span data-stu-id="60592-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="60592-123">0 x 20</span><span class="sxs-lookup"><span data-stu-id="60592-123">0x20</span></span> | <span data-ttu-id="60592-124">La fonction retourne un énumérateur de type avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="60592-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="60592-125">En règle générale, les énumérateurs avant uniquement sont plus rapides et utilisent moins de mémoire que les énumérateurs classiques, mais ils ne permettent pas d’appels à [Clone](clone.md).</span><span class="sxs-lookup"><span data-stu-id="60592-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="60592-126">0</span><span class="sxs-lookup"><span data-stu-id="60592-126">0</span></span> | <span data-ttu-id="60592-127">WMI conserve les pointeurs vers les objets dans l’enumration jusqu'à ce qu’elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="60592-127">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="60592-128">Les indicateurs recommandées sont `WBEM_FLAG_RETURN_IMMEDIATELY` et `WBEM_FLAG_FORWARD_ONLY` pour de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="60592-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="60592-129">[in] En règle générale, cette valeur est `null`.</span><span class="sxs-lookup"><span data-stu-id="60592-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="60592-130">Dans le cas contraire, il est un pointeur vers un [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance qui peut être utilisé par le fournisseur qui fournit les instances demandées.</span><span class="sxs-lookup"><span data-stu-id="60592-130">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`  
<span data-ttu-id="60592-131">[out] Reçoit le pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="60592-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="60592-132">[in] Le niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="60592-132">[in] The authorization level.</span></span>

<span data-ttu-id="60592-133">`impLevel`[in] Le niveau d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="60592-133">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="60592-134">[in] Un pointeur vers un [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objet qui représente l’espace de noms actuel.</span><span class="sxs-lookup"><span data-stu-id="60592-134">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="60592-135">[in] Le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="60592-135">[in] The user name.</span></span> <span data-ttu-id="60592-136">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="60592-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="60592-137">[in] Le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="60592-137">[in] The password.</span></span> <span data-ttu-id="60592-138">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="60592-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="60592-139">[in] Le nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="60592-139">[in] The domain name of the user.</span></span> <span data-ttu-id="60592-140">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="60592-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="60592-141">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="60592-141">Return value</span></span>

<span data-ttu-id="60592-142">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="60592-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="60592-143">Constante</span><span class="sxs-lookup"><span data-stu-id="60592-143">Constant</span></span>  |<span data-ttu-id="60592-144">Value</span><span class="sxs-lookup"><span data-stu-id="60592-144">Value</span></span>  |<span data-ttu-id="60592-145">Description</span><span class="sxs-lookup"><span data-stu-id="60592-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="60592-146">0 x 80041003</span><span class="sxs-lookup"><span data-stu-id="60592-146">0x80041003</span></span> | <span data-ttu-id="60592-147">L’utilisateur ne dispose pas d’autorisation d’afficher les instances de la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="60592-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="60592-148">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="60592-148">0x80041001</span></span> | <span data-ttu-id="60592-149">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="60592-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="60592-150">0 x 80041010</span><span class="sxs-lookup"><span data-stu-id="60592-150">0x80041010</span></span> | <span data-ttu-id="60592-151">`strFilter` n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="60592-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="60592-152">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="60592-152">0x80041008</span></span> | <span data-ttu-id="60592-153">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="60592-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="60592-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="60592-154">0x80041006</span></span> | <span data-ttu-id="60592-155">Pas assez de mémoire est disponible pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="60592-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="60592-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="60592-156">0x80041033</span></span> | <span data-ttu-id="60592-157">WMI s’est probablement arrêté, puis redémarrez.</span><span class="sxs-lookup"><span data-stu-id="60592-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="60592-158">Appelez [ConnectServerWmi](connectserverwmi.md) à nouveau.</span><span class="sxs-lookup"><span data-stu-id="60592-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="60592-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="60592-159">0x80041015</span></span> | <span data-ttu-id="60592-160">Le lien de remote procedure call (RPC) entre les processus en cours et WMI a échoué.</span><span class="sxs-lookup"><span data-stu-id="60592-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="60592-161">0</span><span class="sxs-lookup"><span data-stu-id="60592-161">0</span></span> | <span data-ttu-id="60592-162">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="60592-162">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="60592-163">Notes</span><span class="sxs-lookup"><span data-stu-id="60592-163">Remarks</span></span>

<span data-ttu-id="60592-164">Cette fonction encapsule un appel à la [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="60592-164">This function wraps a call to the [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="60592-165">Notez que l’énumérateur retourné peut avoir zéro élément.</span><span class="sxs-lookup"><span data-stu-id="60592-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="60592-166">Si l’appel de fonction échoue, vous pouvez obtenir des informations d’erreur supplémentaires en appelant le [GetErrorInfo](geterrorinfo.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="60592-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="60592-167">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="60592-167">Requirements</span></span>  
 <span data-ttu-id="60592-168">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60592-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60592-169">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="60592-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="60592-170">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="60592-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60592-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60592-171">See also</span></span>  
[<span data-ttu-id="60592-172">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="60592-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
