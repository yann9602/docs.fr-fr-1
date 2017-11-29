---
title: "ConnectServerWmi (fonction) (référence des API non managées)"
description: "La fonction ConnectServerWmi utilise DCOM pour créer une connexion à un espace de noms WMI."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ConnectServerWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ConnectServerWmi
helpviewer_keywords: ConnectServerWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b51050bce4603ebcfe99fb38d66e54683c677293
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="c75e1-103">ConnectServerWmi (fonction)</span><span class="sxs-lookup"><span data-stu-id="c75e1-103">ConnectServerWmi function</span></span>
<span data-ttu-id="c75e1-104">Crée une connexion via DCOM à un espace de noms WMI sur un ordinateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="c75e1-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c75e1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c75e1-105">Syntax</span></span>  
  
```  
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel, 
   [in] DWORD              authLevel
);
```  
## <a name="parameters"></a><span data-ttu-id="c75e1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c75e1-106">Parameters</span></span>

<span data-ttu-id="c75e1-107">`strNetworkResource`[in] Pointeur vers un élément valide `BSTR` qui contient le chemin d’accès de l’espace de noms WMI.</span><span class="sxs-lookup"><span data-stu-id="c75e1-107">`strNetworkResource` [in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="c75e1-108">Consultez le [notes](#remarks) section pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="c75e1-108">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="c75e1-109">`strUser`[in] Un pointeur vers un élément valide `BSTR` qui contient le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c75e1-109">`strUser` [in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="c75e1-110">A `null` valeur indique le contexte de sécurité actuel.</span><span class="sxs-lookup"><span data-stu-id="c75e1-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="c75e1-111">Si l’utilisateur est dans un autre domaine que celui en cours, `strUser` peut également contenir le nom de domaine et d’utilisateur séparé par une barre oblique inverse.</span><span class="sxs-lookup"><span data-stu-id="c75e1-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="c75e1-112">`strUser`peut également être utilisateur principaux (UPN) de format, suhc comme  *userName@domainName* .</span><span class="sxs-lookup"><span data-stu-id="c75e1-112">`strUser` can also be in user principal name (UPN) format, suhc as *userName@domainName*.</span></span> <span data-ttu-id="c75e1-113">Consultez le [notes](#remarks) section pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="c75e1-113">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="c75e1-114">`strPassword`[in] Un pointeur vers un élément valide `BSTR` qui contient le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="c75e1-114">`strPassword` [in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="c75e1-115">A `null` indique le contexte de sécurité actuel.</span><span class="sxs-lookup"><span data-stu-id="c75e1-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="c75e1-116">Une chaîne vide (« ») indique un mot de passe vide.</span><span class="sxs-lookup"><span data-stu-id="c75e1-116">An empty string ("") indicates a valid zero-length password.</span></span>

<span data-ttu-id="c75e1-117">`strLocale`[in] Un pointeur vers un élément valide `BSTR` qui indique les paramètres régionaux corrects pour la récupération d’informations.</span><span class="sxs-lookup"><span data-stu-id="c75e1-117">`strLocale` [in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="c75e1-118">Pour les identificateurs de paramètres régionaux Microsoft, le format de la chaîne est « MS\_*xxx*», où *xxx* est une chaîne au format hexadécimal qui indique l’identificateur de paramètres régionaux (LCID).</span><span class="sxs-lookup"><span data-stu-id="c75e1-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="c75e1-119">Si une variable locale non valide est spécifié, la méthode retourne `WBEM_E_INVALID_PARAMETER` sauf sur Windows 7, où les paramètres régionaux par défaut du serveur sont utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="c75e1-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="c75e1-120">Si ' null1, les paramètres régionaux est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c75e1-120">If \`null1, the current locale is used.</span></span> 
 
<span data-ttu-id="c75e1-121">`lSecurityFlags`[in] Indicateurs à passer à la `ConnectServerWmi` (méthode).</span><span class="sxs-lookup"><span data-stu-id="c75e1-121">`lSecurityFlags` [in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="c75e1-122">Une valeur de zéro (0) pour ce paramètre entraîne l’appel à `ConnectServerWmi` retournant uniquement après l’établie d’une connexion au serveur.</span><span class="sxs-lookup"><span data-stu-id="c75e1-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="c75e1-123">Cela peut entraîner une application ne répond ne pas indéfiniment si le serveur est interrompue.</span><span class="sxs-lookup"><span data-stu-id="c75e1-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="c75e1-124">Les autres valeurs valides sont :</span><span class="sxs-lookup"><span data-stu-id="c75e1-124">The other valid values are:</span></span>

| <span data-ttu-id="c75e1-125">Constante</span><span class="sxs-lookup"><span data-stu-id="c75e1-125">Constant</span></span>  | <span data-ttu-id="c75e1-126">Valeur</span><span class="sxs-lookup"><span data-stu-id="c75e1-126">Value</span></span>  | <span data-ttu-id="c75e1-127">Description</span><span class="sxs-lookup"><span data-stu-id="c75e1-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="c75e1-128">0 x 40</span><span class="sxs-lookup"><span data-stu-id="c75e1-128">0x40</span></span> | <span data-ttu-id="c75e1-129">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="c75e1-129">Reserved for internal use.</span></span> <span data-ttu-id="c75e1-130">Ne pas utiliser.</span><span class="sxs-lookup"><span data-stu-id="c75e1-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="c75e1-131">0 x 80</span><span class="sxs-lookup"><span data-stu-id="c75e1-131">0x80</span></span> | <span data-ttu-id="c75e1-132">`ConnectServerWmi`Retourne un maximum de deux minutes.</span><span class="sxs-lookup"><span data-stu-id="c75e1-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

<span data-ttu-id="c75e1-133">`strAuthority`[in] Le nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c75e1-133">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="c75e1-134">Il peut afficher les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="c75e1-134">It can have the following values:</span></span>

| <span data-ttu-id="c75e1-135">Valeur</span><span class="sxs-lookup"><span data-stu-id="c75e1-135">Value</span></span> | <span data-ttu-id="c75e1-136">Description</span><span class="sxs-lookup"><span data-stu-id="c75e1-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="c75e1-137">vide</span><span class="sxs-lookup"><span data-stu-id="c75e1-137">blank</span></span> | <span data-ttu-id="c75e1-138">L’authentification NTLM est utilisée, et le domaine NTLM de l’utilisateur actuel est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c75e1-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="c75e1-139">Si `strUser` Spécifie le domaine (l’emplacement recommandé), il ne doit pas être spécifié ici.</span><span class="sxs-lookup"><span data-stu-id="c75e1-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="c75e1-140">La fonction retourne `WBEM_E_INVALID_PARAMETER` si vous spécifiez le domaine dans les deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="c75e1-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="c75e1-141">Kerberos :*nom principal*</span><span class="sxs-lookup"><span data-stu-id="c75e1-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="c75e1-142">L’authentification Kerberos est utilisée, et ce paramètre contient un nom principal Kerberos.</span><span class="sxs-lookup"><span data-stu-id="c75e1-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="c75e1-143">Valeur NTLMDOMAIN :*nom de domaine*</span><span class="sxs-lookup"><span data-stu-id="c75e1-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="c75e1-144">L’authentification NT LAN Manager est utilisée, et ce paramètre contient un nom de domaine NTLM.</span><span class="sxs-lookup"><span data-stu-id="c75e1-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`   
<span data-ttu-id="c75e1-145">[in] En règle générale, ce paramètre est `null`.</span><span class="sxs-lookup"><span data-stu-id="c75e1-145">[in] Typically, this parameter is is `null`.</span></span> <span data-ttu-id="c75e1-146">Dans le cas contraire, il est un pointeur vers un [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) objet requis par un ou plusieurs fournisseurs de classe dynamique.</span><span class="sxs-lookup"><span data-stu-id="c75e1-146">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) object required by one or more dynamic class providers.</span></span> 

`ppNamespace`  
<span data-ttu-id="c75e1-147">[out] Lorsque la fonction retourne, reçoit un pointeur vers un [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objet lié à l’espace de noms spécifié.</span><span class="sxs-lookup"><span data-stu-id="c75e1-147">[out] When the function returns, receives a pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object bound to the specified namespace.</span></span> <span data-ttu-id="c75e1-148">Elle est définie pour pointer vers `null` lorsqu’il existe une erreur.</span><span class="sxs-lookup"><span data-stu-id="c75e1-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`  
<span data-ttu-id="c75e1-149">[in] Le niveau d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="c75e1-149">[in] The impersonation level.</span></span>

`authLevel`  
<span data-ttu-id="c75e1-150">[in] Le niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="c75e1-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="c75e1-151">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c75e1-151">Return value</span></span>

<span data-ttu-id="c75e1-152">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="c75e1-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c75e1-153">Constante</span><span class="sxs-lookup"><span data-stu-id="c75e1-153">Constant</span></span>  |<span data-ttu-id="c75e1-154">Valeur</span><span class="sxs-lookup"><span data-stu-id="c75e1-154">Value</span></span>  |<span data-ttu-id="c75e1-155">Description</span><span class="sxs-lookup"><span data-stu-id="c75e1-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="c75e1-156">0 x 80041001</span><span class="sxs-lookup"><span data-stu-id="c75e1-156">0x80041001</span></span> | <span data-ttu-id="c75e1-157">Il a été un échec général.</span><span class="sxs-lookup"><span data-stu-id="c75e1-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c75e1-158">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="c75e1-158">0x80041008</span></span> | <span data-ttu-id="c75e1-159">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="c75e1-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c75e1-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c75e1-160">0x80041006</span></span> | <span data-ttu-id="c75e1-161">Pas assez de mémoire est disponible pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="c75e1-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="c75e1-162">0</span><span class="sxs-lookup"><span data-stu-id="c75e1-162">0</span></span> | <span data-ttu-id="c75e1-163">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="c75e1-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c75e1-164">Remarques</span><span class="sxs-lookup"><span data-stu-id="c75e1-164">Remarks</span></span>

<span data-ttu-id="c75e1-165">Cette fonction encapsule un appel à la [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="c75e1-165">This function wraps a call to the [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) method.</span></span>

 <span data-ttu-id="c75e1-166">Pour un accès local à l’espace de noms par défaut, `strNetworkResource` peut être un chemin d’accès de l’objet simple : « root\default » ou «\\.\root\default ».</span><span class="sxs-lookup"><span data-stu-id="c75e1-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="c75e1-167">Pour accéder à l’espace de noms par défaut sur un ordinateur distant à l’aide d’un réseau compatible avec Microsoft ou de COM, incluent le nom d’ordinateur : «\\myserver\root\default ».</span><span class="sxs-lookup"><span data-stu-id="c75e1-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="c75e1-168">Le nom d’ordinateur peut être une adresse IP ou le nom DNS.</span><span class="sxs-lookup"><span data-stu-id="c75e1-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="c75e1-169">Le `ConnectServerWmi` fonction peut également se connecter avec les ordinateurs qui exécutent IPv6 à l’aide d’une adresse IPv6.</span><span class="sxs-lookup"><span data-stu-id="c75e1-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="c75e1-170">`strUser`ne peut pas être une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="c75e1-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="c75e1-171">Si le domaine est spécifié dans `strAuthority`, il doit également être exclu dans `strUser`, ou la fonction retourne `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="c75e1-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>


## <a name="requirements"></a><span data-ttu-id="c75e1-172">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c75e1-172">Requirements</span></span>  
 <span data-ttu-id="c75e1-173">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c75e1-173">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c75e1-174">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c75e1-174">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c75e1-175">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c75e1-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75e1-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c75e1-176">See also</span></span>  
[<span data-ttu-id="c75e1-177">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="c75e1-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
