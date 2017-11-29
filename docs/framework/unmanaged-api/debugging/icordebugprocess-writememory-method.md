---
title: "ICorDebugProcess::WriteMemory, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.WriteMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 053c6bf5f451377308f4defbeb6eff9525c4332e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory, méthode
Écrit des données dans une zone de mémoire dans ce processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `address`  
 [in] A `CORDB_ADDRESS` valeur qui est l’adresse de base de la zone de mémoire vers lequel les données est écrites. Avant le transfert de données se produit, le système vérifie que la zone de mémoire de la taille spécifiée, en commençant à l’adresse de base est accessible en écriture. Si elle n’est pas accessible, la méthode échoue.  
  
 `size`  
 [in] Le nombre d’octets à écrire dans la zone de mémoire.  
  
 `buffer`  
 [in] Une mémoire tampon qui contient les données à écrire.  
  
 `written`  
 [out] Pointeur vers une variable qui reçoit le nombre d’octets écrits dans la zone de mémoire dans ce processus. Si `written` est NULL, ce paramètre est ignoré.  
  
## <a name="remarks"></a>Remarques  
 Données sont automatiquement écrite derrière les points d’arrêt. Dans le .NET Framework version 2.0, les débogueurs natifs doivent utilisez pas cette méthode pour injecter des points d’arrêt dans le flux d’instructions. Utilisez [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) à la place.  
  
 Le `WriteMemory` méthode doit être utilisée uniquement en dehors du code managé. Cette méthode peut endommager le runtime pour une utilisation incorrecte.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
