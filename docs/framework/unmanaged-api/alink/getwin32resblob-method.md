---
title: "GetWin32ResBlob, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetWin32ResBlob
api_location: alink.dll
api_type: COM
f1_keywords: GetWin32ResBlob
helpviewer_keywords: GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c4456757c56440463010d4adc3d3eed90dbc07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob, méthode
Récupère le blob de ressources Win32. Appelez cette méthode après avoir défini les options d’assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID de l’assembly.  
  
 `FileToken`  
 Jeton de fichier utilisé pour récupérer le nom de fichier à utiliser lors de la construction de la ressource de Version Win32  
  
 `fDll`  
 TRUE si le fichier est une DLL, false pour un EXE.  
  
 `pszIconFile`  
 Icône facultative à insérer dans le blob de ressources.  
  
 `ppResBlob`  
 Reçoit le blob de ressources.  
  
 `pcbResBlob`  
 Reçoit la taille de l’objet blob.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Spécifications  
 Requiert alink.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 (Interface)](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink (API)](../../../../docs/framework/unmanaged-api/alink/index.md)
