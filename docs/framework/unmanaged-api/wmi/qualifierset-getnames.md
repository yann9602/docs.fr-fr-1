---
title: "QualifierSet_GetNames (fonction) (référence des API non managées)"
description: "La fonction QualifierSet_GetNames récupère les noms des qualificateurs d’un objet ou une propriété."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_GetNames
helpviewer_keywords: QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6077b448c2644f68d12679cf208ee921c2af119a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetgetnames-function"></a>QualifierSet_GetNames (fonction)
Récupère les noms de tous les qualificateurs ou de certains qualificateurs qui sont disponibles à partir de l’objet en cours ou de la propriété. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`   
[in] Ce paramètre est inutilisé.

`ptr`   
[in] Un pointeur vers un [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.

`lFlags`   
[in] Un des indicateurs ou des valeurs qui spécifie les noms à inclure dans l’énumération suivante.

|Constante  |Value  |Description  |
|---------|---------|---------|
|  | 0 | Retourner les noms de tous les qualificateurs. |
| `WBEM_FLAG_LOCAL_ONLY` | 0 x 10 | Retourner uniquement les noms des qualificateurs spécifiques à l’objet ou la propriété actuelle. <br/> Pour une propriété : retourner uniquement les qualificateurs spécifiques à la propriété (y compris les substitutions), et pas ces qualificateurs propagés à partir de la définition de classe. <br/> Pour une instance : retourner uniquement des noms spécifiques à l’instance qualificateur. <br/> Pour une classe : retourner uniquement les qualificateurs spécifiques à la beiong de la classe dérivée.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0 x 20 | Retourne uniquement les noms des qualificateurs propagés à partir d’un autre objet. <br/> Pour une propriété : retour uniquement les qualificateurs propagées à cette propriété à partir de la définition de classe et non celles de la propriété proprement dite. <br/> Pour une instance : retour uniquement ces qualificateurs propagés à partir de la définition de classe. <br/> Pour une classe : retour uniquement les noms de qualificateur héritées des classes parentes. |

`pstrNames`[out] Un nouveau `SAFEARRAY` qui contient les noms demandés. Le tableau peut avoir 0 éléments. Si une erreur se produit, un nouveau `SAFEARRAY` n’est pas renvoyé.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre n’est pas valide. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour commencer une nouvelle énumération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) (méthode).

Une fois que vous avez extrait les noms de qualificateur, vous pouvez accéder à chaque qualificateur par nom, en appelant le [QualifierSet_Get](qualifierset-get.md) (fonction). 

Il n’est pas une erreur d’un objet donné pour que les qualificateurs de zéro, par conséquent, le nombre de chaînes dans `pstrNames` en retour peut être 0, même si la fonction retourne `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
