---
title: '&lt;exposedMethod&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c89acb38678879f882d8bb2a2b5277b555a1eb26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltexposedmethodgt"></a><span data-ttu-id="f119d-102">&lt;exposedMethod&gt;</span><span class="sxs-lookup"><span data-stu-id="f119d-102">&lt;exposedMethod&gt;</span></span>
<span data-ttu-id="f119d-103">Représente une méthode COM+ exposée lorsque l'interface sur un composant COM+ est exposée en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="f119d-103">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="f119d-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f119d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f119d-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="f119d-105">\<comContracts></span></span>  
<span data-ttu-id="f119d-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="f119d-106">\<comContract></span></span>  
<span data-ttu-id="f119d-107">\<méthodes ></span><span class="sxs-lookup"><span data-stu-id="f119d-107">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f119d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f119d-108">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f119d-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f119d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f119d-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f119d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f119d-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="f119d-111">Attributes</span></span>  
  
|<span data-ttu-id="f119d-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="f119d-112">Attribute</span></span>|<span data-ttu-id="f119d-113">Description</span><span class="sxs-lookup"><span data-stu-id="f119d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f119d-114">name</span><span class="sxs-lookup"><span data-stu-id="f119d-114">name</span></span>|<span data-ttu-id="f119d-115">Chaîne qui contient la méthode COM+ exposée lorsque l'interface sur un composant COM+ est exposée comme un service Web.</span><span class="sxs-lookup"><span data-stu-id="f119d-115">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f119d-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f119d-116">Child Elements</span></span>  
 <span data-ttu-id="f119d-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f119d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f119d-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f119d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f119d-119">Élément</span><span class="sxs-lookup"><span data-stu-id="f119d-119">Element</span></span>|<span data-ttu-id="f119d-120">Description</span><span class="sxs-lookup"><span data-stu-id="f119d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f119d-121">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="f119d-121">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="f119d-122">Une collection de [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="f119d-122">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f119d-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="f119d-123">Remarks</span></span>  
 <span data-ttu-id="f119d-124">Il est possible d'utiliser l'outil de configuration d'intégration COM+ (ComSvcConfig.exe) pour ajouter des méthodes spécifiques issues d'une interface COM afin qu'elles apparaissent sur le contrat de service généré.</span><span class="sxs-lookup"><span data-stu-id="f119d-124">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="f119d-125">Par exemple, vous pouvez utiliser la commande suivante pour ajouter les trois méthodes nommées issues de l'interface COM `IFinances` sur le composant financier `ItemOrders` au contrat de service généré.</span><span class="sxs-lookup"><span data-stu-id="f119d-125">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="f119d-126">Lorsque vous exécutez également la ComSvcConfig.exe, il génère le contrat de service suivant, qui répertorie les méthodes mentionnées précédemment comme [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="f119d-126">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 <span data-ttu-id="f119d-127">Au moment de l’initialisation du service, le runtime tente de générer un contrat de service en reflétant sur et en ajoutant uniquement les méthodes incluses dans la liste des [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="f119d-127">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="f119d-128">Une trace est produite pour chaque méthode d'interface qui n'est pas incluse sur le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="f119d-128">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f119d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f119d-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>  
 <xref:System.ServiceModel.Configuration.ComMethodElement>  
 [<span data-ttu-id="f119d-130">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="f119d-130">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="f119d-131">Intégration à des Applications COM +</span><span class="sxs-lookup"><span data-stu-id="f119d-131">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="f119d-132">Comment : configurer les paramètres de Service COM +</span><span class="sxs-lookup"><span data-stu-id="f119d-132">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
