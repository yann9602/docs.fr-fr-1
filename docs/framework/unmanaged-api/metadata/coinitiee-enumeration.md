---
title: "COINITIEE, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COINITIEE
api_location: mscoree.dll
api_type: COM
f1_keywords: COINITIEE
helpviewer_keywords: COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 03711186954aa24beff65e5d4d5b5e484c6dc276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="coinitiee-enumeration"></a>COINITIEE, énumération
Spécifie les constantes utilisées par [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) lors de l’initialisation du common language runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|Mode d’initialisation par défaut. Initialise l’exécution et crée la valeur par défaut <xref:System.AppDomain>.|  
|`COINITEE_DLL`|Initialise l’exécution d’une DLL managée.|  
|`COINITEE_MAIN`|Initialise l’exécution d’un EXE managé. Cela initialise le runtime, mais ne crée pas la valeur par défaut <xref:System.AppDomain>, qui est créé une fois la routine principale de l’EXE.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
