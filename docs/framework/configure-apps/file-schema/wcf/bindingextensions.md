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
# <a name="ltbindingextensionsgt"></a><span data-ttu-id="1b8db-102">&lt;bindingExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="1b8db-102">&lt;bindingExtensions&gt;</span></span>
<span data-ttu-id="1b8db-103">Cette section active l’utilisation d’une liaison définie par l’utilisateur à partir d’un ordinateur ou d’un fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="1b8db-103">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="1b8db-104">Vous pouvez ajouter une liaison définie par l'utilisateur à cette collection en utilisant le mot clé `add` et affecter à l'attribut `type` de l'élément une liaison définie par l'utilisateur, aussi bien que l'attribut `name` au nom de la liaison définie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1b8db-104">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="1b8db-105">Les extensions de liaison permettent à l'utilisateur de créer des liaisons qu'il définit lui-même pour les utiliser dans le cadre d'une configuration de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1b8db-105">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="1b8db-106">Par programme, une extension de liaison est un type qui implémente la classe abstraite <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="1b8db-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="1b8db-107">L'exemple suivant utilise l'élément `add` ainsi que l'attribut `name` pour ajouter une extension de liaison à la section `bindingElementExtensions` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1b8db-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="1b8db-108">Pour ajouter des capacités de configuration à l'élément, l'utilisateur doit écrire et enregistrer un élément `bindingSection`.</span><span class="sxs-lookup"><span data-stu-id="1b8db-108">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="1b8db-109">Pour plus d'informations, consultez la documentation <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="1b8db-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="1b8db-110">Après la définition de l’élément et de son type de configuration, l’extension peut être utilisée comme une partie du point de terminaison comme présenté dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1b8db-110">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>  
    <service name="MyService">  
        <endpoint address="myAddress" binding="MyBinding" />  
    </service>  
</services>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b8db-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b8db-111">See Also</span></span>  
 [<span data-ttu-id="1b8db-112">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="1b8db-112">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
