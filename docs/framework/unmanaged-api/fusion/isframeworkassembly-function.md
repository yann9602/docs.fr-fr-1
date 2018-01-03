---
title: IsFrameworkAssembly, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IsFrameworkAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IsFrameworkAssembly
helpviewer_keywords: IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa077ce13031772ec2ea20708c1dbd29da02d32a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly, fonction
Obtient une valeur qui indique si l’assembly spécifié est géré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwzAssemblyReference`  
 [in] Le nom de l’assembly à vérifier.  
  
 `pbIsFrameworkAssembly`  
 [out] Valeur booléenne qui indique si l’assembly est géré.  
  
 `pwzFrameworkAssemblyIdentity`  
 [in] Chaîne non canonique qui contient l’identité unique de l’assembly.  
  
 `pccSize`  
 [in] Taille de `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Notes  
 Le `pwzAssemblyReference` paramètre est un pointeur vers une chaîne de caractères qui contient le nom d’un assembly.  
  
 Si cet assembly fait partie du .NET Framework, le `pbIsFrameworkAssembly` paramètre contient une valeur booléenne `true`.  
  
 Si l’assembly nommé n’est pas partie du .NET Framework, ou si le `pwzAssemblyReference` paramètre ne désigne pas un assembly, `pbIsFrameworkAssembly` contient une valeur booléenne `false`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions statiques globales de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
