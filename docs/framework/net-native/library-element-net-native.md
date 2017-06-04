---
title: "&lt;Library&gt;, &#233;l&#233;ment (.NET Native) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# &lt;Library&gt;, &#233;l&#233;ment (.NET Native)
Définit l'assembly qui contient des types et des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.  
  
## Syntaxe  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Name`|Attribut requis.  Spécifie le nom d'un assembly.  Les éléments enfants de cet élément `<Library>` définissent la stratégie de réflexion runtime pour les types et membres de type se trouvant dans cet assembly.|  
  
## Name \(attribut\)  
  
|Valeur|Description|  
|------------|-----------------|  
|*assembly\_name*|Nom simple de l'assembly, sans son extension de fichier.  Cet attribut correspond à la propriété <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=fullName>.  Par exemple, le nom d'un assembly nommé Extensions.dll est « Extensions ».  Consultez la section Notes pour une forme particulière d'*assembly\_name* qui prend en charge l'inclusion conditionnelle de métadonnées à partir de l'assembly.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Assembly\>](../../../docs/framework/net-native/assembly-element-net-native.md)|Applique la stratégie à tous les types d'un assembly particulier.|  
|[\<Namespace\>](../../../docs/framework/net-native/namespace-element-net-native.md)|Applique la stratégie à tous les types d'un espace de noms particulier.|  
|[\<Type\>](../../../docs/framework/net-native/type-element-net-native.md)|Applique la stratégie à un type particulier, tel qu'une classe ou une structure.|  
|[\<TypeInstantiation\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Applique la stratégie à un type générique construit.  Par exemple, vous pouvez utiliser un élément [\<TypeInstantiation\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)pour définir une stratégie pour un type `List<String>`.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Directives\>](../../../docs/framework/net-native/directives-element-net-native.md)|Élément racine d'un fichier de directives de runtime.|  
  
## Notes  
 L'élément [\<Directives\>](../../../docs/framework/net-native/directives-element-net-native.md) peut contenir zéro, un ou plusieurs éléments `<Library>`.  
  
 L'élément `<Library>` sert de conteneur pour la définition des éléments de programme dont les métadonnées sont nécessaires au moment de l'exécution ; cet élément n'exprime pas la stratégie.  Au moment de la compilation, les outils du compilateur recherchent uniquement dans la bibliothèque désignée par l'élément `<Library>` les éléments de programme identifiés par ses éléments enfants.  En revanche, les outils du compilateur recherchent dans toutes les bibliothèques, y compris les bibliothèques principales du Framework .NET, les éléments de programme identifiés par les éléments enfants de l'élément [\<Application\>](../../../docs/framework/net-native/application-element-net-native.md).  
  
 Les directives `<Library>` peuvent être utilisées de manière conditionnelle.  Si le nom de l'élément `<Library>` commence et se termine par un astérisque \(\*\), la directive `<Library>` n'a d'effet que si l'assembly spécifié entre les astérisques est référencé par l'application.  Par exemple, la directive runtime suivante ne s'applique que si l'assembly Utillities.dll est référencé par l'application.  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name=”*Utilities*”>  
   ...  
  </Library>  
</Directives>  
  
```  
  
## Voir aussi  
 [\<Application\>, élément](../../../docs/framework/net-native/application-element-net-native.md)   
 [\<Directives\>, élément](../../../docs/framework/net-native/directives-element-net-native.md)   
 [Guide de référence du fichier de configuration des directives runtime \(rd.xml\)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Éléments de directive runtime](../../../docs/framework/net-native/runtime-directive-elements.md)