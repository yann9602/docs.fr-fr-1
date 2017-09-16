---
title: "&lt;Directives&gt;, élément (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9305af8d241315fb3da9c0bfc487213a44213115
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="ltdirectivesgt-element-net-native"></a>&lt;Directives&gt;, élément (.NET Native)
Élément racine de chaque fichier de directives runtime pour [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **\<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
      <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`xmlns`|Espace de noms XML. Sa valeur est toujours **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.|  
  
## <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Définit l'assembly dont les types enfants et les membres de type nécessitent des métadonnées au moment de l'exécution.|  
  
## <a name="remarks"></a>Remarques  
 Chaque fichier de directives runtime ne peut contenir qu'un seul élément `<Directives>`.  
  
 L’élément `<Directives>` peut contenir zéro ou un élément [\<Application>](../../../docs/framework/net-native/application-element-net-native.md), ainsi que zéro, un ou plusieurs éléments [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de fichier de configuration de directives runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Éléments de directive runtime](../../../docs/framework/net-native/runtime-directive-elements.md)

