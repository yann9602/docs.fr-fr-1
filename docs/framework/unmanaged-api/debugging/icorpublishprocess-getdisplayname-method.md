---
title: "ICorPublishProcess::GetDisplayName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.GetDisplayName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bbaa05d767302bcd75303ec902a82e7992e1db3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessgetdisplayname-method"></a>ICorPublishProcess::GetDisplayName, méthode
Obtient le chemin d’accès complet du fichier exécutable pour le processus référencé par ce [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cchName`  
 [in] Taille du tableau `szName`.  
  
 `pcchName`  
 [out] Le nombre de caractères étendus retournés dans le `szName` tableau.  
  
 `szName`  
 [out] Un tableau pour stocker le nom, y compris le chemin d’accès complet du fichier exécutable. Le nom se termine par null.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub.idl, CorPub.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorPublishProcess (Interface)](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
