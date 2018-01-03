---
title: "ISymUnmanagedWriter::DefineLocalVariable, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineLocalVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89ea3e23166b4745b34b7c2af498d29564cdd68d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable, méthode
Définit une variable unique dans la portée lexicale actuelle. Cette méthode peut être appelée plusieurs fois pour une variable du même nom qui a plusieurs dossiers de base dans une étendue. Dans ce cas, toutefois, les valeurs de la `startOffset` et `endOffset` paramètres ne doivent pas se chevaucher.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `name`  
 [in] Un pointeur vers un `WCHAR` qui définit le nom de variable locale.  
  
 `attributes`  
 [in] Attributs de la variables locale.  
  
 `cSig`  
 [in] A `ULONG32` qui indique la taille, en octets, de la `signature` mémoire tampon.  
  
 `signature`  
 [in] La signature de variable locale.  
  
 `addrKind`  
 [in] Le type d’adresse.  
  
 `addr1`  
 [in] La première adresse de la spécification du paramètre.  
  
 `addr2`  
 [in] La deuxième adresse de la spécification du paramètre.  
  
 `addr3`  
 [in] Troisième adresse de la spécification du paramètre.  
  
 `startOffset`  
 [in] Offset de début de la variable. Ce paramètre est optionnel. Si la valeur est 0, ce paramètre est ignoré et la variable est définie dans la portée entière. Si elle est une valeur différente de zéro, la variable est comprise entre les offsets de la portée actuelle.  
  
 `endOffset`  
 [in] Offset de fin de la variable. Ce paramètre est optionnel. Si la valeur est 0, ce paramètre est ignoré et la variable est définie dans la portée entière. Si elle est une valeur différente de zéro, la variable est comprise entre les offsets de la portée actuelle.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedWriter, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [DefineGlobalVariable, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)  
 [DefineLocalVariable2, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
