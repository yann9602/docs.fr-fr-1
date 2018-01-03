---
title: "ICorDebugAppDomain2::GetArrayOrPointerType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2.GetArrayOrPointerType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6beb75638ccbf81149fd7fa1682acca3e7673dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType, méthode
Obtient un tableau du type spécifié, ou un pointeur ou une référence au type spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `elementType`  
 [in] Valeur de l’énumération CorElementType qui spécifie le type natif sous-jacent (tableau, pointeur ou référence) à créer.  
  
 `nRank`  
 [in] Le rang (autrement dit, le nombre de dimensions) du tableau. Cette valeur doit être 0 si `elementType` spécifie un pointeur ou type référence.  
  
 `pTypeArg`  
 [in] Un pointeur vers un objet ICorDebugType qui représente le type de tableau, pointeur ou référence à créer.  
  
 `ppType`  
 [out] Un pointeur vers l’adresse d’un `ICorDebugType` type d’objet qui représente le tableau construit, type pointeur ou référence.  
  
## <a name="remarks"></a>Notes  
 La valeur de *elementType* doit être une des opérations suivantes :  
  
-   ELEMENT_TYPE_PTR  
  
-   ELEMENT_TYPE_BYREF  
  
-   ELEMENT_TYPE_ARRAY ou ELEMENT_TYPE_SZARRAY  
  
 Si la valeur de *elementType* est ELEMENT_TYPE_PTR ou ELEMENT_TYPE_BYREF, *nRank* doit être égal à zéro.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
