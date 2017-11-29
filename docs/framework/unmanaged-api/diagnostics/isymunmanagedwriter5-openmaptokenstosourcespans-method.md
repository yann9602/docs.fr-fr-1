---
title: "ISymUnmanagedWriter5::OpenMapTokensToSourceSpans, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f226a71ac6381c8ca04093beb1d9772d6e6c75e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a>ISymUnmanagedWriter5::OpenMapTokensToSourceSpans, méthode
Ouvrez une section spéciale de données personnalisé pour émettre des informations de mappage de span à source de jeton dans. Ouverture de cette section lorsqu’une méthode est déjà ouverte, ou vice versa, est une erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `HRESULT`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [Isymunmanagedwriter5, Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
