---
title: "QualifierSet_Put (fonction) (référence des API non managées)"
description: "La fonction QualifierSet_Put écrit qualificateur nommé et sa valeur."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Put
helpviewer_keywords: QualifierSet_Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bf5c6dbf0f707942d58f4d7cf155636f0532724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetput-function"></a>QualifierSet_Put (fonction)
Écrit la valeur et le qualificateur nommé. Le nouveau qualificateur remplace la valeur précédente du même nom. Si le qualificateur n’existe pas, il est créé. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`   
[in] Ce paramètre est inutilisé.

`ptr`   
[in] Un pointeur vers un [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.

`wszName`   
[in] Le nom du qualificateur à écrire.

`pVal`[in] Un pointeur vers un élément valide `VARIANT` qui contient le qualificateur à écrire. Ce paramètre ne peut pas être `null`.

`lFlavor`[in] Une des constantes suivantes qui définit les versions de qualificateur souhaité pour ce qualificateur. La valeur par défaut est `WBEM_FLAVOR_OVERRIDABLE` (0).

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | Le qualificateur peut être substitué dans une classe dérivée ou une instance. **Il s’agit de la valeur par défaut.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | Le qualificateur est propagé aux instances. |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | Le qualificateur est propagé aux classes dérivées. |
| ' WBEM_FLAVOR_NOT_OVERRIDABLE | 0 x 10 | Le qualificateur ne peut pas être écrasé dans une classe ou une instance dérivée. |
| ' WBEM_FLAVOR_AMENDED | 0 x 80 | Le qualificateur est localisé. |

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Une tentative non conforme pour spécifier le **clé** qualificateur sur une propriété qui ne peut pas être une clé. Les clés sont spécifiées om c ; définition ass d’un objet et ne peut pas être modifié sur chaque instance. |
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | Le `pVal` paramètre n’est pas un type de qualificateur autorisé. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Il n’est pas possible d’appeler le `QualifierSet_Put` méthode sur le qualificateur, car l’objet propriétaire n’autorise pas les remplacements. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) (méthode).

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
