---
title: "ISymUnmanagedWriter::SetScopeRange, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetScopeRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b86df423d53c9fa3a738c603d6cc575add594cae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetscoperange-method"></a>ISymUnmanagedWriter::SetScopeRange, méthode
Définit la plage d'offsets pour la portée lexicale spécifiée. La portée devient la nouvelle portée actuelle et est placée sur une pile d’étendues. Les portées doivent former une hiérarchie. Frères ne sont pas autorisées à chevaucher.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `scopeId`  
 [in] Identificateur de l’étendue dans l’étendue.  
  
 `startOffset`  
 [in] Offset, en octets, de la première instruction dans la portée lexicale à partir du début de la méthode.  
  
 `endOffset`  
 [in] Offset, en octets, de la dernière instruction dans la portée lexicale à partir du début de la méthode.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 [ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retourne un identificateur de portée opaque qui peut être utilisé avec `ISymUnmanagedWriter::SetScopeRange` pour définir une étendue de début et de fin décalage ultérieurement. Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) sont ignorés. Les identificateurs de portée sont valides uniquement dans la méthode actuelle.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedWriter (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
