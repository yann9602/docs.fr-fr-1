---
title: "SetSecurity (fonction) (référence des API non managées)"
description: "La fonction SetSecurity récupère le jeton d’emprunt d’identité du thread actuel."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SetSecurity
helpviewer_keywords: SetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4fd7ccb0cfb25773da7e489f9ce4d6332b80a616
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="setsecurity-function"></a>SetSecurity (fonction)
Récupère le jeton d’emprunt d’identité associé au thread actuel.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a>Paramètres

`pNeedToReset`[out] Lorsque la fonction est retournée, contient un pointeur vers un `boolean` qui indique si le jeton doit être réinitialisé en appelant le [ResetSecurity](resetsecurity.md) (fonction).  

`token`  
[out] Lorsque la fonction est retournée, contient un pointeur vers le handle du jeton d’emprunt d’identité associé au thread actuel. Sa valeur peut être `null` s’il n’existe aucun jeton associé au thread actuel. 

## <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de retour est `S_OK` (0).

Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro. Pour obtenir des informations d’erreur plus complètes, appelez le [GetErrorInfo](geterrorinfo.md) (fonction).
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
