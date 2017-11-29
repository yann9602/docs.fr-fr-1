---
title: "ISymUnmanagedReader::Initialize, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5917fbe3cebe9b1e9ab91d113aee2461f414c14d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize, méthode
Initialise le lecteur de symboles avec l’interface de métadonnées de l’importateur ce lecteur sera associé, ainsi que le nom de fichier du module.  
  
> [!NOTE]
>  Cette méthode peut être appelée qu’une seule fois et doit être appelée avant toute autre méthode de lecteur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `importer`  
 [in] L’interface importateur de métadonnées à laquelle ce lecteur sera associé.  
  
 `filename`  
 [in] Le nom de fichier du module. Vous pouvez utiliser la `pIStream` paramètre à la place.  
  
 `searchPath`  
 [in] Le chemin d’accès à rechercher. Ce paramètre est optionnel.  
  
 `pIStream`  
 [in] Flux de fichier, utilisé comme alternative au paramètre de nom de fichier.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Vous devez ne spécifier qu’un seul de le `filename` ou `pIStream` paramètres, pas les deux. Le paramètre `searchPath` est optionnel.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedReader (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
