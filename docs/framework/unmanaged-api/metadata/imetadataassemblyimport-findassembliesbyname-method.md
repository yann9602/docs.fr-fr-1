---
title: "IMetaDataAssemblyImport::FindAssembliesByName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindAssembliesByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3b957430e66e4381a9be33ceb687d7aecba53a4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName, méthode
Obtient un tableau d’assemblys avec l’objet `szAssemblyName` paramètre, à l’aide de règles standard employées par le common language runtime (CLR) pour la résolution des références.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szAppBase`  
 [in] Le répertoire racine dans lequel rechercher l’assembly donné. Si cette valeur est définie sur `null`, `FindAssembliesByName` recherche uniquement dans le global assembly cache de l’assembly.  
  
 `szPrivateBin`  
 [in] Liste des sous-répertoires délimitée par des points-virgules (par exemple, « bin ; bin2 »), sous le répertoire racine, dans laquelle effectuer la recherche de l’assembly. Ces répertoires sont détectés en plus de celles spécifiées dans la valeur par défaut, les règles de détection.  
  
 `szAssemblyName`  
 [in] Le nom de l’assembly à rechercher. Le format de cette chaîne est défini dans la page de référence de classe pour <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 [in] Un tableau de type <<!--zzxref:IUnknown --> `IUnknown`> dans lequel placer le `IMetadataAssemblyImport` des pointeurs d’interface.  
  
 `cMax`  
 [out] Le nombre maximal de pointeurs d’interface qui peut être placée dans `ppIUnk`.  
  
 `pcAssemblies`  
 [out] Le nombre de pointeurs d’interface retourné. Autrement dit, le nombre de pointeurs d’interface réellement placés dans `ppIUnk`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`retourné avec succès.|  
|`S_FALSE`|Il n’existe aucun assembly.|  
  
## <a name="remarks"></a>Remarques  
 Un nom d’assembly, le `FindAssembliesByName` méthode trouve l’assembly en suivant les règles standards pour résoudre les références d’assembly. (Pour plus d’informations, consultez [méthode de localisation des assemblys par le Runtime](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permet à l’appelant de configurer différents aspects du contexte de résolution assembly, tels qu’application chemin de recherche de base et privées.  
  
 Le `FindAssembliesByName` méthode requiert que le CLR soit initialisé dans le processus pour appeler la logique de résolution d’assembly. Par conséquent, vous devez appeler [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (en passant COINITEE_DEFAULT) avant d’appeler `FindAssembliesByName`, puis suivez avec un appel à [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName`Retourne un [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointeur vers le fichier contenant le manifeste d’assembly pour le nom de l’assembly qui est passé. Si le nom de l’assembly donné n’est pas complètement spécifié (par exemple, si elle n’inclut pas de version), plusieurs assemblys peuvent être retournés.  
  
 `FindAssembliesByName`est couramment utilisé par un compilateur qui tente de trouver un assembly référencé au moment de la compilation.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode de localisation des assemblys par le runtime](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [IMetaDataAssemblyImport (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
