---
title: "ExecNotificationQueryWmi (fonction) (référence des API non managées)"
description: "La fonction ExecNotificationQueryWmi exécute une requête pour recevoir les événements."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ExecNotificationQueryWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ExecNotificationQueryWmi
helpviewer_keywords: ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6dd0926d2262f8d0aa125b86755017a65a95a7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="79bfb-103">ExecNotificationQueryWmi (fonction)</span><span class="sxs-lookup"><span data-stu-id="79bfb-103">ExecNotificationQueryWmi function</span></span>
<span data-ttu-id="79bfb-104">Exécute une requête pour recevoir les événements.</span><span class="sxs-lookup"><span data-stu-id="79bfb-104">Executes a query to receive events.</span></span> <span data-ttu-id="79bfb-105">L’appel retourne immédiatement, et l’appelant peut interroger l’énumérateur retourné pour les événements qu’elles arrivent.</span><span class="sxs-lookup"><span data-stu-id="79bfb-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="79bfb-106">Libération de l’énumérateur retourné annule la requête.</span><span class="sxs-lookup"><span data-stu-id="79bfb-106">Releasing the returned enumerator cancels the query.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="79bfb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79bfb-107">Syntax</span></span>  
  
```  
HRESULT ExecNotificationQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
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

## <a name="parameters"></a><span data-ttu-id="79bfb-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79bfb-108">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="79bfb-109">[in] Une chaîne avec le langage de requête valide pris en charge par Windows Management.</span><span class="sxs-lookup"><span data-stu-id="79bfb-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="79bfb-110">Il doit être « WQL », l’acronyme de langage de requête WMI.</span><span class="sxs-lookup"><span data-stu-id="79bfb-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="79bfb-111">[in] Le texte de la requête.</span><span class="sxs-lookup"><span data-stu-id="79bfb-111">[in] The text of the query.</span></span> <span data-ttu-id="79bfb-112">Ce paramètre ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="79bfb-112">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="79bfb-113">[in] Une combinaison des deux indicateurs suivants qui affectent le comportement de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="79bfb-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="79bfb-114">Ces valeurs sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="79bfb-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> 

| <span data-ttu-id="79bfb-115">Constante</span><span class="sxs-lookup"><span data-stu-id="79bfb-115">Constant</span></span> | <span data-ttu-id="79bfb-116">Value</span><span class="sxs-lookup"><span data-stu-id="79bfb-116">Value</span></span>  | <span data-ttu-id="79bfb-117">Description</span><span class="sxs-lookup"><span data-stu-id="79bfb-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="79bfb-118">0 x 10</span><span class="sxs-lookup"><span data-stu-id="79bfb-118">0x10</span></span> | <span data-ttu-id="79bfb-119">L’indicateur provoque un appel semi-synchrone.</span><span class="sxs-lookup"><span data-stu-id="79bfb-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="79bfb-120">Si cet indicateur n’est pas défini, l’appel échoue.</span><span class="sxs-lookup"><span data-stu-id="79bfb-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="79bfb-121">Il s’agit, car les événements sont reçus en continu, ce qui signifie que l’utilisateur doit interroger l’énumérateur retourné.</span><span class="sxs-lookup"><span data-stu-id="79bfb-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="79bfb-122">Cet appel de blocage infini rend qui est impossible.</span><span class="sxs-lookup"><span data-stu-id="79bfb-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="79bfb-123">0 x 20</span><span class="sxs-lookup"><span data-stu-id="79bfb-123">0x20</span></span> | <span data-ttu-id="79bfb-124">La fonction retourne un énumérateur de type avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="79bfb-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="79bfb-125">En règle générale, les énumérateurs avant uniquement sont plus rapides et utilisent moins de mémoire que les énumérateurs classiques, mais ils ne permettent pas d’appels à [Clone](clone.md).</span><span class="sxs-lookup"><span data-stu-id="79bfb-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`  
<span data-ttu-id="79bfb-126">[in] En règle générale, cette valeur est `null`.</span><span class="sxs-lookup"><span data-stu-id="79bfb-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="79bfb-127">Dans le cas contraire, il est un pointeur vers un [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance qui peut être utilisé par le fournisseur qui fournit les événements demandés.</span><span class="sxs-lookup"><span data-stu-id="79bfb-127">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested events.</span></span> 

`ppEnum`  
<span data-ttu-id="79bfb-128">[out] Si aucune erreur ne se produit, reçoit le pointeur vers l’énumérateur qui permet à l’appelant récupérer les instances dans le jeu de résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="79bfb-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="79bfb-129">Consultez le [notes](#remarks) section pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="79bfb-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="79bfb-130">[in] Le niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="79bfb-130">[in] The authorization level.</span></span>

