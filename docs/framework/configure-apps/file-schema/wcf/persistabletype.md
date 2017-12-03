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
ms.openlocfilehash: 56443902885e191d93897096e55742f7665ba00a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="7e13f-102">&lt;élément persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="7e13f-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="7e13f-103">Spécifie tous les types persistants.</span><span class="sxs-lookup"><span data-stu-id="7e13f-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="7e13f-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7e13f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7e13f-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="7e13f-105">\<comContracts></span></span>  
<span data-ttu-id="7e13f-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="7e13f-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e13f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e13f-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="7e13f-108">Type</span><span class="sxs-lookup"><span data-stu-id="7e13f-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e13f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7e13f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7e13f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7e13f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e13f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="7e13f-111">Attributes</span></span>  
  
|<span data-ttu-id="7e13f-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="7e13f-112">Attribute</span></span>|<span data-ttu-id="7e13f-113">Description</span><span class="sxs-lookup"><span data-stu-id="7e13f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e13f-114">id</span><span class="sxs-lookup"><span data-stu-id="7e13f-114">id</span></span>|<span data-ttu-id="7e13f-115">Attribut requis qui contient une chaîne spécifiant un identificateur unique pour un type persistant.</span><span class="sxs-lookup"><span data-stu-id="7e13f-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="7e13f-116">name</span><span class="sxs-lookup"><span data-stu-id="7e13f-116">name</span></span>|<span data-ttu-id="7e13f-117">Attribut facultatif qui contient une chaîne spécifiant le nom du type persistant.</span><span class="sxs-lookup"><span data-stu-id="7e13f-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e13f-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7e13f-118">Child Elements</span></span>  
 <span data-ttu-id="7e13f-119">None</span><span class="sxs-lookup"><span data-stu-id="7e13f-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e13f-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7e13f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7e13f-121">Élément</span><span class="sxs-lookup"><span data-stu-id="7e13f-121">Element</span></span>|<span data-ttu-id="7e13f-122">Description</span><span class="sxs-lookup"><span data-stu-id="7e13f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e13f-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="7e13f-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="7e13f-124">Collection d'éléments `persistableType`.</span><span class="sxs-lookup"><span data-stu-id="7e13f-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e13f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e13f-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="7e13f-126">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="7e13f-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="7e13f-127">Intégration à des Applications COM +</span><span class="sxs-lookup"><span data-stu-id="7e13f-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="7e13f-128">Comment : configurer les paramètres de Service COM +</span><span class="sxs-lookup"><span data-stu-id="7e13f-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
