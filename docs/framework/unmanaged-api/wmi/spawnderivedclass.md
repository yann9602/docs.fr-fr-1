---
title: "SpawnDerivedClass (fonction) (référence des API non managées)"
description: "La fonction SpawnDerivedClass crée un nouvel objet qui dérive d’un objet."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SpawnDerivedClass
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SpawnDerivedClass
helpviewer_keywords: SpawnDerivedClass function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51a0dd0013b1bb3898bcc81ee2d64be20a5b6ecc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass (fonction)
Crée un objet de classe qui vient d’être dérivée d’un objet spécifié.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`lFlags`  
[in] Réservé. Ce paramètre doit être 0.

`ppNewClass`  
[out] Reçoit le pointeur vers le nouvel objet de définition de classe. Si une erreur se produit, un nouvel objet n’est pas renvoyé, et `ppNewClass` non de gauche est modifié. Sa valeur ne peut pas être `null`.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0 x 80041001 | Il a été un échec général. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Une opération non valide, telles que la génération d’une classe à partir d’une instance, a été demandée. |
| `WBEM_E_INCOMPLETE_CLASS` | La classe source n’a pas complètement a été définie ou inscrits avec la gestion de Windows, pour une nouvelle classe dérivée n’est pas autorisée. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour terminer l’opération. |
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | `ppNewClass` a la valeur `null`. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) (méthode).

`ptr`doit être une définition de classe qui devient la classe parente de l’objet généré. L’objet retourné est une sous-classe de l’objet actuel.

Le nouvel objet retourné dans `ppNewClass` devient automatiquement une sous-classe de l’objet actuel. Ce comportement ne peut pas être substitué. Il n’existe aucune autre méthode par laquelle les sous-classes (classes dérivées) peuvent être créés.

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
