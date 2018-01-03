---
title: "ICorDebugModule2::SetJMCStatus, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a461a9c05b18de45426247743c6e4ffca775025a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus, méthode
Définit l’état d’uniquement mon Code (JMC) de toutes les méthodes de toutes les classes dans ce ICorDebugModule2 à la valeur spécifiée, à l’exception de celles figurant dans le `pTokens` tableau, il définit la valeur opposée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bIsJustMycode`  
 [in] La valeur `true` si le code doit être débogué ; sinon, la valeur `false`.  
  
 `cTokens`  
 [in] Taille du tableau `pTokens`.  
  
 `pTokens`  
 [in] Un tableau de `mdToken` valeurs, chacune d’elles fait référence à une méthode qui aura son statut JMC !`bIsJustMycode`.  
  
## <a name="remarks"></a>Notes  
 L’état JMC de chaque méthode qui est spécifiée dans le `pTokens` tableau est défini à l’opposé de le `bIsJustMycode` valeur. L’état de toutes les autres méthodes dans ce module est défini sur la `bIsJustMycode` valeur.  
  
 Le `SetJMCStatus` méthode efface tous les paramètres JMC précédents dans ce module.  
  
 Le `SetJMCStatus` méthode retourne un HRESULT S_OK si toutes les fonctions ont été définies correctement. Il retourne un HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE si certaines fonctions qui sont marqués `true` ne sont pas débogable.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
