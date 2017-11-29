---
title: "ISymUnmanagedWriter::GetDebugInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.GetDebugInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 562e9015f2aa402a90a7b31e4b7002e68893a812
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo, méthode
Retourne les informations nécessaires à un compilateur d’écrire l’entrée de répertoire de débogage dans l’en-tête du fichier exécutable portable (PE). Le writer de symbole remplit tous les champs à l’exception de `TimeDateStamp` et `PointerToRawData`. (Le compilateur est chargé de définir ces deux champs de manière appropriée).  
  
 Un compilateur doit appeler cette méthode, émettre le blob de données dans le fichier PE, définir le `PointerToRawData` champ IMAGE_DEBUG_DIRECTORY pour pointer vers les données émises et écrire IMAGE_DEBUG_DIRECTORY dans le fichier PE. Le compilateur doit également définir le `TimeDateStamp` champ égal le `TimeDateStamp` du fichier PE qui est généré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pIDD`  
 [dans, out] Pointeur vers un IMAGE_DEBUG_DIRECTORY que le writer de symbole remplira.  
  
 `cData`  
 [in] Un `DWORD` qui contient la taille des données de débogage.  
  
 `pcData`  
 [out] Un pointeur vers un `DWORD` qui reçoit la taille de la mémoire tampon requise pour contenir les données de débogage.  
  
 `data`  
 [out] Pointeur vers une mémoire tampon qui est suffisamment grande pour contenir les données de débogage pour le magasin de symboles.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedWriter (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
