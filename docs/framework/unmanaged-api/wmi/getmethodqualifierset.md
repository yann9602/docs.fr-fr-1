---
title: "GetMethodQualifierSet (fonction) (référence des API non managées)"
description: "La fonction GetMethodQualifierSet récupère le jeu de qualificateurs d’une méthode."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodQualifierSet
helpviewer_keywords: GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2999bef31576cf2bc025868260c2b1782a9b69f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getmethodqualifierset-function"></a>GetMethodQualifierSet (fonction)
Récupère le qualificateur défini pour une méthode particulière.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszMethod`  
[in] Le nom de la méthode. `wszMethod`doit pointer vers un valide `LPCWSTR`. 

`ppQualSet`  
[out] Reçoit le pointeur d’interface qui autorise l’accès pour les qualificateurs de la méthode. `ppQualSet` ne peut pas avoir la valeur `null`. Si une erreur se produit, un nouvel objet n’est pas retourné, et le pointeur est défini pour pointer vers `null`. 

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | La méthode spécifiée n’existe pas. |
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre est `null`. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) (méthode). 

Un appel à cette fonction est prise en charge uniquement si l’objet actuel est une définition de classe CIM. Manipulation de la méthode n’est pas disponible pour [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters qui pointent vers les instances CIM.

Étant donné que chaque méthode peut avoir son propre qualificateurs, le [IWbemQualifierSet pointeur](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) permet d’ajouter, modifier ou supprimer ces qualificateurs de l’appelant.

## <a name="requirements"></a>Configuration requise  
**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
