---
title: "GetPropertyQualifierSet (fonction) (référence des API non managées)"
description: "La fonction GetPropertyQualifierSet récupère le qualificateur d’une propriété."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyQualifierSet
helpviewer_keywords: GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ca2981c8833abaafd5d206b66d6e91f34e2c91d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getpropertyqualifierset-function"></a>GetPropertyQualifierSet (fonction)
Récupère le qualificateur définie pour une propriété particulière.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszMethod`  
[in] Le nom de propriété. `wszProperty`doit pointer vers un valide `LPCWSTR`. 

`ppQualSet`  
[out] Reçoit le pointeur d’interface qui autorise l’accès pour les qualificateurs de la propriété. `ppQualSet` ne peut pas avoir la valeur `null`. Si une erreur se produit, un nouvel objet n’est pas retourné, et le pointeur est défini pour pointer vers `null`. 

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0 x 80041001 | Il a été un échec général. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | La méthode spécifiée n’existe pas. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour terminer l’opération. |
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre est `null`. |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | La fonction tente d’obtenir des qualificateurs d’une propriété système. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) (méthode). 

Un appel à cette fonction est prise en charge uniquement si l’objet actuel est une définition de classe CIM. Manipulation de la méthode n’est pas disponible pour [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters qui pointent vers les instances CIM.

Étant donné que chaque méthode peut avoir son propre qualificateurs, le [IWbemQualifierSet pointeur](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) permet d’ajouter, modifier ou supprimer ces qualificateurs de l’appelant.

Dans la mesure où les propriétés système n’ont des qualificateurs d’aucun, la fonction retourne `WBEM_E_SYSTEM_PROPERTY` si vous tentez d’obtenir un [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) pointeur pour une propriété système.

## <a name="requirements"></a>Configuration requise  
**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
