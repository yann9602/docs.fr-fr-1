---
title: "PutMethod (fonction) (référence des API non managées)"
description: "La fonction PutMethod crée une méthode."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutMethod
helpviewer_keywords: PutMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 64e43165b34b74540931b308100c9ca942946bcf
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="putmethod-function"></a>PutMethod (fonction)
Crée une méthode.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`wszName`  
[in] Le nom de la méthode à créer. 

`lFlags`  
[in] Réservé. Ce paramètre doit être 0.

`pSignatureIn`  
[in] Un pointeur vers une copie de la [classe __Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) qui contient le `in` paramètres de méthode. Ce paramètre est ignoré si la valeur `null`.  

`pSignatureOut`  
[in]  Un pointeur vers une copie de la [classe __Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) qui contient le `out` paramètres de méthode. Ce paramètre est ignoré si la valeur `null`.
 

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un ou plusieurs paramètres ne sont pas valides. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | Le `[in, out]` paramètre de méthode spécifié à la fois dans le *pInSignature* et *pOutSignature* objets ont des qualificateurs différents.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Il manque la spécification d’un paramètre de méthode le **ID** qualificateur. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | La série d’ID qui est attribuée aux paramètres de méthode n’est pas consécutif ou n’a pas été commencent à 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | La valeur de retour pour une méthode a un **ID** qualificateur. |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Une tentative a été effectuée pour réutiliser un nom de méthode existant à partir d’une classe parente, et les signatures ne correspondent pas. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi. |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) (méthode).

Cet appel de méthode n’est possible que si `ptr` est une définition de classe CIM. Manipulation de la méthode n’est pas disponible à partir de [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) pointeurs qui pointent vers les instances CIM.

Les utilisateurs ne peuvent pas créer des méthodes dont les noms commencent ou finir par un trait de soulignement. Cela est réservé pour les propriétés et les classes du système.

Pour une méthode, le `in` et `out` paramètres sont décrits en tant que propriétés dans [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objets.

Un `[in/out]` paramètre peut être défini par l’ajout de la même propriété pour les deux objets pointés par le `pInSignature` et `pOutSignature` paramètres. Dans ce cas, les propriétés de partagent le même **ID** valeur du qualificateur.

Chaque propriété dans un [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) objet de classe autre que `ReturnValue` doit avoir un **ID** qualificateur, une valeur numérique de base zéro qui identifie l’ordre dans lequel les paramètres apparaissent. Aucun deux paramètres ne peuvent avoir le même **ID** valeur et non **ID** valeur peut être ignorée. Si des conditions se produit, le `PutMethod` fonction renvoie `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Exemple

Pour obtenir un exemple, consultez la [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) (méthode).

## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
