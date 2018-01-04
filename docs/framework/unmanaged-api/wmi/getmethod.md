---
title: "GetMethod (fonction) (référence des API non managées)"
description: "La fonction GetMethod récupère des informations sur une méthode."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethod
helpviewer_keywords: GetMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f22a2dfa7aae411cac960cbad2017718df8057e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getmethod-function"></a>GetMethod (fonction)
Récupère des informations sur la méthode spécifiée.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszName`  
[in] Le nom de la méthode. Ce paramètre ne peut pas être `null` et doit pointer vers un valide `LPCWSTR`.

`lFlags`  
[in] Réservé. Ce paramètre doit être 0.

`ppInSignature`   
[out] Un pointeur vers l’adresse d’un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance qui décrit le paramteers en à la méthode. Ce paramètre est ignoré s’il est défini `null`. 

`ppOutSignature`  
[out] Un pointeur vers l’adresse d’un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance qui décrit les paramètres de sortie à la méthode. Ce paramètre est ignoré s’il est défini `null`. 

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | La propriété spécifiée est introuvable. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour terminer l’opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) (méthode).

Gestion de Windows peut définir le [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointeur vers `null` si la méthode n’a aucun paramètre dans.

Dans `ppInSignature` et `ppOutSignature` décrivent respectivement en tant que propriétés dans les paramètres, in et out un `IWbemClassObject` l’instance de la classe système [_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx). Les propriétés de `ppInsignature` sont nommés **Param***n*, où  *n*  est la position du paramètre dans la signature de méthode (par exemple, en tant que `Param1`, `Param2`, etc..). Les propriétés de `ppOutSignature` sont également appelés **Param***n*, et la valeur de retour est nommée **ReturnValue**. Pour plus d’informations et obtenir un exemple, consultez [IWbemClassObject::GetMethod méthode](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx).

## <a name="requirements"></a>Configuration requise  
**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
