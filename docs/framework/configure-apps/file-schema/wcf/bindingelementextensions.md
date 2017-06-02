---
title: "&lt;bindingElementExtensions&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;bindingElementExtensions&gt;
Cette section active l'utilisation d'un élément de liaison personnalisé à partir d'un ordinateur ou d'un fichier de configuration de l'application.  Vous pouvez ajouter un élément de liaison personnalisé à cette collection en utilisant le mot clé `add` et affecter à l'attribut `type` de l'élément une extension d'élément de liaison, ainsi que l'attribut `name` à l'élément de liaison personnalisé.  
  
 Les extensions de liaison permettent la création d'éléments de liaison définis par l'utilisateur à utiliser dans le cadre de liaisons personnalisées.  Par programme, une extension de liaison est un type qui implémente la classe abstraite <xref:System.ServiceModel.Channels.BindingElement>.  Dans le fichier de configuration, la section `bindingElementExtensions` est utilisée pour définir un élément d'extension.  
  
 L'exemple suivant utilise l'élément `add` ainsi que l'attribut `name` pour ajouter une extension de liaison à la section `bindingElementExtensions` du fichier de configuration.  
  
```  
<system.serviceModel>  
    <extensions>  
        <bindingElementExtensions>  
           <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingElementExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Pour ajouter des capacités de configuration à l'élément, l'utilisateur doit écrire et enregistrer un élément `bindingElementExtensionSection`.  Pour plus d'informations, consultez la documentation <xref:System.Configuration>.  
  
 Après la définition de l'élément et de son type de configuration, l'extension peut être utilisée comme une partie de la liaison personnalisée telle que présentée dans l'exemple suivant.  
  
```  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)