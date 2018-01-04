---
title: "GetObjectText (fonction) (référence des API non managées)"
description: "La fonction GetObjectText retourne un rendu de texte d’un objet dans la syntaxe MOF."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetObjectText
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetObjectText
helpviewer_keywords: GetObjectText function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b47dc73bb9da71b0c8593aa5758179327d7572d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getobjecttext-function"></a>GetObjectText (fonction)
Retourne un rendu de texte de l’objet dans la syntaxe de Format MOF (Managed Object).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre est inutilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.

`lFlags`  
[in] Normalement, 0. Si `WBEM_FLAG_NO_FLAVORS` (ou 0 x 1) est spécifié, les qualificateurs sont incluses sans informations de propagation ou la version.

`pstrObjectText`   
[out] Un pointeur vers un `null` sur ENTRÉE. Moment du retour, qui vient d’être alloué `BSTR` qui contient un rendu de la syntaxe MOF de l’objet.  

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0 x 80041001 | Il a été un échec général. |
|`WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre n’est pas valide. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour terminer l’opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx) (méthode).

Le texte de la structure MOF retourné ne contient pas toutes les informations sur l’objet, mais suffisamment d’informations pour le compilateur MOF être en mesure de recréer l’objet d’origine. Par exemple, aucun qualificateurs propagés ou les propriétés de la classe parent ne sont incluses.

L’algorithme suivant est utilisé pour reconstruire le texte des paramètres d’une méthode :

1. Les paramètres sont resequenced dans l’ordre de leurs valeurs d’identificateur.
1. Les paramètres sont spécifiés en tant que `[in]` et `[out]` sont combinés en un seul paramètre.
 
`pstrObjectText`doit être un pointeur vers un `null` lorsque la fonction est appelée ; il ne doit pas pointer vers une chaîne qui est valide avant l’appel de méthode, car le pointeur n’est pas être libéré.

## <a name="requirements"></a>Configuration requise  
**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
