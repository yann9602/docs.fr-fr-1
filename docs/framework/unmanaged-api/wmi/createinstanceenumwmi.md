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
ms.openlocfilehash: 19a4102796da7a5692eb5b9b459a6a95ff7409f9
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="createinstanceenumwmi-function"></a>CreateInstanceEnumWmi (fonction)
Retourne un énumérateur qui retourne les instances d’une classe spécifiée qui répondent aux critères de sélection spécifiés. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
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

## <a name="parameters"></a>Paramètres

`strFilter`    
[in] Le nom de la classe pour laquelle des instances sont souhaitées. Ce paramètre ne peut pas être `null`.

`lFlags`   
[in] Une combinaison d’indicateurs qui affectent le comportement de cette fonction. Les valeurs suivantes sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code : 

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0 x 20000 | Si l’ensemble, la fonction récupère les qualificateurs stockées dans l’espace de noms localisé des paramètres régionaux de la connexion actuelle. <br/> Si ce n’est pas le cas, ensemble, la fonction récupère uniquement les qualificateurs stockées dans l’espace de noms immédiate. |
| `WBEM_FLAG_DEEP` | 0 | L’énumération inclut cette et toutes les sous-classes de la hiérarchie. |
| `WBEM_FLAG_SHALLOW` | 1 | L’énumération inclut uniquement les instances de cette classe pures et exclut toutes les instances de sous-classes qui fournissent des propriétés non trouvées dans cette classe. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0 x 10 | L’indicateur provoque un appel semi-synchrone. |
| `WBEM_FLAG_FORWARD_ONLY` | 0 x 20 | La fonction retourne un énumérateur de type avant uniquement. En règle générale, les énumérateurs avant uniquement sont plus rapides et utilisent moins de mémoire que les énumérateurs classiques, mais ils ne permettent pas d’appels à [Clone](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI conserve les pointeurs vers les objets dans l’enumration jusqu'à ce qu’elles sont disponibles. | 

Les indicateurs recommandées sont `WBEM_FLAG_RETURN_IMMEDIATELY` et `WBEM_FLAG_FORWARD_ONLY` pour de meilleures performances.

`pCtx`  
[in] En règle générale, cette valeur est `null`. Dans le cas contraire, il est un pointeur vers un [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance qui peut être utilisé par le fournisseur qui fournit les instances demandées.

`ppEnum`  
[out] Reçoit le pointeur vers l’énumérateur.

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

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0 x 80041003 | L’utilisateur ne dispose pas d’autorisation d’afficher les instances de la classe spécifiée. |
| `WBEM_E_FAILED` | 0 x 80041001 | Une erreur non spécifiée s’est produite. |
| `WBEM_E_INVALID_CLASS` | 0 x 80041010 | `strFilter` n’existe pas. |
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour terminer l’opération. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI s’est probablement arrêté, puis redémarrez. Appelez [ConnectServerWmi](connectserverwmi.md) à nouveau. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Le lien de remote procedure call (RPC) entre les processus en cours et WMI a échoué. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx) (méthode).

Notez que l’énumérateur retourné peut avoir zéro élément.

Si l’appel de fonction échoue, vous pouvez obtenir des informations d’erreur supplémentaires en appelant le [GetErrorInfo](geterrorinfo.md) (fonction).

## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
