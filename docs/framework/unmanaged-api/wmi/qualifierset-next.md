---
title: "QualifierSet_Next (fonction) (référence des API non managées)"
description: "La fonction QualifierSet_Next récupère le qualificateur suivant dans une énumération."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Next
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Next
helpviewer_keywords: QualifierSet_Next function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b66eeab2cba18268b602350c8bc8f489d943309
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetnext-function"></a>QualifierSet_Next (fonction)
Récupère le qualificateur suivant dans une énumération démarrée avec un appel à la [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) (fonction).   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`   
[in] Ce paramètre est inutilisé.

`ptr`   
[in] Un pointeur vers un [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.

`lFlags`   
[in] Réservé. Ce paramètre doit être 0.

`pstrName`   
[out] Le nom du qualificateur. Si `null`, ce paramètre est ignoré ; sinon, `pstrName` ne doit pas pointer vers un valide `BSTR` ou une fuite de mémoire se produit. Si non null, la fonction toujours alloue un nouveau `BSTR` lorsqu’elle retourne `WBEM_S_NO_ERROR`.

`pVal`   
[out] Cas de réussite, la valeur du qualificateur. Si la fonction échoue, la `VARIANT` vers lequel pointe `pVal` n’est pas modifié. Si ce paramètre est `null`, le paramètre est ignoré.

`plFlavor`   
[out] Pointeur vers un entier LONG qui reçoit le type de qualificateur. Si les informations de version ne sont pas souhaitées, ce paramètre peut être `null`. 

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre n’est pas valide. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | L’appelant n’a pas appelé [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour commencer une nouvelle énumération. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Aucun qualificateur plus n’est laissées dans l’énumération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) (méthode).

Vous appelez le `QualifierSet_Next` fonction à plusieurs reprises pour énumérer tous les qualificateurs jusqu'à ce que le retour de fonction `WBEM_S_NO_MORE_DATA`. Pour terminer l’énumération au début, appelez le [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) (fonction).

L’ordre des qualificateurs retournée lors de l’énumération n’est pas défini.

## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
