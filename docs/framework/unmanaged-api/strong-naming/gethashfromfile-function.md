---
title: GetHashFromFile, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromFile
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromFile
helpviewer_keywords: GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c8e84881822cbafa8c43c3669f7522c390d5c5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromfile-function"></a>GetHashFromFile, fonction
Génère un hachage sur le contenu du fichier spécifié.  
  
 Cette fonction est déconseillée. Utilisez le [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szFilePath`  
 [in] Le nom du fichier à hacher.  
  
 `piHashAlg`  
 [dans, out] L’algorithme à utiliser lors de la génération du hachage. Les algorithmes valides sont ceux définis par le CryptoAPI Win32. Si `piHashAlg` est définie sur 0, l’algorithme par défaut CALG_SHA-1 est utilisé.  
  
 `pbHash`  
 [out] Tableau d’octets contenant le hachage généré.  
  
 `cchHash`  
 [in] La taille maximale de la mémoire tampon qui `pbHash` pointe vers.  
  
 `pchHash`  
 [out] La taille, en octets, de retourné `pbHash`.  
  
## <a name="remarks"></a>Remarques  
 Cette fonction est identique à [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), sauf que la spécification de nom de fichier est au format ANSI au lieu d’Unicode.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [GetHashFromFile (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [GetHashFromFileW (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [ICLRStrongName Interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
