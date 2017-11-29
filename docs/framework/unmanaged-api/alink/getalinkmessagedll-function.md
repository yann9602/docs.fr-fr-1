---
title: GetALinkMessageDll, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetALinkMessageDll
api_location: alink.dll
api_type: DLLExport
f1_keywords: GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e87fe5b49a7d939a350d5d0bcb31f79eaaf333c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll, fonction
Recherche et charge la DLL de message. Retourne 0 si Impossible de trouver ou de charger la DLL de message. La DLL de message doit être dans un sous-répertoire dont le nom est un ID de langue, ou dans le répertoire actif.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** alink.h  
  
 **Bibliothèque**: alink.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Al.exe (Assembly Linker)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
