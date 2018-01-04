---
title: "FormatFromRawValue (fonction) (référence des API non managées)"
description: "La fonction FormatFromRawValue convertit les données de performances brutes dans un format spécifié."
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: FormatFromRawValue
api_location: PerfCounter.dll
api_type: DLLExport
f1_keywords: FormatFromRawValue
helpviewer_keywords: FormatFromRawValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3daa89ec0b40bb9c08898ecd682f05f0f0ce09a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue (fonction)
Convertit une valeur de données de performances brutes au format spécifié, ou les deux valeurs de données de performances brutes si la conversion de format est basé sur le temps.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```  

## <a name="parameters"></a>Paramètres

`dwCounterType`  
[in] Le type de compteur. Pour obtenir la liste des types de compteurs, consultez [WMI Performance Counter Types](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx). `dwCounterType`peut être n’importe quel type de compteur à l’exception de `PERF_LARGE_RAW_FRACTION` et `PERF_LARGE_RAW_BASE`. 

`dwFormat`  
[in] Le format dans lequel convertir les données de performances brutes. Il peut prendre l’une des valeurs suivantes :

|Constante  |Value  |Description |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Retourne la valeur calculée comme une valeur à virgule flottante double précision. | 
| `PDH_FMT_LARGE` | 0x00000400 | Retourne la valeur calculée sous forme d’entier 64 bits. |
| `PDH_FMT_LONG` | 0x00000100 | Retourne la valeur calculée sous forme d’entier 32 bits. |

Une des valeurs précédentes peut être dissocié avec l’un des indicateurs de mise à l’échelle suivants :

|Constante  |Value  |Description |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Ne pas appliquer les facteurs d’échelle du compteur. |
| `PDH_FMT_1000` | 0x00002000 | Multipliez la valeur finale par 1 000. | 

`pTimeBase`  
[in] Pointeur vers la base de temps, si nécessaire pour la conversion de format. Si les informations de base de temps ne sont pas nécessaires pour la conversion de format, la valeur de ce paramètre est ignorée.

`pRawValue1`[in] Un pointeur vers un [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure qui représente une valeur de performance brute.

`pRawValue2`[in] Un pointeur vers un [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure qui représente une seconde valeur de performance brute. Si une seconde valeur de performance brute n’est pas nécessaire, ce paramètre doit être `null`.

`pFmtValue`[out] Un pointeur vers un [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) structure qui reçoit la valeur de performance de mise en forme.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes sont retournées par cette fonction :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | L’appel de fonction a réussi. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Un argument requis est manquant ou incorrect. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Le handle n’est pas un objet PDH valide. |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) (fonction).

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Bibliothèque :** PerfCounter.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
