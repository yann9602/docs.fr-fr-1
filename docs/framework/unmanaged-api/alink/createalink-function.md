---
title: CreateALink, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateALink
api_location: alink.dll
api_type: DLLExport
f1_keywords: CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54a5afd8ee42fa122f3e18415be0b1d06c2f9302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="createalink-function"></a>CreateALink, fonction
Crée une instance de l’utilitaire Assembly Linker et définit un pointeur vers l’interface spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`riid`|Le nom physique d’une des interfaces Assembly Linker.|  
|`ppInterface`|L’emplacement de réussite contient un pointeur vers le `riid` interface.|  
  
## <a name="requirements"></a>Configuration requise  
 **Bibliothèque**: alink.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Al.exe (Assembly Linker)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
