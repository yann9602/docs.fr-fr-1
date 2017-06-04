---
title: "&lt;Directives&gt;, &#233;l&#233;ment (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# &lt;Directives&gt;, &#233;l&#233;ment (.NET Native)
Élément racine de chaque fichier de directives runtime pour [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **\<Directives xmlns\="http:\/\/schemas.microsoft.com\/netfx\/2013\/01\/metadata"\>**  
  
## Syntaxe  
  
```xml  
  
        <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`xmlns`|Espace de noms XML.  Sa valeur est toujours **"http:\/\/schemas.microsoft.com\/netfx\/2013\/01\/metadata"**.|  
  
## Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Application\>](../../../docs/framework/net-native/application-element-net-native.md)|Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion.|  
|[\<Library\>](../../../docs/framework/net-native/library-element-net-native.md)|Définit l'assembly dont les types enfants et les membres de type nécessitent des métadonnées au moment de l'exécution.|  
  
## Notes  
 Chaque fichier de directives runtime ne peut contenir qu'un seul élément `<Directives>`.  
  
 L'élément `<Directives>` peut contenir zéro ou un élément [\<Application\>](../../../docs/framework/net-native/application-element-net-native.md), ainsi que zéro, un ou plusieurs éléments [\<Library\>](../../../docs/framework/net-native/library-element-net-native.md).  
  
## Voir aussi  
 [Guide de référence du fichier de configuration des directives runtime \(rd.xml\)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Éléments de directive runtime](../../../docs/framework/net-native/runtime-directive-elements.md)