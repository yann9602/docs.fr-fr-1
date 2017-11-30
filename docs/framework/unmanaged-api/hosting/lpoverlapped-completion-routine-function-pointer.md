---
title: LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LPOVERLAPPED_COMPLETION_ROUTINE
api_location: mscoree.dll
api_type: COM
f1_keywords: LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords: LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d50f2058796d4c5c900474cdcbe71d8a5a911ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)
Pointe vers une fonction qui avertit l’hôte lorsqu’un chevauchement (autrement dit, asynchrone) e/s sur un périphérique est terminée.  
  
 Ce pointeur de fonction a été déconseillé dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwErrorCode`  
 [in] Une valeur qui est un code d’erreur si l’appareil a été fermé ; Sinon, cette valeur est zéro.  
  
 Fermeture d’un périphérique entraîne tout en attente d’e/s sur le périphérique pour être exécutée immédiatement.  
  
 `dwNumberOfBytesTransfered`  
 [in] Le nombre d’octets transférés par l’opération d’e/s.  
  
 `lpOverlapped`  
 [in] Pointeur vers une structure qui contient des informations à utiliser pour effectuer la demande d’e/s.  
  
## <a name="remarks"></a>Remarques  
 La fonction à laquelle `LPOVERLAPPED_COMPLETION_ROUTINE` points est une fonction de rappel et doit être implémentée par le writer de l’application d’hébergement. La fonction de rappel permet à l’hôte traiter la demande d’e/s achevée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorWks.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
