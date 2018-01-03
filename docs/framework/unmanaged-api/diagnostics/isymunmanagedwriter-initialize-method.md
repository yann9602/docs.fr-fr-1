---
title: "ISymUnmanagedWriter::Initialize, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 737e6b5218d51d8a1a051104ecdd11240a2ddac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize, méthode
Définit l’interface d’émetteur de métadonnées avec laquelle ce writer sera associé et définit le nom de fichier de sortie dans lequel les symboles de débogage doit être écrite.  
  
 Cette méthode peut être appelée qu’une seule fois, et elle doit être appelée avant toute autre méthode de writer. Certains writers peuvent nécessiter un nom de fichier. Toutefois, vous pouvez toujours passer un nom de fichier à cette méthode sans effet négatif sur les writers qui n’utilisent pas le nom de fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `emitter`  
 [in] Pointeur vers l’interface d’émetteur de métadonnées.  
  
 `filename`  
 [in] Le nom de fichier dans lequel sont écrits les symboles de débogage. Si vous spécifiez un nom de fichier pour un writer qui n'utilise pas les noms de fichiers, ce paramètre est ignoré.  
  
 `pIStream`  
 [in] Si spécifié, le writer de symbole émettra les symboles dans le donné <xref:System.Runtime.InteropServices.ComTypes.IStream> plutôt que dans le fichier spécifié dans le `filename` paramètre. Le paramètre `pIStream` est optionnel.  
  
 `fFullBuild`  
 [in] `true` s’il s’agit d’une régénération complète ; `false` s’il s’agit d’une compilation incrémentielle.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedWriter, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Initialize2, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
