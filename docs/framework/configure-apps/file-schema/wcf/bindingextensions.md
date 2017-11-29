---
title: '&lt;bindingExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c02af972ad52119af07da404a61fd3afc0facbeb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltbindingextensionsgt"></a>&lt;bindingExtensions&gt;
Cette section active l’utilisation d’une liaison définie par l’utilisateur à partir d’un ordinateur ou d’un fichier de configuration de l’application. Vous pouvez ajouter une liaison définie par l'utilisateur à cette collection en utilisant le mot clé `add` et affecter à l'attribut `type` de l'élément une liaison définie par l'utilisateur, aussi bien que l'attribut `name` au nom de la liaison définie par l'utilisateur.  
  
 Les extensions de liaison permettent à l'utilisateur de créer des liaisons qu'il définit lui-même pour les utiliser dans le cadre d'une configuration de point de terminaison. Par programme, une extension de liaison est un type qui implémente la classe abstraite <xref:System.ServiceModel.Channels.Binding>.  
  
 L'exemple suivant utilise l'élément `add` ainsi que l'attribut `name` pour ajouter une extension de liaison à la section `bindingElementExtensions` du fichier de configuration.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingExtensions>  
           <add name="MyBinding" type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Pour ajouter des capacités de configuration à l'élément, l'utilisateur doit écrire et enregistrer un élément `bindingSection`. Pour plus d'informations, consultez la documentation <xref:System.Configuration>.  
  
 Après la définition de l’élément et de son type de configuration, l’extension peut être utilisée comme une partie du point de terminaison comme présenté dans l’exemple suivant.  
  
```xml  
<services>  
    <service name="MyService">  
        <endpoint address="myAddress" binding="MyBinding" />  
    </service>  
</services>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)
