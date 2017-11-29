---
title: "QualifierSet_Delete (fonction) (référence des API non managées)"
description: La fonction QualifierSet_Delete supprime un qualificateur par nom.
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Delete
helpviewer_keywords: QualifierSet_Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9245fc0ee109837249f1f3df400385c117a2f2d7
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetdelete-function"></a>QualifierSet_Delete (fonction)
Supprime un qualificateur spécifié par nom.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`   
[in] Un pointeur vers un [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.

`wszName`   
[in] Le nom du qualificateur de la suppression.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Le `wszName` paramètre n’est pas valide. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | La suppression de ce qualificateur est non conforme. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Le qualificateur spécifié est introuvable. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | Le remplacement local a été supprimé et le qualificateur d’origine de l’objet parent a repris l’étendue. |

## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) (méthode).

En raison des règles de propagation de qualificateur, un qualificateur particulier peut ont été hérité d’un autre objet et simplement remplacé dans l’instance ou la classe actuelle. Dans ce cas, le `QualifierSet_Delete` méthode rétablit le qualificateur de la valeur héritée d’origine. Dans ce cas, la fonction retourne le code d’état `WBEM_S_RESET_TO_DEFAULT`.

## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
