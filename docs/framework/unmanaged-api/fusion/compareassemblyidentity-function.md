---
title: CompareAssemblyIdentity, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: CompareAssemblyIdentity
helpviewer_keywords: CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 266868a65a0db75b57d46d92a469b4b6ceaa88e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity, fonction
Compare deux identités d’assembly pour déterminer s’ils sont équivalents.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwzAssemblyIdentity1`  
 [in] Identité textuelle du premier assembly de la comparaison.  
  
 `fUnified1`  
 [in] Indicateur booléen qui indique l’unification de spécifié par l’utilisateur pour `pwzAssemblyIdentity1`.  
  
 `pwzAssemblyIdentity2`  
 [in] Identité textuelle du second assembly de la comparaison.  
  
 `fUnified2`  
 [in] Indicateur booléen qui indique l’unification de spécifié par l’utilisateur pour `pwzAssemblyIdentity2`.  
  
 `pfEquivalent`  
 [out] Indicateur booléen qui indique si les deux assemblys sont équivalents.  
  
 `pResult`  
 [out] Un [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) énumération qui contient des informations détaillées sur la comparaison.  
  
## <a name="return-value"></a>Valeur de retour  
 `pfEquivalent`Retourne une valeur booléenne qui indique si les deux assemblys sont équivalents. `pResult`Retourne l’une de le `AssemblyComparisonResult` valeurs, afin de donner une raison plus détaillée pour la valeur de `pfEquivalent`.  
  
## <a name="remarks"></a>Notes  
 `CompareAssemblyIdentity`vérifie si `pwzAssemblyIdentity1` et `pwzAssemblyIdentity2` sont équivalents. `pfEquivalent`a la valeur `true` sous un ou plusieurs des conditions suivantes :  
  
-   Les identités des deux assemblys sont équivalentes. Pour les assemblys à nom fort, l’équivalence implique le nom de l’assembly, version, jeton de clé publique et la culture sont identiques. Pour les assemblys de nommés simple, l’équivalence implique une correspondance sur le nom de l’assembly et la culture.  
  
-   Les deux identités d’assembly font référence aux assemblys qui s’exécutent sur le .NET Framework. Cette condition renvoie `true` même si les numéros de version d’assembly ne correspondent pas.  
  
-   Les deux assemblys ne sont pas des assemblys managés, mais `fUnified1` ou `fUnified2` a été défini sur `true`.  
  
 Le `fUnified` indicateur indique que tous les numéros de version au numéro de version de l’assembly à nom fort sont considérés comme équivalents à l’assembly de nom fort. Par exemple, si la valeur de `pwzAssemblyIndentity1` est « MyAssembly, version = 3.0.0.0, culture = neutral, publicKeyToken =... » et la valeur de `fUnified1` est `true`, cela indique que toutes les versions de MyAssembly à partir de la version 0.0.0.0 à 3.0.0.0 doivent être traité comme équivalent. Dans ce cas, si `pwzAssemblyIndentity2` fait référence au même assembly en tant que `pwzAssemblyIndentity1`, sauf qu’elle a un numéro de version inférieur, `pfEquivalent` a la valeur `true`. Si `pwzAssemblyIdentity2` fait référence à un numéro de version supérieur, `pfEquivalent` a la valeur `true` uniquement si la valeur de `fUnified2` est `true`.  
  
 Le `pResult` paramètre inclut des informations spécifiques sur la raison pour laquelle les deux assemblys sont considérés comme équivalents ou pas. Pour plus d’informations, consultez [AssemblyComparisonResult, énumération](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions statiques globales de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [AssemblyComparisonResult, énumération](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