<span data-ttu-id="79bfb-131">`impLevel`[in] Le niveau d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="79bfb-131">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="79bfb-132">[in] Un pointeur vers un [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objet qui représente l’espace de noms actuel.</span><span class="sxs-lookup"><span data-stu-id="79bfb-132">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="79bfb-133">[in] Le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="79bfb-133">[in] The user name.</span></span> <span data-ttu-id="79bfb-134">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="79bfb-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="79bfb-135">[in] Le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="79bfb-135">[in] The password.</span></span> <span data-ttu-id="79bfb-136">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="79bfb-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="79bfb-137">[in] Le nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="79bfb-137">[in] The domain name of the user.</span></span> <span data-ttu-id="79bfb-138">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="79bfb-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="79bfb-139">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="79bfb-139">Return value</span></span>

<span data-ttu-id="79bfb-140">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="79bfb-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="79bfb-141">Constante</span><span class="sxs-lookup"><span data-stu-id="79bfb-141">Constant</span></span>  |<span data-ttu-id="79bfb-142">Value</span><span class="sxs-lookup"><span data-stu-id="79bfb-142">Value</span></span>  |<span data-ttu-id="79bfb-143">Description</span><span class="sxs-lookup"><span data-stu-id="79bfb-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="79bfb-144">0 x 80041003</span><span class="sxs-lookup"><span data-stu-id="79bfb-144">0x80041003</span></span> | <span data-ttu-id="79bfb-145">L’utilisateur ne dispose pas d’autorisation d’afficher un ou plusieurs des classes de la fonction peut retourner.</span><span class="sxs-lookup"><span data-stu-id="79bfb-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="79bfb-146">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="79bfb-146">0x80041001</span></span> | <span data-ttu-id="79bfb-147">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="79bfb-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="79bfb-148">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="79bfb-148">0x80041008</span></span> | <span data-ttu-id="79bfb-149">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="79bfb-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="79bfb-150">0 x 80041010</span><span class="sxs-lookup"><span data-stu-id="79bfb-150">0x80041010</span></span> | <span data-ttu-id="79bfb-151">La requête spécifie une classe qui n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="79bfb-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="79bfb-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="79bfb-152">0x80042002</span></span> | <span data-ttu-id="79bfb-153">Trop de précision dans la remise d’événements a été demandée.</span><span class="sxs-lookup"><span data-stu-id="79bfb-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="79bfb-154">Une plus grande tolérance de panne d’interrogation doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="79bfb-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="79bfb-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="79bfb-155">0x80042001</span></span> | <span data-ttu-id="79bfb-156">La requête requess plus d’informations que la gestion de Windows peut fournir.</span><span class="sxs-lookup"><span data-stu-id="79bfb-156">The query requess more information than Windows Management can provide.</span></span> <span data-ttu-id="79bfb-157">Cela `HRESULT` est renvoyée lorsqu’un événement de la requête dans une requête d’interrogation de tous les objets dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="79bfb-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="79bfb-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="79bfb-158">0x80041017</span></span> | <span data-ttu-id="79bfb-159">La requête a dû à une erreur de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="79bfb-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="79bfb-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="79bfb-160">0x80041018</span></span> | <span data-ttu-id="79bfb-161">Le langage de requête demandé n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="79bfb-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="79bfb-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="79bfb-162">0x8004106c</span></span> | <span data-ttu-id="79bfb-163">La requête est trop complexe.</span><span class="sxs-lookup"><span data-stu-id="79bfb-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="79bfb-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="79bfb-164">0x80041006</span></span> | <span data-ttu-id="79bfb-165">Pas assez de mémoire est disponible pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="79bfb-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="79bfb-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="79bfb-166">0x80041033</span></span> | <span data-ttu-id="79bfb-167">WMI s’est probablement arrêté, puis redémarrez.</span><span class="sxs-lookup"><span data-stu-id="79bfb-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="79bfb-168">Appelez [ConnectServerWmi](connectserverwmi.md) à nouveau.</span><span class="sxs-lookup"><span data-stu-id="79bfb-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="79bfb-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="79bfb-169">0x80041015</span></span> | <span data-ttu-id="79bfb-170">Le lien de remote procedure call (RPC) entre les processus en cours et WMI a échoué.</span><span class="sxs-lookup"><span data-stu-id="79bfb-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="79bfb-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="79bfb-171">0x80041058</span></span> | <span data-ttu-id="79bfb-172">La requête ne peut pas être analysée.</span><span class="sxs-lookup"><span data-stu-id="79bfb-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="79bfb-173">0</span><span class="sxs-lookup"><span data-stu-id="79bfb-173">0</span></span> | <span data-ttu-id="79bfb-174">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="79bfb-174">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="79bfb-175">Notes</span><span class="sxs-lookup"><span data-stu-id="79bfb-175">Remarks</span></span>

<span data-ttu-id="79bfb-176">Cette fonction encapsule un appel à la [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="79bfb-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="79bfb-177">Une fois que la fonction retourne, l’appelant transmet périodiquement retourné `ppEnum` de l’objet à la [suivant](next.md) afin de voir si des événements sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="79bfb-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="79bfb-178">Il existe des limites au nombre de `AND` et `OR` mots clés qui peuvent être utilisés dans les requêtes WQL.</span><span class="sxs-lookup"><span data-stu-id="79bfb-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="79bfb-179">Grand nombre de mots clés WQL utilisés dans une requête complexe peut provoquer de WMI retourner le `WBEM_E_QUOTA_VIOLATION` (ou 0x8004106c) en tant que code d’erreur un `HRESULT` valeur.</span><span class="sxs-lookup"><span data-stu-id="79bfb-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="79bfb-180">La limite des mots clés WQL dépend de la complexité de la requête est.</span><span class="sxs-lookup"><span data-stu-id="79bfb-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="79bfb-181">Si l’appel de fonction échoue, vous pouvez obtenir des informations d’erreur supplémentaires en appelant le [GetErrorInfo](geterrorinfo.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="79bfb-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="79bfb-182">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="79bfb-182">Requirements</span></span>  
 <span data-ttu-id="79bfb-183">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79bfb-183">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79bfb-184">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="79bfb-184">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="79bfb-185">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="79bfb-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79bfb-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79bfb-186">See also</span></span>  
[<span data-ttu-id="79bfb-187">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="79bfb-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
