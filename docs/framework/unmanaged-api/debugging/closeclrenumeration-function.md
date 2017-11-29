---
title: Fonction CloseCLREnumeration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CloseCLREnumeration
api_location: dbgshim.dll
api_type: COM
f1_keywords: CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9f14b851795c92c3ce0c1e7536a4ff78fbdf927
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="closeclrenumeration-function"></a>Fonction CloseCLREnumeration
Ferme tout valide common language runtime (CLR) événements continue-startup situés dans un tableau de handles retourné par le [fonction EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)et libère la mémoire pour les tableaux de chemin d’accès de handles et de chaînes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pHandleArray`  
 [in] Pointeur vers le tableau de handles d’événement retourné par la [fonction EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `pStringArray`  
 [in] Pointeur vers le tableau de chemins d’accès de la chaîne CLR retournée à partir de la [fonction EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `dwArrayLength`  
 [in] Valeur DWORD contenant la taille (longueur) de `pHandleArray` ou de `pStringArray` (ils sont identiques).  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Handles ouverts par le [fonction EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) sont fermés, et de la mémoire allouée pour les tableaux de handles et de chaînes est libérée.  
  
 E_INVALIDARG  
 La longueur de `pHandleArray` ne correspond pas à la longueur passée dans `dwArrayLength`.  
  
 E_FAIL (ou autres codes de retour E_)  
 La fonction ne peut pas libérer la mémoire pour `pHandleArray` et `pStringArray`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** dbgshim.h  
  
 **Bibliothèque :** dbgshim.dll  
  
 **Versions du .NET framework :** 3.5 SP1
