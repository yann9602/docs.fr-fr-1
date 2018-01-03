---
title: "ICorDebugFunction2::GetVersionNumber, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.GetVersionNumber
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16902d1a50f691ae555fdbc964bb9a1c6bf563c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber, méthode
Obtient la version Modifier & Continuer de cette fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pnVersion`  
 [out] Pointeur vers un entier qui représente le numéro de version de la fonction qui est représentée par cet objet ICorDebugFunction2.  
  
## <a name="remarks"></a>Notes  
 Le runtime conserve une trace du nombre de modifications qui ont eu lieu pour chaque module pendant une session de débogage. Le numéro de version d’une fonction est un supérieur au nombre de la modification qui a introduit la fonction. Version d’origine de la fonction est 1. Le numéro est incrémenté chaque fois qu’un module [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) est appelé sur ce module. Par conséquent, si le corps d’une fonction a été remplacé dans le premier et le troisième appel à `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` peut retourner la version 1, 2 ou 4 de cette fonction, mais pas la version 3. (Cette fonction n’aura aucune version 3).  
  
 Le numéro de version est suivi séparément pour chaque module. Par conséquent, si vous effectuez quatre modifications sur le Module 1 et aucune sur le Module 2, votre modification suivante sur le Module 1 affecte un numéro de version 6 à toutes les fonctions modifiées dans le Module 1. Si la même modification affecte le Module 2, les fonctions dans le Module 2 obtient un numéro de version 2.  
  
 Le numéro de version obtenues par le `GetVersionNumber` méthode peut être inférieur à celui obtenu par [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).  
  
 Le [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) méthode effectue la même opération que `ICorDebugFunction2::GetVersionNumber`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
