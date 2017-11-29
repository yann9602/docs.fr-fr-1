---
title: "WritePropertyValue (fonction) (référence des API non managées)"
description: "La fonction WritePropertyValue écrit les octets à une propriété."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: WritePropertyValue
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: WritePropertyValue
helpviewer_keywords: WritePropertyValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26337a13ab9840b79c253d4af2d84a10e70877c5
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue (fonction)
Écrit un nombre spécifié d’octets à une propriété identifiée par un descripteur de propriété.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.

`lHandle`  
[in] Entier qui contient le descripteur qui identifie cette propriété. Le handle peut être récupéré en appelant le [GetPropertyHandle](getpropertyhandle.md) (fonction).   

`lNumBytes`  
[in] Le nombre d’octets écrits dans la propriété. Consultez le [notes](#remarks) section pour plus d’informations.

`pHandle`   
[out] Pointeur vers le tableau d’octets qui contient les données.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre n’est pas valide. |
|`WBEM_E_TYPE_MISMATCH` | 0 x 80041005 | Une incompatibilité de type s’est produite. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx) (méthode).

Utilisez cette fonction pour définir une chaîne et tous les autres non -`DWORD` ou non-`QWORD` données.

Pour les valeurs de propriété de chaîne, `lNumBytes` doit être la taille des données correct du type de propriété spécifié. Pour les valeurs de propriété de chaîne, `lNumBytes` doit être la longueur de la chaîne spécifiée en octets et la chaîne lui-même doit être de même longueur en octets et être suivie d’un caractère de fin de la valeur null.

## <a name="requirements"></a>Spécifications  
**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
