---
title: "ICorDebugNativeFrame::GetLocalRegisterValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetLocalRegisterValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03f528547797cd7eaf7d18ba63203bcbf0300e69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterValue, méthode
Obtient la valeur d’un argument ou une variable locale qui est stockée dans le Registre spécifié pour ce frame natif.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `reg`  
 [in] Valeur de l’énumération « CorDebugRegister » qui spécifie le Registre contenant la valeur.  
  
 `cbSigBlob`  
 [in] Entier qui spécifie la taille de la signature de métadonnées binaires qui est référencée par le `pvSigBlob` paramètre.  
  
 `pvSigBlob`  
 [in] A `PCCOR_SIGNATURE` valeur qui pointe vers la signature de métadonnées binaires du type de la valeur.  
  
 `ppValue`  
 [out] Pointeur vers l’adresse d’un objet « ICorDebugValue » représentant la valeur récupérée qui est stockée dans le Registre spécifié.  
  
## <a name="remarks"></a>Notes  
 Le `GetLocalRegisterValue` méthode peut être utilisée dans un frame natif ou un juste-à-temps (JIT)-frame compilé.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 
