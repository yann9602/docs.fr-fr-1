---
title: "GetMethodOrigin (fonction) (référence des API non managées)"
description: "La fonction GetMethodOrigin détermine la classe dans laquelle une méthode est déclarée."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodOrigin
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodOrigin
helpviewer_keywords: GetMethodOrigin function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a97376b459a5d9cce9b18ff692ac4c7535a24a56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getmethodorigin-function"></a>GetMethodOrigin (fonction)
Détermine la classe dans laquelle une méthode est déclarée.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszMethodName`  
[in] Le nom de la méthode de l’objet dont la classe propriétaire est demandée. 

`pstrClassName`  
[out] Reçoit le nom de la classe qui possède la méthode.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | La méthode spécifiée est introuvable. |
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un ou plusieurs paramètres ne sont pas valides. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::GetMethodOrigin](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) (méthode).

Car une classe peut hériter des méthodes à partir d’une ou plusieurs classes de base, les développeurs souhaitent souvent de déterminer la classe dans laquelle une méthode donnée est définie.

Le `pstrClassName` paramètre ne doit pas pointer vers un valide `BSTR` avant l’appel de la fonction, car il s’agit d’un `out` paramètre ; ce pointeur n’est pas libéré une fois que la fonction retourne.

## <a name="requirements"></a>Configuration requise  
**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
