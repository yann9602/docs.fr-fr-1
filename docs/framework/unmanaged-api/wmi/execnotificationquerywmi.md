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
# <a name="execnotificationquerywmi-function"></a>ExecNotificationQueryWmi (fonction)
Exécute une requête pour recevoir les événements. L’appel retourne immédiatement, et l’appelant peut interroger l’énumérateur retourné pour les événements qu’elles arrivent. Libération de l’énumérateur retourné annule la requête.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
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

## <a name="parameters"></a>Paramètres

`strQueryLanguage`    
[in] Une chaîne avec le langage de requête valide pris en charge par Windows Management. Il doit être « WQL », l’acronyme de langage de requête WMI.

`strQuery`  
[in] Le texte de la requête. Ce paramètre ne peut pas être `null`.

`lFlags`   
[in] Une combinaison des deux indicateurs suivants qui affectent le comportement de cette fonction. Ces valeurs sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code. 

| Constante | Value  | Description  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0 x 10 | L’indicateur provoque un appel semi-synchrone. Si cet indicateur n’est pas défini, l’appel échoue. Il s’agit, car les événements sont reçus en continu, ce qui signifie que l’utilisateur doit interroger l’énumérateur retourné. Cet appel de blocage infini rend qui est impossible. |
| `WBEM_FLAG_FORWARD_ONLY` | 0 x 20 | La fonction retourne un énumérateur de type avant uniquement. En règle générale, les énumérateurs avant uniquement sont plus rapides et utilisent moins de mémoire que les énumérateurs classiques, mais ils ne permettent pas d’appels à [Clone](clone.md). |

`pCtx`  
[in] En règle générale, cette valeur est `null`. Dans le cas contraire, il est un pointeur vers un [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance qui peut être utilisé par le fournisseur qui fournit les événements demandés. 

`ppEnum`  
[out] Si aucune erreur ne se produit, reçoit le pointeur vers l’énumérateur qui permet à l’appelant récupérer les instances dans le jeu de résultats de la requête. Consultez le [notes](#remarks) section pour plus d’informations.

`authLevel`  
[in] Le niveau d’autorisation.

`impLevel`[in] Le niveau d’emprunt d’identité.

`pCurrentNamespace`   
[in] Un pointeur vers un [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objet qui représente l’espace de noms actuel.

`strUser`   
[in] Le nom d’utilisateur. Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.

`strPassword`   
[in] Le mot de passe. Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.

`strAuthority`   
[in] Le nom de domaine de l’utilisateur. Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0 x 80041003 | L’utilisateur ne dispose pas d’autorisation d’afficher un ou plusieurs des classes de la fonction peut retourner. |
| `WBEM_E_FAILED` | 0 x 80041001 | Une erreur non spécifiée s’est produite. |
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_INVALID_CLASS` | 0 x 80041010 | La requête spécifie une classe qui n’existe pas. |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | Trop de précision dans la remise d’événements a été demandée. Une plus grande tolérance de panne d’interrogation doit être spécifié. |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | La requête requess plus d’informations que la gestion de Windows peut fournir. Cela `HRESULT` est renvoyée lorsqu’un événement de la requête dans une requête d’interrogation de tous les objets dans un espace de noms. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | La requête a dû à une erreur de syntaxe. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Le langage de requête demandé n’est pas pris en charge. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | La requête est trop complexe. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour terminer l’opération. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI s’est probablement arrêté, puis redémarrez. Appelez [ConnectServerWmi](connectserverwmi.md) à nouveau. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Le lien de remote procedure call (RPC) entre les processus en cours et WMI a échoué. |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | La requête ne peut pas être analysée. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx) (méthode).

Une fois que la fonction retourne, l’appelant transmet périodiquement retourné `ppEnum` de l’objet à la [suivant](next.md) afin de voir si des événements sont disponibles.

Il existe des limites au nombre de `AND` et `OR` mots clés qui peuvent être utilisés dans les requêtes WQL. Grand nombre de mots clés WQL utilisés dans une requête complexe peut provoquer de WMI retourner le `WBEM_E_QUOTA_VIOLATION` (ou 0x8004106c) en tant que code d’erreur un `HRESULT` valeur. La limite des mots clés WQL dépend de la complexité de la requête est.

Si l’appel de fonction échoue, vous pouvez obtenir des informations d’erreur supplémentaires en appelant le [GetErrorInfo](geterrorinfo.md) (fonction).

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
