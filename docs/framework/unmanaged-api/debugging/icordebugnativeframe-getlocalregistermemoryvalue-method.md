---
title: "ICorDebugNativeFrame::GetLocalRegisterMemoryValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47520e6ab4c8c3bba7383ddd08b7ff23be9dddc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterMemoryValue, méthode
Obtient la valeur d’un argument ou une variable locale dont le mot de poids faible et le mot de poids fort sont stockés dans l’emplacement de mémoire et le Registre spécifié, respectivement, pour ce frame natif.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `highWordReg`  
 [in] Valeur de l’énumération « CorDebugRegister » qui spécifie le Registre contenant le mot de poids fort de la valeur.  
  
 `lowWordAddress`  
 [in] A `CORDB_ADDRESS` valeur qui spécifie l’emplacement de mémoire qui contient le mot de poids faible de la valeur.  
  
 `cbSigBlob`  
 [in] Entier qui spécifie la taille de la signature de métadonnées binaires qui est référencée par le `pvSigBlob` paramètre.  
  
 `pvSigBlob`  
 [in] A `PCCOR_SIGNATURE` valeur qui pointe vers la signature de métadonnées binaires du type de la valeur.  
  
 `ppValue`  
 [out] Pointeur vers l’adresse d’un objet « ICorDebugValue » représentant la valeur récupérée qui est stockée dans l’emplacement de Registre et de mémoire spécifié.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 
