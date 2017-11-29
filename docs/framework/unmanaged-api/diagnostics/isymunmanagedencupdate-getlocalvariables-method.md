---
title: "ISymUnmanagedENCUpdate::GetLocalVariables, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.GetLocalVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 492d41402531cb6fb92f90ab0e533fb20c6129df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a>ISymUnmanagedENCUpdate::GetLocalVariables, méthode
Obtient les variables locales.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `mdMethodToken`  
 [in] Le jeton de métadonnées de la méthode.  
  
 `cLocals`  
 [in] A `ULONG` qui indique la taille de la `rgLocals` paramètre.  
  
 `rgLocals`  
 [out] Le tableau retourné <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable` instances.  
  
 `pceltFetched`  
 [out] Un pointeur vers un `ULONG` qui reçoit la taille de la `rgLocals` mémoire tampon requise pour contenir les variables locales.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedENCUpdate (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
