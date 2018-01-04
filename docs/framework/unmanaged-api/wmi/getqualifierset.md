---
title: "GetQualifierSet (fonction) (référence des API non managées)"
description: "La fonction GetQualifierSet récupère le qualificateur définie pour une classe ou instance."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetQualifierSet
helpviewer_keywords: GetQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 127e7862d0cb0d204e91cd5ee36f2d32f1453a8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getqualifierset-function"></a>GetQualifierSet (fonction)
Récupère le qualificateur définie pour une instance de classe ou une définition de classe.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`ppQualSet`  
[out] Reçoit le pointeur d’interface qui autorise l’accès pour les qualificateurs de l’objet de classe. `ppQualSet` ne peut pas avoir la valeur `null`. Si une erreur se produit, un nouvel objet n’est pas retourné, et que le pointeur reste inchangée. 

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0 x 80041001 | Il a été un échec général. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | La méthode spécifiée n’existe pas. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour terminer l’opération. |
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre est `null`. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::GetQualifierSet](https://msdn.microsoft.com/library/aa391451(v=vs.85).aspx) (méthode). 

Le [IWbemQualifierSet pointeur](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) permet d’ajouter, modifier ou supprimer ces qualificateurs de l’appelant. Ces qualificateurs ajoutés, modifiés ou supprimés s’appliquent à la définition de classe ou instance entière.

## <a name="requirements"></a>Configuration requise  
**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
