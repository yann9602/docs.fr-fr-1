---
title: "ExecQueryWmi (fonction) (référence des API non managées)"
description: "La fonction ExecQueryWmi exécute une requête pour récupérer des objets."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ExecQueryWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ExecQueryWmi
helpviewer_keywords: ExecQueryWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ebd5463fd3b4109203e829da8e3683bbb79cf59
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="execquerywmi-function"></a><span data-ttu-id="f8402-103">ExecQueryWmi (fonction)</span><span class="sxs-lookup"><span data-stu-id="f8402-103">ExecQueryWmi function</span></span>
<span data-ttu-id="f8402-104">Exécute une requête pour récupérer des objets.</span><span class="sxs-lookup"><span data-stu-id="f8402-104">Executes a query to retrieve objects.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f8402-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8402-105">Syntax</span></span>  
  
```  
HRESULT ExecQueryWmi (
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

## <a name="parameters"></a><span data-ttu-id="f8402-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8402-106">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="f8402-107">[in] Une chaîne avec le langage de requête valide pris en charge par Windows Management.</span><span class="sxs-lookup"><span data-stu-id="f8402-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="f8402-108">Il doit être « WQL », l’acronyme de langage de requête WMI.</span><span class="sxs-lookup"><span data-stu-id="f8402-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="f8402-109">[in] Le texte de la requête.</span><span class="sxs-lookup"><span data-stu-id="f8402-109">[in] The text of the query.</span></span> <span data-ttu-id="f8402-110">Ce paramètre ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="f8402-110">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="f8402-111">[in] Une combinaison d’indicateurs qui affectent le comportement de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="f8402-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="f8402-112">Les valeurs suivantes sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="f8402-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

| <span data-ttu-id="f8402-113">Constante</span><span class="sxs-lookup"><span data-stu-id="f8402-113">Constant</span></span> | <span data-ttu-id="f8402-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="f8402-114">Value</span></span>  | <span data-ttu-id="f8402-115">Description</span><span class="sxs-lookup"><span data-stu-id="f8402-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="f8402-116">0 x 20000</span><span class="sxs-lookup"><span data-stu-id="f8402-116">0x20000</span></span> | <span data-ttu-id="f8402-117">Si l’ensemble, la fonction récupère les qualificateurs stockées dans l’espace de noms localisé des paramètres régionaux de la connexion actuelle.</span><span class="sxs-lookup"><span data-stu-id="f8402-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="f8402-118">Si ce n’est pas le cas, ensemble, la fonction récupère uniquement les qualificateurs stockées dans l’espace de noms immédiate.</span><span class="sxs-lookup"><span data-stu-id="f8402-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="f8402-119">0 x 10</span><span class="sxs-lookup"><span data-stu-id="f8402-119">0x10</span></span> | <span data-ttu-id="f8402-120">L’indicateur provoque un appel semi-synchrone.</span><span class="sxs-lookup"><span data-stu-id="f8402-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="f8402-121">0 x 20</span><span class="sxs-lookup"><span data-stu-id="f8402-121">0x20</span></span> | <span data-ttu-id="f8402-122">La fonction retourne un énumérateur de type avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="f8402-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="f8402-123">En règle générale, les énumérateurs avant uniquement sont plus rapides et utilisent moins de mémoire que les énumérateurs classiques, mais ils ne permettent pas d’appels à [Clone](clone.md).</span><span class="sxs-lookup"><span data-stu-id="f8402-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="f8402-124">0</span><span class="sxs-lookup"><span data-stu-id="f8402-124">0</span></span> | <span data-ttu-id="f8402-125">WMI conserve les pointeurs vers les objets dans l’enumration jusqu'à ce qu’elles sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="f8402-125">WMI retains pointers to objects in the enumration until they are released.</span></span> | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="f8402-126">0 x 100</span><span class="sxs-lookup"><span data-stu-id="f8402-126">0x100</span></span> | <span data-ttu-id="f8402-127">Permet de s’assurer que les retourné objets ont suffisamment d’informations dans les propriétés de ce système, tel que **__PATH**, **__RELPATH**, et **__SERVER**, ne sont pas `null`.</span><span class="sxs-lookup"><span data-stu-id="f8402-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="f8402-128">2</span><span class="sxs-lookup"><span data-stu-id="f8402-128">2</span></span> | <span data-ttu-id="f8402-129">Cet indicateur est utilisé pour le prototypage.</span><span class="sxs-lookup"><span data-stu-id="f8402-129">This flag is used for prototyping.</span></span> <span data-ttu-id="f8402-130">Il ne s’exécute pas la requête et retourne à la place d’un objet qui ressemble à un objet de résultat par défaut.</span><span class="sxs-lookup"><span data-stu-id="f8402-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="f8402-131">0 x 200</span><span class="sxs-lookup"><span data-stu-id="f8402-131">0x200</span></span> | <span data-ttu-id="f8402-132">Provoque un accès direct au fournisseur de la classe spécifiée sans tenir compte de sa classe parente ou n’importe quelles sous-classes.</span><span class="sxs-lookup"><span data-stu-id="f8402-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="f8402-133">Les indicateurs recommandées sont `WBEM_FLAG_RETURN_IMMEDIATELY` et `WBEM_FLAG_FORWARD_ONLY` pour de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="f8402-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="f8402-134">[in] En règle générale, cette valeur est `null`.</span><span class="sxs-lookup"><span data-stu-id="f8402-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="f8402-135">Dans le cas contraire, il est un pointeur vers un [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance qui peut être utilisé par le fournisseur qui fournit les classes demandées.</span><span class="sxs-lookup"><span data-stu-id="f8402-135">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="f8402-136">[out] Si aucune erreur ne se produit, reçoit le pointeur vers l’énumérateur qui permet à l’appelant récupérer les instances dans le jeu de résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="f8402-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="f8402-137">La requête peut avoir un jeu de résultats avec instances.</span><span class="sxs-lookup"><span data-stu-id="f8402-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="f8402-138">Consultez le [notes](#remarks) section pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="f8402-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="f8402-139">[in] Le niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f8402-139">[in] The authorization level.</span></span>

<span data-ttu-id="f8402-140">`impLevel`[in] Le niveau d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="f8402-140">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="f8402-141">[in] Un pointeur vers un [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objet qui représente l’espace de noms actuel.</span><span class="sxs-lookup"><span data-stu-id="f8402-141">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="f8402-142">[in] Le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f8402-142">[in] The user name.</span></span> <span data-ttu-id="f8402-143">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="f8402-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="f8402-144">[in] Le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f8402-144">[in] The password.</span></span> <span data-ttu-id="f8402-145">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="f8402-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="f8402-146">[in] Le nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f8402-146">[in] The domain name of the user.</span></span> <span data-ttu-id="f8402-147">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="f8402-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="f8402-148">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f8402-148">Return value</span></span>

<span data-ttu-id="f8402-149">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="f8402-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f8402-150">Constante</span><span class="sxs-lookup"><span data-stu-id="f8402-150">Constant</span></span>  |<span data-ttu-id="f8402-151">Valeur</span><span class="sxs-lookup"><span data-stu-id="f8402-151">Value</span></span>  |<span data-ttu-id="f8402-152">Description</span><span class="sxs-lookup"><span data-stu-id="f8402-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="f8402-153">0 x 80041003</span><span class="sxs-lookup"><span data-stu-id="f8402-153">0x80041003</span></span> | <span data-ttu-id="f8402-154">L’utilisateur ne dispose pas d’autorisation d’afficher un ou plusieurs des classes de la fonction peut retourner.</span><span class="sxs-lookup"><span data-stu-id="f8402-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="f8402-155">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="f8402-155">0x80041001</span></span> | <span data-ttu-id="f8402-156">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f8402-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f8402-157">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="f8402-157">0x80041008</span></span> | <span data-ttu-id="f8402-158">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="f8402-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="f8402-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="f8402-159">0x80041017</span></span> | <span data-ttu-id="f8402-160">La requête a dû à une erreur de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="f8402-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="f8402-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="f8402-161">0x80041018</span></span> | <span data-ttu-id="f8402-162">Le langage de requête demandé n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f8402-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="f8402-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="f8402-163">0x8004106c</span></span> | <span data-ttu-id="f8402-164">La requête est trop complexe.</span><span class="sxs-lookup"><span data-stu-id="f8402-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f8402-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f8402-165">0x80041006</span></span> | <span data-ttu-id="f8402-166">Pas assez de mémoire est disponible pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="f8402-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="f8402-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="f8402-167">0x80041033</span></span> | <span data-ttu-id="f8402-168">WMI s’est probablement arrêté, puis redémarrez.</span><span class="sxs-lookup"><span data-stu-id="f8402-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="f8402-169">Appelez [ConnectServerWmi](connectserverwmi.md) à nouveau.</span><span class="sxs-lookup"><span data-stu-id="f8402-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="f8402-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="f8402-170">0x80041015</span></span> | <span data-ttu-id="f8402-171">Le lien de remote procedure call (RPC) entre les processus en cours et WMI a échoué.</span><span class="sxs-lookup"><span data-stu-id="f8402-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="f8402-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f8402-172">0x80041002</span></span> | <span data-ttu-id="f8402-173">La requête spécifie une classe qui n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="f8402-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f8402-174">0</span><span class="sxs-lookup"><span data-stu-id="f8402-174">0</span></span> | <span data-ttu-id="f8402-175">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="f8402-175">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f8402-176">Remarques</span><span class="sxs-lookup"><span data-stu-id="f8402-176">Remarks</span></span>

<span data-ttu-id="f8402-177">Cette fonction encapsule un appel à la [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="f8402-177">This function wraps a call to the [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="f8402-178">Cette fonction traite la requête spécifiée dans le `strQuery` paramètre et crée un énumérateur par le biais duquel l’appelant peut accéder les résultats de requête.</span><span class="sxs-lookup"><span data-stu-id="f8402-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="f8402-179">L’énumérateur est un pointeur vers un [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) interface ; la requête résultats sont des instances d’objets de classe disponibles via le [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) interface.</span><span class="sxs-lookup"><span data-stu-id="f8402-179">The enumerator is a pointer to an [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) interface; the query results are instances of class objects made available through the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) interface.</span></span>

<span data-ttu-id="f8402-180">Il existe des limites au nombre de `AND` et `OR` mots clés qui peuvent être utilisés dans les requêtes WQL.</span><span class="sxs-lookup"><span data-stu-id="f8402-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="f8402-181">Grand nombre de mots clés WQL utilisés dans une requête complexe peut provoquer de WMI retourner le `WBEM_E_QUOTA_VIOLATION` (ou 0x8004106c) en tant que code d’erreur un `HRESULT` valeur.</span><span class="sxs-lookup"><span data-stu-id="f8402-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="f8402-182">La limite des mots clés WQL dépend de la complexité de la requête est.</span><span class="sxs-lookup"><span data-stu-id="f8402-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="f8402-183">Si l’appel de fonction échoue, vous pouvez obtenir des informations d’erreur supplémentaires en appelant le [GetErrorInfo](geterrorinfo.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="f8402-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8402-184">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f8402-184">Requirements</span></span>  
 <span data-ttu-id="f8402-185">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8402-185">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8402-186">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f8402-186">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f8402-187">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f8402-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8402-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8402-188">See also</span></span>  
[<span data-ttu-id="f8402-189">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="f8402-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
