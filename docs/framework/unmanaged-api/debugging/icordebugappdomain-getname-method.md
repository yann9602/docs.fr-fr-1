---
title: "ICorDebugAppDomain::GetName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62defcb4b7a2f143269c7f617b762e3419d55426
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName, méthode
Obtient le nom du domaine d’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cchName`  
 [in] Taille du tableau `szName`. Définissez cette valeur sur zéro pour mettre cette méthode en mode requête.  
  
 `pcchName`  
 [out] Un pointeur vers la taille du nom ou le nombre de caractères réellement retournés dans `szName`. En mode requête, cette valeur permet de l’appelant savoir comment une mémoire tampon de taille à allouer pour le nom.  
  
 `szName`  
 [out] Tableau qui stocke le nom du domaine d’application.  
  
## <a name="remarks"></a>Notes  
 Un débogueur appelle la `GetName` méthode une fois pour obtenir la taille d’une mémoire tampon requise pour le nom. Le débogueur alloue la mémoire tampon, puis appelle la méthode une deuxième fois pour remplir la mémoire tampon. Le premier appel, pour obtenir la taille du nom, est appelé *en mode requête*.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
