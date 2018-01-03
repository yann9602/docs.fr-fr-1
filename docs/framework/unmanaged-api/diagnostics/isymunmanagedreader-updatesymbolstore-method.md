---
title: "ISymUnmanagedReader::UpdateSymbolStore, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.UpdateSymbolStore
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 267037cbdf9e9bf45454bd8b584563ba1ecd847d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a>ISymUnmanagedReader::UpdateSymbolStore, méthode
Met à jour le magasin de symboles existant avec un magasin de symboles delta. Cette méthode est utilisée dans les scénarios modifier et continuer pour mettre à jour le magasin de symboles pour correspondre aux deltas avec le fichier exécutable portable d’origine (PE).  
  
> [!NOTE]
>  Vous devez spécifier un seul de le `filename` ou `pIStream` paramètres, pas les deux. Si `filename` est spécifié, le magasin de symboles sera mise à jour avec les symboles dans ce fichier. Si `pIStream` est spécifié, le magasin sera mise à jour avec les données de la <xref:System.Runtime.InteropServices.ComTypes.IStream>.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `filename`  
 [in] Le nom du fichier qui contient le magasin de symboles.  
  
 `pIStream`  
 [in] Flux de fichier, utilisé comme alternative à le `filename` paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedReader, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
