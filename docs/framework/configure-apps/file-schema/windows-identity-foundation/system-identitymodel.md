---
title: '&lt;system.identityModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e5d26ab2ff3207b0905c33ba237bf71e623a103d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemidentitymodelgt"></a><span data-ttu-id="e0cff-102">&lt;system.identityModel&gt;</span><span class="sxs-lookup"><span data-stu-id="e0cff-102">&lt;system.identityModel&gt;</span></span>
<span data-ttu-id="e0cff-103">Fournit la configuration pour activer les options de Windows Identity Foundation (WIF) dans les applications.</span><span class="sxs-lookup"><span data-stu-id="e0cff-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="e0cff-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="e0cff-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0cff-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0cff-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0cff-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e0cff-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e0cff-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e0cff-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0cff-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="e0cff-108">Attributes</span></span>  
 <span data-ttu-id="e0cff-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e0cff-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e0cff-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e0cff-110">Child Elements</span></span>  
  
|<span data-ttu-id="e0cff-111">Élément</span><span class="sxs-lookup"><span data-stu-id="e0cff-111">Element</span></span>|<span data-ttu-id="e0cff-112">Description</span><span class="sxs-lookup"><span data-stu-id="e0cff-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0cff-113">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e0cff-113">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="e0cff-114">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="e0cff-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0cff-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e0cff-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e0cff-116">Élément</span><span class="sxs-lookup"><span data-stu-id="e0cff-116">Element</span></span>|<span data-ttu-id="e0cff-117">Description</span><span class="sxs-lookup"><span data-stu-id="e0cff-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="e0cff-118">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0cff-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0cff-119">Notes</span><span class="sxs-lookup"><span data-stu-id="e0cff-119">Remarks</span></span>  
 <span data-ttu-id="e0cff-120">Ajouter un `<system.identityModel>` section au fichier de configuration pour configurer un service ou une application à utiliser Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="e0cff-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="e0cff-121">Le `<system.identityModel>` élément est représenté par la <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> classe.</span><span class="sxs-lookup"><span data-stu-id="e0cff-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0cff-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="e0cff-122">Example</span></span>  
 <span data-ttu-id="e0cff-123">L’exemple suivant montre comment ajouter un `<system.identityModel>` section dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e0cff-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="e0cff-124">Vous devez d’abord ajouter la déclaration d’espace de noms et de la section configuration sous la `<configSections>` élément.</span><span class="sxs-lookup"><span data-stu-id="e0cff-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="e0cff-125">Vous pouvez ensuite ajouter le `<system.IdentityModel>` élément à votre fichier de configuration pour spécifier une ou plusieurs configurations d’identité.</span><span class="sxs-lookup"><span data-stu-id="e0cff-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0cff-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0cff-126">See Also</span></span>  
 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
