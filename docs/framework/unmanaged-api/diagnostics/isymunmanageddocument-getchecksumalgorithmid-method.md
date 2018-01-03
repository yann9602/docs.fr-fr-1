---
title: "ISymUnmanagedDocument::GetCheckSumAlgorithmId, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58fbb5ae13433e0faa47db1e1e49d086670e69d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a>ISymUnmanagedDocument::GetCheckSumAlgorithmId, méthode
Obtient l’identificateur d’algorithme de somme de contrôle, ou retourne un GUID de tous les zéros s’il n’existe aucune somme de contrôle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Pointeur vers une variable qui reçoit l’identificateur d’algorithme de somme de contrôle.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit.  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedDocument, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
