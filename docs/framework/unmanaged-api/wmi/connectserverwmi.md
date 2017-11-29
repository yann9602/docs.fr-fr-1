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
# <a name="connectserverwmi-function"></a>ConnectServerWmi (fonction)
Crée une connexion via DCOM à un espace de noms WMI sur un ordinateur spécifié.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
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
## <a name="parameters"></a>Paramètres

`strNetworkResource`[in] Pointeur vers un élément valide `BSTR` qui contient le chemin d’accès de l’espace de noms WMI. Consultez le [notes](#remarks) section pour plus d’informations.

`strUser`[in] Un pointeur vers un élément valide `BSTR` qui contient le nom d’utilisateur. A `null` valeur indique le contexte de sécurité actuel. Si l’utilisateur est dans un autre domaine que celui en cours, `strUser` peut également contenir le nom de domaine et d’utilisateur séparé par une barre oblique inverse. `strUser`peut également être utilisateur principaux (UPN) de format, suhc comme  *userName@domainName* . Consultez le [notes](#remarks) section pour plus d’informations.

`strPassword`[in] Un pointeur vers un élément valide `BSTR` qui contient le mot de passe. A `null` indique le contexte de sécurité actuel. Une chaîne vide (« ») indique un mot de passe vide.

`strLocale`[in] Un pointeur vers un élément valide `BSTR` qui indique les paramètres régionaux corrects pour la récupération d’informations. Pour les identificateurs de paramètres régionaux Microsoft, le format de la chaîne est « MS\_*xxx*», où *xxx* est une chaîne au format hexadécimal qui indique l’identificateur de paramètres régionaux (LCID). Si une variable locale non valide est spécifié, la méthode retourne `WBEM_E_INVALID_PARAMETER` sauf sur Windows 7, où les paramètres régionaux par défaut du serveur sont utilisé à la place. Si ' null1, les paramètres régionaux est utilisé. 
 
`lSecurityFlags`[in] Indicateurs à passer à la `ConnectServerWmi` (méthode). Une valeur de zéro (0) pour ce paramètre entraîne l’appel à `ConnectServerWmi` retournant uniquement après l’établie d’une connexion au serveur. Cela peut entraîner une application ne répond ne pas indéfiniment si le serveur est interrompue. Les autres valeurs valides sont :

| Constante  | Valeur  | Description  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0 x 40 | Réservé à un usage interne. Ne pas utiliser. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0 x 80 | `ConnectServerWmi`Retourne un maximum de deux minutes. |

`strAuthority`[in] Le nom de domaine de l’utilisateur. Il peut afficher les valeurs suivantes :

| Valeur | Description |
|---------|---------|
| vide | L’authentification NTLM est utilisée, et le domaine NTLM de l’utilisateur actuel est utilisé. Si `strUser` Spécifie le domaine (l’emplacement recommandé), il ne doit pas être spécifié ici. La fonction retourne `WBEM_E_INVALID_PARAMETER` si vous spécifiez le domaine dans les deux paramètres. |
| Kerberos :*nom principal* | L’authentification Kerberos est utilisée, et ce paramètre contient un nom principal Kerberos. |
| Valeur NTLMDOMAIN :*nom de domaine* | L’authentification NT LAN Manager est utilisée, et ce paramètre contient un nom de domaine NTLM. |

`pCtx`   
[in] En règle générale, ce paramètre est `null`. Dans le cas contraire, il est un pointeur vers un [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) objet requis par un ou plusieurs fournisseurs de classe dynamique. 

`ppNamespace`  
[out] Lorsque la fonction retourne, reçoit un pointeur vers un [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objet lié à l’espace de noms spécifié. Elle est définie pour pointer vers `null` lorsqu’il existe une erreur.

`impLevel`  
[in] Le niveau d’emprunt d’identité.

`authLevel`  
[in] Le niveau d’autorisation.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0 x 80041001 | Il a été un échec général. |
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour terminer l’opération. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) (méthode).

 Pour un accès local à l’espace de noms par défaut, `strNetworkResource` peut être un chemin d’accès de l’objet simple : « root\default » ou «\\.\root\default ». Pour accéder à l’espace de noms par défaut sur un ordinateur distant à l’aide d’un réseau compatible avec Microsoft ou de COM, incluent le nom d’ordinateur : «\\myserver\root\default ». Le nom d’ordinateur peut être une adresse IP ou le nom DNS. Le `ConnectServerWmi` fonction peut également se connecter avec les ordinateurs qui exécutent IPv6 à l’aide d’une adresse IPv6.

`strUser`ne peut pas être une chaîne vide. Si le domaine est spécifié dans `strAuthority`, il doit également être exclu dans `strUser`, ou la fonction retourne `WBEM_E_INVALID_PARAMETER`.


## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
