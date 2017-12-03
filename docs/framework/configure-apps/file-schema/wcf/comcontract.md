---
title: '&lt;comContract&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f4fb83478ef7061a4b14e87d2dce7f9cd9bbf8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcomcontractgt"></a><span data-ttu-id="5a4bc-102">&lt;comContract&gt;</span><span class="sxs-lookup"><span data-stu-id="5a4bc-102">&lt;comContract&gt;</span></span>
<span data-ttu-id="5a4bc-103">Spécifie un contrat de service d'intégration COM+.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-103">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="5a4bc-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5a4bc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a4bc-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="5a4bc-105">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a4bc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a4bc-106">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="string"  
      namespace="string"  
      name="string"  
      requireSession="Boolean">  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a4bc-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5a4bc-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5a4bc-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a4bc-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="5a4bc-109">Attributes</span></span>  
  
|<span data-ttu-id="5a4bc-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="5a4bc-110">Attribute</span></span>|<span data-ttu-id="5a4bc-111">Description</span><span class="sxs-lookup"><span data-stu-id="5a4bc-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a4bc-112">contrat</span><span class="sxs-lookup"><span data-stu-id="5a4bc-112">contract</span></span>|<span data-ttu-id="5a4bc-113">Chaîne qui contient le type de contrat.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-113">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="5a4bc-114">name</span><span class="sxs-lookup"><span data-stu-id="5a4bc-114">name</span></span>|<span data-ttu-id="5a4bc-115">Chaîne qui contient le type de nom.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-115">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="5a4bc-116">namespace</span><span class="sxs-lookup"><span data-stu-id="5a4bc-116">namespace</span></span>|<span data-ttu-id="5a4bc-117">Chaîne qui contient l'espace de noms du contrat.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-117">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="5a4bc-118">requiresSession</span><span class="sxs-lookup"><span data-stu-id="5a4bc-118">requiresSession</span></span>|<span data-ttu-id="5a4bc-119">Valeur booléenne qui spécifie si le contrat ne peut être utilisé que sur des liaisons de session.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-119">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="5a4bc-120">Lorsque le service est initialisé, l'exécution d'intégration garantit que ce paramètre est cohérent avec le type de liaison à utiliser.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-120">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="5a4bc-121">Une exception est générée en cas de conflit avec une ou plusieurs liaisons du contrat.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-121">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="5a4bc-122">Si cette propriété a la valeur `false`, qu'un canal unidirectionnel est utilisé et qu'un paramètre [out] est présent, une exception est également levée.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-122">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a4bc-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5a4bc-123">Child Elements</span></span>  
  
|<span data-ttu-id="5a4bc-124">Élément</span><span class="sxs-lookup"><span data-stu-id="5a4bc-124">Element</span></span>|<span data-ttu-id="5a4bc-125">Description</span><span class="sxs-lookup"><span data-stu-id="5a4bc-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a4bc-126">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="5a4bc-126">persistableTypes</span></span>|<span data-ttu-id="5a4bc-127">Tous les types persistants.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-127">All the persistable types.</span></span>|  
|<span data-ttu-id="5a4bc-128">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="5a4bc-128">userDefinedTypes</span></span>|<span data-ttu-id="5a4bc-129">Collection de types définis par l'utilisateur (UDT) à inclure dans le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-129">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="5a4bc-130">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="5a4bc-130">exposedMethods</span></span>|<span data-ttu-id="5a4bc-131">Collection de méthodes COM+ exposées lorsque l’interface sur un composant COM+ est exposée en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-131">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a4bc-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5a4bc-132">Parent Elements</span></span>  
  
|<span data-ttu-id="5a4bc-133">Élément</span><span class="sxs-lookup"><span data-stu-id="5a4bc-133">Element</span></span>|<span data-ttu-id="5a4bc-134">Description</span><span class="sxs-lookup"><span data-stu-id="5a4bc-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a4bc-135">comContracts</span><span class="sxs-lookup"><span data-stu-id="5a4bc-135">comContracts</span></span>|<span data-ttu-id="5a4bc-136">Contient une collection d'éléments `comContract`.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-136">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a4bc-137">Remarques</span><span class="sxs-lookup"><span data-stu-id="5a4bc-137">Remarks</span></span>  
 <span data-ttu-id="5a4bc-138">Contrats de service d’intégration COM + sont actuellement restreints à l’espace de noms « http://tempuri.org » et le nom de contrat est dérivé de l’interface COM de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-138">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="5a4bc-139">Toutefois, vous pouvez spécifier des alternatives à l'aide de la section `comContracts`, ainsi que l'élément `comContract` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-139">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="5a4bc-140">Par exemple, vous pouvez utiliser la configuration suivante pour spécifier l'espace de noms, le nom de contrat et les types définis par l'utilisateur à inclure, ainsi que d'autres paramètres pour un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-140">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="5a4bc-141">Lorsque le service est initialisé, les espaces de noms et les noms de contrat spécifiés sont appliqués aux descriptions de service générées.</span><span class="sxs-lookup"><span data-stu-id="5a4bc-141">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4bc-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a4bc-142">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="5a4bc-143">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="5a4bc-143">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="5a4bc-144">Intégration à des Applications COM +</span><span class="sxs-lookup"><span data-stu-id="5a4bc-144">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="5a4bc-145">Comment : configurer les paramètres de Service COM +</span><span class="sxs-lookup"><span data-stu-id="5a4bc-145">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
