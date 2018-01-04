---
title: Fonction GetTypeLibInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetTypeLibInfo
api_location: TlbRef.dll
api_type: DLLExport
f1_keywords: GetTypeLibInfo
helpviewer_keywords: GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f6b1ad18809b46b7a2b38137231028f696d51b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="gettypelibinfo-function"></a>Fonction GetTypeLibInfo
Retourne des informations sur la bibliothèque de types spécifiée en examinant sa [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) structure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szFile`  
 [in] Le nom de fichier de la bibliothèque de types.  
  
 `pTypeLibID`  
 [out] Le GUID de la bibliothèque de types.  
  
 `pTypeLibLCID`  
 [out] ID de localisation de la bibliothèque de types.  
  
 `pTypeLibPlatform`  
 [out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) indicateur qui identifie le système d’exploitation cible pour la bibliothèque de types. Les valeurs courantes sont SYS_WIN32 et SYS_WIN64.  
  
 `pTypeLibMajorVer`  
 [out] Numéro de version principale de la bibliothèque de types. Par exemple, pour la version *x.y*, le numéro de version majeure est *x*.  
  
 `pTypeLibMinorVer`  
 [out] Numéro de version secondaire de la bibliothèque de types. Par exemple, pour la version *x.y*, le numéro de version mineure est *y*.  
  
## <a name="remarks"></a>Notes  
 Le `GetTypeLibInfo` fonction est appelée par le [Tlbexp.exe (exportateur)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md). Cet outil génère une bibliothèque de types décrivant les types dans un assembly du common language runtime (CLR).  
  
 Si un paramètre est null, la fonction retourne un `HRESULT` de `E_POINTER`. Sinon, il retourne `S_OK`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** TlbRef.h  
  
 **Bibliothèque :** TlbRef.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’assistance Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx de le dont (fonction)](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)
