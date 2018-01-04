---
title: "BlessIWbemServicesObject (fonction) (référence des API non managées)"
description: "La fonction BlessIWbemServicesObject indique si les informations d’identification utilisateur autorisent l’accès à un objet IWbemServices"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BlessIWbemServicesObject
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BlessIWbemServicesObject
helpviewer_keywords: BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2430358e5ea21468c2e975c2a26f20fe801ee546
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject (fonction)
Indique si les informations d’identification utilisateur autorisent l’accès à un [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objet.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>Paramètres

`pIWbemServices`  
[in] Pointeur vers un objet du service WMI.

`strUser`  
[in] Le nom d’utilisateur.

`strPassword`  
[in] Le mot de passe associé `strUser`.

`strAuthority`[in] Le nom de domaine de l’utilisateur. Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.

`impLevel`[in] Le niveau d’emprunt d’identité.

`authnLevel`[in] Le niveau d’autorisation.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WinError.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `E_INVALIDARG` | 0 x 80070057 | Un ou plusieurs arguments ne sont pas valide. |
| `E_POINTER` | 0 x 80004003 | `pIWbemServices` a la valeur `null`. | 
| `E_FAIL` | 0x80000008 | Une erreur non spécifiée s’est produite. |
| `E_OUTOFMEMORY` | 0x80000002 | Mémoire disponible est insuffisante pour effectuer l’opération. | 
| `S_OK` | 0 | L’appel de fonction a réussi. | 

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
