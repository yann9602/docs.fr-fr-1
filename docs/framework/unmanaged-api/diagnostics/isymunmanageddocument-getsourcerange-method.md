---
title: "ISymUnmanagedDocument::GetSourceRange, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetSourceRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6c47f1f491b184e9abe9d56d0729100b0d9b36a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange, méthode
Retourne la plage spécifiée de la source incorporée dans la mémoire tampon donnée. La mémoire tampon doit être suffisamment grande pour contenir la source.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `startLine`  
 [in] La ligne de départ dans le document actif.  
  
 `startColumn`  
 [in] La colonne de départ dans le document actif.  
  
 `endLine`  
 [in] La dernière ligne dans le document actif.  
  
 `endColumn`  
 [in] La dernière colonne dans le document actif.  
  
 `cSourceBytes`  
 [in] La taille de la source, en octets.  
  
 `pcSourceBytes`  
 [out] Pointeur vers une variable qui reçoit la taille de la source.  
  
 `source`  
 [out] La taille et la longueur de la plage spécifiée du document source, en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit.  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedDocument (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
