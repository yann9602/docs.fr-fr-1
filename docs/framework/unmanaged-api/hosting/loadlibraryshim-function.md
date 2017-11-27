---
title: LoadLibraryShim, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LoadLibraryShim
helpviewer_keywords: LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c56f5a3576c505fd7b7d514e3f2d038e7f8f3ecc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim, fonction
Charge une version spécifiée d’une DLL qui est incluse dans le package redistribuable .NET Framework.  
  
 Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Utilisez le [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szDllName`  
 [in] Chaîne terminée par zéro qui représente le nom de la DLL doit être chargé à partir de la bibliothèque .NET Framework.  
  
 `szVersion`  
 [in] Chaîne terminée par zéro qui représente la version de la DLL à charger. Si `szVersion` est null, la version sélectionnée pour charger est la version la plus récente de la DLL spécifiée est inférieure à la version 4. Autrement dit, toutes les versions égales ou supérieures à la version 4 sont ignorées si `szVersion` a la valeur null, et si aucune version inférieure à la version 4 n’est installé, la DLL ne peut pas charger. Il s’agit de garantir que l’installation de le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] n’affecte pas des applications existantes ou des composants. Consultez l’entrée [côte à côte In-Process et le démarrage rapide de Migration](http://go.microsoft.com/fwlink/?LinkId=200329) dans le blog de l’équipe CLR.  
  
 `pvReserved`  
 Réservé à un usage ultérieur.  
  
 `phModDll`  
 [out] Pointeur vers le handle du module.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur de modèle COM (Component Object) standard, tel que défini dans WinError.h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|CLR_E_SHIM_RUNTIMELOAD|Chargement `szDllName` requiert le chargement, le common language runtime (CLR) et la version nécessaire du CLR ne peut pas être chargé.|  
  
## <a name="remarks"></a>Remarques  
 Cette fonction est utilisée pour charger les DLL qui sont inclus dans le package redistribuable .NET Framework. Il ne charge pas les DLL générées par l’utilisateur.  
  
> [!NOTE]
>  À compter de .NET Framework version 2.0, en chargeant Fusion.dll provoque le CLR à charger. Il s’agit, car les fonctions dans le fichier Fusion.dll sont maintenant des wrappers dont les implémentations sont fournies par le runtime.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
