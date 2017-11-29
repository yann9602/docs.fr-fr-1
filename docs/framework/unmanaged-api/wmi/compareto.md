---
title: "CompareTo (fonction) (référence des API non managées)"
description: "La fonction CompareTo compare un objet à un autre objet WMI."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CompareTo
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CompareTo
helpviewer_keywords: CompareTo function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dacb1516bebfc73ae9e16b03f3755ab49382e571
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="compareto-function"></a>CompareTo (fonction)
Compare un objet à un autre objet de gestion de Windows.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`flags`  
[in] Combinaison de bits des indicateurs qui spécifient les caractéristiques de l’objet à prendre en compte pour la comparaison. Consultez le [notes](#remarks) section pour plus d’informations.

`pCompareTo`  

[in] L’objet de comparaison. `pcompareTo`doit être un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance ; elle ne peut pas être `null`.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0 x 80041001 | Une erreur non spécifiée s’est produite. |
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Un deuxième appel à `BeginEnumeration` a été effectuée sans appel intermédiaire à [ `EndEnumeration` ](endenumeration.md). |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Les objets sont différents. |
| `WBEM_S_SAME` | 0 | Les objets sont identiques selon les indicateurs de comparaison. |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) (méthode).

Les indicateurs qui peuvent être passés en tant que le `lEnumFlags` argument sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code. Vous pouvez spécifier les caractéristiques individuelles impliquées dans la comparaison en spécifiant une combinaison au niveau du bit des indicateurs suivants :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Ignorer la source (le serveur et l’espace de noms que dont elles proviennent). |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | Ignorer tous les qualificateurs (y compris **clé** et **dynamique**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Ignorer les valeurs par défaut des propriétés. Cet indicateur s’applique uniquement à la comparaison des classes. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0 x 20 | Ignorer les versions de qualificateur. Cet indicateur toujours qualificateurs en tenant compte, mais ignore les distinctions de version tels que les règles de propagation et remplace les restrictions. |
| `WBEM_FLAG_IGNORE_CASE` | 0 x 10 | Ignorer la casse lors de la comparaison des valeurs de chaîne. Cela s’applique à la fois pour les chaînes et valeurs de qualificateur. La comparaison des noms de propriété et le qualificateur est toujours la casse, même si cet indicateur est défini. |
| `WBEM_FLAG_IGNORE_CLASS` | 0 x 8 | Supposons que les objets comparés sont des instances de la même classe. Par conséquent, cet indicateur compare uniquement des informations relatives aux instances. Utilisez cette indicateurs pour optimiser les performances. Si les objets ne sont pas de la même classe, les résultats sont indéfinis. |

Ou vous pouvez spécifier un seul indicateur composite comme suit :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Prendre en compte toutes les fonctionnalités dans la comparaison. |

## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
