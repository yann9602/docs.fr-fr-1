---
title: "Fonction Put (référence des API non managées)"
description: "La fonction Put affecte une nouvelle valeur à une propriété nommée."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Put
helpviewer_keywords: Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c4ad979a3a662618ab62b52d63bda3dbb1e71b9
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="put-function"></a>Fonction Put
Définit une propriété nommée par une nouvelle valeur.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszName`  
[in] Le nom de la propriété. Ce paramètre ne peut pas être `null`.

`lFlags`  
[in] Réservé. Ce paramètre doit être 0.

`pVal`   
[in] Un pointeur vers un élément valide `VARIANT` qui devient la nouvelle valeur de propriété. Si `pVal` est `null` ou pointe vers un `VARIANT` de type `VT_NULL`, la propriété est définie `null`. 

`vtType`  
[in] Le type de `VARIANT` vers lequel pointe `pVal`. Consultez le [notes](#remarks) section pour plus d’informations.
 

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0 x 80041001 | Il a été un échec général. |
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un ou plusieurs paramètres ne sont pas valides. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | Le type de propriété n’est pas reconnu. Cette valeur est retournée lors de la création des instances de classe si la classe existe déjà. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour terminer l’opération. |
| `WBEM_E_TYPE_MISMATCH` | 0 x 80041005 | Pour les instances : indique que `pVal` pointe vers un `VARIANT` d’un type incorrect pour la propriété. <br/> Pour les définitions de classe : la propriété existe déjà dans la classe parente et le nouveau type de COM est différent de l’ancien type COM. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi. |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) (méthode).

Cette fonction remplace toujours la valeur actuelle de la propriété avec un autre. Si le [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointe vers une définition de classe, `Put` crée ou met à jour la valeur de propriété. Lorsque [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointe vers une instance CIM, `Put` met à jour la valeur de propriété uniquement. `Put` Impossible de créer une valeur de propriété.

Le `__CLASS` système propriété est uniquement accessible en écriture lors de la création de la classe, lorsqu’il ne peut pas être vide. Toutes les autres propriétés système sont en lecture seule.

Un utilisateur ne peut pas créer des propriétés dont les noms commencent ou finir par un trait de soulignement (« _ »). Cela est réservé pour les propriétés et les classes du système.

Si la propriété définie le `Put` fonction existe dans la classe parente, la valeur par défaut de la propriété est modifiée, sauf si le type de propriété ne correspond pas au type de classe parent. Si la propriété n’existe pas et il n’est pas une incompatibilité de type, la propriété est ceated.

Utilisez le `vtType` paramètre uniquement lorsque vous créez de nouvelles propriétés dans une définition de classe CIM et `pVal` est `null` ou pointe vers un `VARIANT` de type `VT_NULL`. Dans ce cas, le `vType` paramètre spécifie le type CIM de la propriété. Dans tous les autres cas, `vtType` doit être 0. `vtType`doit également être 0 si l’objet sous-jacent est une instance (même si `Val` est `null`), car le type de la propriété est fixe et ne peut pas être modifié.   

## <a name="example"></a>Exemple

Pour obtenir un exemple, consultez la [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) (méthode).

## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
