---
title: "ISymUnmanagedDocument::GetURL, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetURL
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 591383fee2f9b22a00956193555c719e72d722bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgeturl-method"></a>ISymUnmanagedDocument::GetURL, méthode
Retourne le localisateur de ressource uniforme (URL) pour ce document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cchUrl`  
 [in] La taille, en caractères, de la `szURL` mémoire tampon.  
  
 `pcchUrl`  
 [out] Pointeur vers une variable qui reçoit la taille de l’URL, y compris le caractère null de fin.  
  
 `szUrl`  
 [out] La mémoire tampon contenant l’URL.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedDocument (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
