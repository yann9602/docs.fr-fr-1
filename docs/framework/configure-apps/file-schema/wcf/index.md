---
title: "Schéma de configuration WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 05aeeea7d10c012804fe083890bcc8516aa8c8bc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="3c690-102">Schéma de configuration WCF</span><span class="sxs-lookup"><span data-stu-id="3c690-102">WCF Configuration Schema</span></span>
<span data-ttu-id="3c690-103">Les éléments de configuration de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] permettent de configurer le service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] et les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="3c690-103">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] configuration elements enable you to configure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service and client applications.</span></span> <span data-ttu-id="3c690-104">Vous pouvez utiliser l’[outil Éditeur de configuration (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) pour créer et modifier des fichiers de configuration pour les clients et les services.</span><span class="sxs-lookup"><span data-stu-id="3c690-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="3c690-105">Les fichiers de configuration étant au format XML, il est nécessaire de maîtriser ce format pour pouvoir modifier ces fichiers à l'aide d'un éditeur de texte,</span><span class="sxs-lookup"><span data-stu-id="3c690-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="3c690-106">sans quoi vous risquez de rencontrer des problèmes tels qu'une balise ou un attribut d'élément XML manquant.</span><span class="sxs-lookup"><span data-stu-id="3c690-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="3c690-107">Ce problème a lieu car les balises et les attributs d'éléments XML respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="3c690-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="3c690-108">Le système de configuration [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] est basé sur l'espace de noms <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="3c690-108">The [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="3c690-109">Par conséquent, vous pouvez utiliser tous les dispositifs standard fournis par l'espace de noms <xref:System.Configuration>, tel que le verrouillage, le chiffrement et la fusion de la configuration, afin de renforcer la sécurité de votre application et sa configuration.</span><span class="sxs-lookup"><span data-stu-id="3c690-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="3c690-110">Pour plus d'informations sur ces concepts, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="3c690-110">For more information on these concepts, see the following topics.</span></span>  
  
 [<span data-ttu-id="3c690-111">Chiffrement des informations de configuration</span><span class="sxs-lookup"><span data-stu-id="3c690-111">Encrypting Configuration Information</span></span>](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [<span data-ttu-id="3c690-112">Verrouillage des paramètres de configuration</span><span class="sxs-lookup"><span data-stu-id="3c690-112">Locking Configuration Settings</span></span>](http://go.microsoft.com/fwlink/?LinkId=95338)  
  
 <span data-ttu-id="3c690-113">Cette section décrit toutes les valeurs possibles de chaque élément de configuration et leur interaction avec d'autres éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="3c690-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="3c690-114">Le plan suivant illustre le schéma de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="3c690-114">The following map illustrates the WCF configuration schema.</span></span>  
  
 <span data-ttu-id="3c690-115">![Schéma de configuration WCF](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")</span><span class="sxs-lookup"><span data-stu-id="3c690-115">![WCF Configuration Schema](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="3c690-116">Vous devez protéger des sections de configuration de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dans vos fichiers de configuration d'application (app.config) en utilisant les listes ACL appropriées, afin d'empêcher toute menace potentielle sur la sécurité.</span><span class="sxs-lookup"><span data-stu-id="3c690-116">You should protect [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="3c690-117">Par exemple, vous devez vous assurer que seules les personnes appropriées peuvent accéder ou modifier les paramètres de sécurité relatifs aux liaisons d’application ou la section relative au modèle de service figurant dans le fichier de configuration d’un service.</span><span class="sxs-lookup"><span data-stu-id="3c690-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c690-118">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3c690-118">In This Section</span></span>  
 [<span data-ttu-id="3c690-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3c690-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 <span data-ttu-id="3c690-120">Décrit l'élément `ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="3c690-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="3c690-121">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="3c690-121">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 <span data-ttu-id="3c690-122">Configure l'outil SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="3c690-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="3c690-123">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="3c690-123">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 <span data-ttu-id="3c690-124">Élément de niveau supérieur permettant de définir les options lors de l'utilisation de sérialiseurs tels que le <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3c690-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3c690-125">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="3c690-125">Related Sections</span></span>  
 [<span data-ttu-id="3c690-126">Configuration des applications Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3c690-126">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 <span data-ttu-id="3c690-127">Explique comment configurer des services et des clients [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c690-127">Describes how to configure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services and clients.</span></span>
