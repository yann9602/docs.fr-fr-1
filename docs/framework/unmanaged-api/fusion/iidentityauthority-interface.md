---
title: IIdentityAuthority, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IIdentityAuthority
api_location: fusion.dll
api_type: COM
f1_keywords: IIdentityAuthority
helpviewer_keywords: IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3f38d932fa0376186e2c22232d21857d5fa128f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority, interface
Gère les clés d’identité pour les objets de code.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|Obtient une valeur qui indique si les deux spécifiés [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances sont égales.|  
|`IIdentityAuthority::AreReferencesEqual`|Obtient une valeur qui indique si les deux spécifiés [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances sont égales.|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Obtient une valeur qui indique si les deux représentations sous forme de chaîne spécifiée définition identity sont égaux.|  
|`IIdentityAuthority::AreTextualReferencesEqual`|Obtient une valeur qui indique si les deux représentations sous forme de chaîne spécifiée référence identité sont égaux.|  
|`IIdentityAuthority::CreateDefinition`|Obtient un pointeur vers un nouveau `IDefinitionIdentity` instance qui représente l’objet de code dans la portée actuelle.|  
|`IIdentityAuthority::CreateReference`|Obtient un pointeur vers un nouveau `IReferenceIdentity` instance qui représente l’objet de code dans la portée actuelle.|  
|`IIdentityAuthority::DefinitionToText`|Obtient une version de la chaîne mise en forme du `IDefinitionIdentity`.|  
|`IIdentityAuthority::DefinitionToTextBuffer`|Remplit la mémoire tampon de caractères larges spécifié avec une version de chaîne de l’objet `IDefinitionIdentity`.|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|Obtient une valeur qui indique si le texte spécifié `IDefinitionIdentity` et `IReferenceIdentity` instances font référence au même objet de code.|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Obtient une valeur qui indique si les chaînes spécifiées font référence au même objet de code.|  
|`IIdentityAuthority::GenerateDefinitionKey`|Obtient un pointeur vers une clé de chaîne qui vient d’être créée pour spécifié `IDefinitionIdentity`.|  
|`IIdentityAuthority::GenerateReferenceKey`|Obtient un pointeur vers une clé de chaîne qui vient d’être créée pour spécifié `IReferenceIdentity`.|  
|`IIdentityAuthority::HashDefinition`|Obtient une valeur de hachage spécifié `IDefinitionIdentity`.|  
|`IIdentityAuthority::HashReference`|Obtient une valeur de hachage spécifié `IreferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToText`|Obtient une version de la chaîne mise en forme du `IReferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToTextBuffer`|Remplit la mémoire tampon de caractères larges spécifié avec une version de chaîne de l’objet `IReferenceIdentity`.|  
|`IIdentityAuthority::TextToDefinition`|Obtient un pointeur d’interface vers un `IDefinitionIdentity` instance générée à partir de la chaîne de mise en forme.|  
|`IIdentityAuthority::TextToReference`|Obtient un pointeur d’interface vers un `IReferenceIdentity` instance générée à partir de la chaîne de mise en forme.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Isolation.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
