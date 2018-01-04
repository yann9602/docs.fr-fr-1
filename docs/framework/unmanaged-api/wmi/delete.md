---
title: "Supprimer la fonction (référence des API non managées)"
description: "La fonction Delete supprime la propriété spécifiée et tous ses qualificateurs à partir d’une définition de classe CIM."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Delete
helpviewer_keywords: Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30f5bf651990cafe06811019cf2b3d92f866f646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="delete-function"></a>Supprimer (fonction)
Supprime la propriété spécifiée et tous ses qualificateurs d’une définition de classe CIM.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszName`  
[in] Le nom de la propriété à supprimer. `wszName`doit être un pointeur vers une valide `LPCWSTR`.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0 x 80041001 | Une erreur non spécifiée s’est produite. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | La propriété ne peut pas être supprimée. |
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | `wszzName` n'est pas valide. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | La propriété spécifiée n’existe pas. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Il n’est pas suffisamment de mémoire pour terminer l’opération. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | La propriété est héritée d’une classe de base. |
| `WBEM_E_SYSTEM_PROPERTY` | | La propriété est une propriété système. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | La fonction supprimée d’une valeur par défaut de remplacement pour la classe actuelle. La valeur par défaut pour cette propriété dans la classe parente a été reactiviated. | 

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx) (méthode).

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
