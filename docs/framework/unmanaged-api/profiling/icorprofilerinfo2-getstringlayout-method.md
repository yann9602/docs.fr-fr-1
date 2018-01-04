---
title: "ICorProfilerInfo2::GetStringLayout, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetStringLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ad91829fab31b47a1dd51bb6cc9118c2ebe4c3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout, méthode
Obtient des informations sur la disposition d'un objet string. Cette méthode est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]et est remplacé par le [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pBufferLengthOffset`  
 [out] Un pointeur vers l’offset de l’emplacement, relatif à la `ObjectID` pointeur, qui stocke la longueur de la chaîne. La longueur est stockée comme un `DWORD`.  
  
> [!NOTE]
>  Ce paramètre retourne la longueur de la chaîne proprement dite, mais pas la longueur de la mémoire tampon. La longueur de la mémoire tampon n’est plus disponible.  
  
 `PStringLengthOffset`  
 [out] Un pointeur vers l’offset de l’emplacement, relatif à la `ObjectID` pointeur, qui stocke la longueur de la chaîne. La longueur est stockée comme un `DWORD`.  
  
 `pBufferOffset`  
 [out] Un pointeur vers l’offset de la mémoire tampon, relative à la `ObjectID` pointeur, qui stocke la chaîne de caractères larges.  
  
## <a name="remarks"></a>Notes  
 Le `GetStringLayout` méthode obtient les offsets, relatif à la `ObjectID` pointeur, des emplacements dans lesquels sont stockés les éléments suivants :  
  
-   La longueur de la mémoire tampon de la chaîne.  
  
-   La longueur de la chaîne.  
  
-   Mémoire tampon qui contient la chaîne réelle de caractères larges.  
  
 Les chaînes peuvent être se terminant par null.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
