---
title: "&lt;élément persistableType&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3064727eeda30c05f38558f4f0977c71e5abb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="362c9-102">&lt;élément persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="362c9-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="362c9-103">Spécifie tous les types persistants.</span><span class="sxs-lookup"><span data-stu-id="362c9-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="362c9-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="362c9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="362c9-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="362c9-105">\<comContracts></span></span>  
<span data-ttu-id="362c9-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="362c9-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="362c9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="362c9-107">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="type"></a><span data-ttu-id="362c9-108">Type</span><span class="sxs-lookup"><span data-stu-id="362c9-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="362c9-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="362c9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="362c9-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="362c9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="362c9-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="362c9-111">Attributes</span></span>  
  
|<span data-ttu-id="362c9-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="362c9-112">Attribute</span></span>|<span data-ttu-id="362c9-113">Description</span><span class="sxs-lookup"><span data-stu-id="362c9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="362c9-114">id</span><span class="sxs-lookup"><span data-stu-id="362c9-114">id</span></span>|<span data-ttu-id="362c9-115">Attribut requis qui contient une chaîne spécifiant un identificateur unique pour un type persistant.</span><span class="sxs-lookup"><span data-stu-id="362c9-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="362c9-116">name</span><span class="sxs-lookup"><span data-stu-id="362c9-116">name</span></span>|<span data-ttu-id="362c9-117">Attribut facultatif qui contient une chaîne spécifiant le nom du type persistant.</span><span class="sxs-lookup"><span data-stu-id="362c9-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="362c9-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="362c9-118">Child Elements</span></span>  
 <span data-ttu-id="362c9-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="362c9-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="362c9-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="362c9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="362c9-121">Élément</span><span class="sxs-lookup"><span data-stu-id="362c9-121">Element</span></span>|<span data-ttu-id="362c9-122">Description</span><span class="sxs-lookup"><span data-stu-id="362c9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="362c9-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="362c9-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="362c9-124">Collection d'éléments `persistableType`.</span><span class="sxs-lookup"><span data-stu-id="362c9-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="362c9-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="362c9-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="362c9-126">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="362c9-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="362c9-127">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="362c9-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="362c9-128">Guide pratique pour configurer des paramètres de service COM+</span><span class="sxs-lookup"><span data-stu-id="362c9-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
