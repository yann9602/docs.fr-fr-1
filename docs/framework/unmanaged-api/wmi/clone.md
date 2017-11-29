---
title: "Clone (fonction) (référence des API non managées)"
description: "La fonction de clonage retourne un nouvel objet qui est un clone complet de l’objet actuel."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Clone
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Clone
helpviewer_keywords: Clone function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df6a089f66ddd6f8f9a2d5677dd8dd6917fcb719
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="clone-function"></a>Clone, fonction
Retourne un nouvel objet qui est un clone complet de l’objet actuel.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`ppCopy`  
[out] Un nouvel objet qui est complète isolés de `ptr`. Cet argument ne peut pas être `null` s’il reçoit la copie de l’objet actuel.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0 x 80041001 | Il a été un échec général. |
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | `null`a été spécifié en tant que paramètre, et n’est pas autorisé dans ce cas. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour cloner l’objet. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la [IWbemClassObject::Clone](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) (méthode).

L’objet cloné est un objet COM qui a un nombre de référence de 1.

## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
