---
title: "ICeeGen::GetSectionBlock, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionBlock
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4732eef9a47f9ea1e919bd9d855afbec18974454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock, méthode
Obtient un bloc de section de la base de code.  
  
 Cette méthode est obsolète et ne doit pas être utilisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a>Paramètres  
 `section`  
 [in] La section à partir de laquelle récupérer un bloc de la base de code.  
  
 `len`  
 [in] La longueur du bloc doit être récupéré.  
  
 `align`  
 [in] Octets par rapport au début de la section, avec lequel aligner le premier octet du bloc. Il s’agit de la position du bloc dans la section.  
  
 `ppBytes`  
 [out] Pointeur vers un emplacement qui reçoit l’adresse du bloc récupéré.  
  
## <a name="remarks"></a>Remarques  
 Appelez `GetSectionBlock` uniquement si vous avez des exigences de section spéciale qui ne sont pas gérés par d’autres méthodes.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICeeGen (Interface)](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
