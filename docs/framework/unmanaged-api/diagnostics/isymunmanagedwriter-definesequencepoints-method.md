---
title: "ISymUnmanagedWriter::DefineSequencePoints, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 836774114798324ac16d3263e58dd56665a9aa49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints, méthode
Définit un groupe de points de séquence dans la méthode actuelle. Chaque ligne de début et de la colonne de début définissent le début d’une instruction dans une méthode. Chaque ligne de fin et de colonne de fin définissent la fin d’une instruction dans une méthode. Les tableaux doivent être triés dans l’ordre croissant des offsets. Le décalage est mesuré à partir du début de la méthode, en octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `document`  
 [in] L’objet de document pour lequel les points de séquence sont définies.  
  
 `spCount`  
 [in] A `ULONG32` qui indique la taille de chacun de la `offsets`, `lines`, `columns`, `endLines`, et `endColumns` mémoires tampons.  
  
 `offsets`  
 [in] Le décalage des points de séquence mesuré à partir du début de la méthode.  
  
 `lines`  
 [in] Les numéros de ligne de départ des points de séquence.  
  
 `columns`  
 [in] Les numéros de colonne de début des points de séquence.  
  
 `endLines`  
 [in] Les numéros de ligne de fin des points de séquence. Ce paramètre est optionnel.  
  
 `endColumns`  
 [in] Les numéros de colonne de fin des points de séquence. Ce paramètre est optionnel.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedWriter (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
