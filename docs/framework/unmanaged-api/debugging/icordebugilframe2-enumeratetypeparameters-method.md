---
title: "ICorDebugILFrame2::EnumerateTypeParameters, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2.EnumerateTypeParameters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9180ea68dde667ffe0dc8e15b98cb82efaa667ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>ICorDebugILFrame2::EnumerateTypeParameters, méthode
Obtient un objet du ICorDebugTypeEnum qui contient le <xref:System.Type> paramètres dans ce frame.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppTyParEnum`  
 Pointeur vers l’adresse d’un objet d’interface ICorDebugTypeEnum qui permet l’énumération des paramètres de type.  
  
 La liste des paramètres de type inclut les paramètres de type classe (le cas échéant) suivis par les paramètres de type (méthode) (le cas échéant).  
  
## <a name="remarks"></a>Notes  
 Utilisez le [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) méthode pour déterminer le nombre de paramètres de type de classe et de méthode de cette liste contient les paramètres de type.  
  
 Les paramètres de type ne sont pas toujours disponibles.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
