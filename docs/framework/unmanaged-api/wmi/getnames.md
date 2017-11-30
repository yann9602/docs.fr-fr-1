---
title: "GetNames (fonction) (référence des API non managées)"
description: "La fonction GetNames récupère les noms des propriétés d’un objet."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetNames
helpviewer_keywords: GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2ba2530dd43e6924187c80214d5efa13ebc548de
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="getnames-function"></a>GetNames (fonction)
Récupère un sous-ensemble ou tous les noms des propriétés d’un objet. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszQualifierName`  
[in] Un pointeur vers un élément valide `LPCWSTR` qui spécifie un nom du qualificateur qui fonctionne en tant que partie d’un filtre. Pour plus d’informations, consultez la [notes](#remarks) section. Ce paramètre peut être `null`. 

`lFlags`  
[in] Une combinaison des champs de bits. Pour plus d’informations, consultez la [notes](#remarks) section.

`pQualifierValue`   
[in] Un pointeur vers un élément valide `VARIANT` structure initialisé à une valeur de filtre. Ce paramètre peut être `null`. 

`pstrNames`  
[out] A `SAFEARRAY` structure qui contient les noms de propriété. À l’entrée, ce paramètre doit toujours être un pointeur vers `null`. Consultez le [notes](#remarks) section pour plus d’informations. 

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0 x 80041001 | Il a été un échec général. |
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un ou plusieurs paramètres ne sont pas valides, ou une combinaison incorrecte d’indicateurs et de paramètres a été spécifiée. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour terminer l’opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) (méthode).

Nommé retourné est contrôlé par une combinaison d’indicateurs et de paramètres. Par exemple, la fonction peut retourner les noms de toutes les propriétés ou uniquement les noms des propriétés de clé.  Le filtre principal est spécifié dans le `lFlags` paramètre et les autres paramètres varient selon qu’il.

Valeurs de l’indicateur de `lFlags` sont des champs de bits


Les indicateurs qui peuvent être passés en tant que le `lEnumFlags` argument sont des champs de bits sont définis dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code.  Vous pouvez combiner un indicateur de chaque groupe de tout indicateur de tout autre groupe. Toutefois, les indicateurs à partir du même groupe sont mutuellement exclusifs. 

| Indicateurs de groupe 1 |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Retourner tous les noms de propriété. `strQualifierName`et `pQualifierVal` ne sont pas utilisés. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Retourner uniquement les propriétés qui ont un qualificateur du nom spécifié par le `strQualifierName` paramètre. Si cet indicateur est utilisé, vous devez spécifier `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Retourner uniquement des propriétés qui n’ont pas d’un qualificateur du nom spécifié par le `strQualifierName` paramètre. Si cet indicateur est utilisé, vous devez spécifier `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Retourne uniquement les propriétés qui ont un qualificateur du nom spécifié par le `wszQualifierName` paramètre et également avoir une valeur identique à celle spécifiée par la `pQualifierVal` structure. Si cet indicateur est utilisé, vous devez spécifier à la fois un `wszQualifierName` et un `pQualifierValue`. |

| Indicateurs de groupe 2 |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0 x 4 | Retourner uniquement les noms des propriétés qui définissent les clés. |
|`WBEM_FLAG_REFS_ONLY` | 0 x 8 | Retour uniquement noms de propriétés qui sont des références d’objet. |

| Indicateurs de groupe 3 |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0 x 10 | Retourner uniquement les noms de propriété qui appartiennent à la classe la plus dérivée. Exclure les propriétés des classes parentes. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0 x 20 | Retourner uniquement les noms de propriété qui appartiennent à des classes parentes. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0 x 30 | Retourner uniquement les noms des propriétés système. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0 x 40 | Retourner uniquement les noms des propriétés de non système. |

La fonction alloue une nouvelle toujours `SAFEARRAY` si elle retourne `WBEM_S_NO_ERROR`, et `pstrNames` est toujours défini à pointer sur elle. Le tableau retourné peut avoir des éléments, 0 si aucune propriété correspondent aux filtres spécifiés. Si la fonction retourne une valeur autre que `WBM_S_NO_ERROR`, un nouveau `SAFEARRAY` structure n’est pas retournée.
 
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
