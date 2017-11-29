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
ms.openlocfilehash: 590bfb5d7d8cac8e322bddfe6258ad9bf377dad6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
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
  
## <a name="remarks"></a>Remarques  
 Un débogueur appelle la `GetName` méthode une fois pour obtenir la taille d’une mémoire tampon requise pour le nom. Le débogueur alloue la mémoire tampon, puis appelle la méthode une deuxième fois pour remplir la mémoire tampon. Le premier appel, pour obtenir la taille du nom, est appelé *en mode requête*.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
