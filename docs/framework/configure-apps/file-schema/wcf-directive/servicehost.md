---
title: '@ServiceHost'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 027debb311a3f9547623b6dff778e82b7e475327
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="servicehost"></a>@ServiceHost
<span data-ttu-id="6cd00-101">Associe la fabrique utilisée pour générer l'hôte de service au service à héberger ainsi qu'à d'autres aspects de programmation requis pour compiler le code d'hébergement fourni dans le fichier .svc ou pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="6cd00-101">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd00-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cd00-102">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="6cd00-103">Attributs</span><span class="sxs-lookup"><span data-stu-id="6cd00-103">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="6cd00-104">Service</span><span class="sxs-lookup"><span data-stu-id="6cd00-104">Service</span></span>  
 <span data-ttu-id="6cd00-105">Nom de type CLR du service hébergé.</span><span class="sxs-lookup"><span data-stu-id="6cd00-105">The CLR type name of the service hosted.</span></span> <span data-ttu-id="6cd00-106">Il doit s'agir d'un nom qualifié correspondant à un type qui implémente un ou plusieurs contacts du service.</span><span class="sxs-lookup"><span data-stu-id="6cd00-106">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="6cd00-107">Fabrique</span><span class="sxs-lookup"><span data-stu-id="6cd00-107">Factory</span></span>  
 <span data-ttu-id="6cd00-108">Nom de type CLR correspondant à la fabrique de l'hôte de service utilisée pour instancier l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="6cd00-108">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="6cd00-109">Cet attribut est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6cd00-109">This attribute is optional.</span></span> <span data-ttu-id="6cd00-110">S'il n'est pas spécifié, le <xref:System.ServiceModel.Activation.ServiceHostFactory> par défaut est utilisé et renvoie une instance de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6cd00-110">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="6cd00-111">Déboguer</span><span class="sxs-lookup"><span data-stu-id="6cd00-111">Debug</span></span>  
 <span data-ttu-id="6cd00-112">Indique si le service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] doit être compilé avec les symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="6cd00-112">Indicates whether the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service should be compiled with debug symbols.</span></span> <span data-ttu-id="6cd00-113">`true` si le service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] doit être compilé avec les symboles de débogage ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="6cd00-113">`true` if the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="6cd00-114">Langage</span><span class="sxs-lookup"><span data-stu-id="6cd00-114">Language</span></span>  
 <span data-ttu-id="6cd00-115">Spécifie le langage utilisé lors de la compilation de l'intégralité du code incorporé dans le fichier (.svc).</span><span class="sxs-lookup"><span data-stu-id="6cd00-115">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="6cd00-116">Ces valeurs peuvent représenter tout langage pris en charge par .NET, notamment C#, VB et JS, qui font respectivement référence à C#, Visual Basic .NET et JScript .NET.</span><span class="sxs-lookup"><span data-stu-id="6cd00-116">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="6cd00-117">Cet attribut est facultatif.</span><span class="sxs-lookup"><span data-stu-id="6cd00-117">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="6cd00-118">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="6cd00-118">CodeBehind</span></span>  
 <span data-ttu-id="6cd00-119">Spécifie le fichier source qui implémente le service web XML, lorsque la classe implémentant le service web XML ne réside pas dans le même fichier et n’a pas été compilée dans un assembly et placée dans le répertoire \Bin.</span><span class="sxs-lookup"><span data-stu-id="6cd00-119">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cd00-120">Notes</span><span class="sxs-lookup"><span data-stu-id="6cd00-120">Remarks</span></span>  
 <span data-ttu-id="6cd00-121">Le <xref:System.ServiceModel.ServiceHost> utilisé pour héberger le service est un point d'extensibilité figurant dans le modèle de programmation [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6cd00-121">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] programming model.</span></span> <span data-ttu-id="6cd00-122">Un modèle de fabrique est utilisé pour instancier le <xref:System.ServiceModel.ServiceHost> car il peut s'agir d'un type polymorphe ne devant pas être instancié directement par l'environnement d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="6cd00-122">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="6cd00-123">L'implémentation par défaut utilise <xref:System.ServiceModel.Activation.ServiceHostFactory> pour créer une instance de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6cd00-123">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="6cd00-124">Mais vous pouvez fournir votre propre fabrique (celle qui retourne votre hôte dérivé) en spécifiant le nom de type CLR de l’implémentation de fabrique dans la [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) la directive.</span><span class="sxs-lookup"><span data-stu-id="6cd00-124">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="6cd00-125">Pour utiliser fabrique hôte de service personnalisé propre au lieu de la fabrique par défaut, simplement fournir le nom de type dans le [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive comme suit :</span><span class="sxs-lookup"><span data-stu-id="6cd00-125">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="6cd00-126">Surchargez les implémentations de fabrique le moins possible.</span><span class="sxs-lookup"><span data-stu-id="6cd00-126">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="6cd00-127">Si vous disposez d'une importante logique personnalisée, votre code est plus facilement réutilisable si vous intégrez cette logique à votre hôte et non à la fabrique.</span><span class="sxs-lookup"><span data-stu-id="6cd00-127">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="6cd00-128">Par exemple, pour activer un point de terminaison compatible AJAX pour `MyService`, spécifiez la <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> pour la valeur de la `Factory` attribut, au lieu de la valeur par défaut <xref:System.ServiceModel.Activation.ServiceHostFactory>, dans le [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive en tant que indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6cd00-128">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cd00-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="6cd00-129">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6cd00-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cd00-130">See Also</span></span>  
 [<span data-ttu-id="6cd00-131">Hôte de service personnalisé</span><span class="sxs-lookup"><span data-stu-id="6cd00-131">Custom Service Host</span></span>](../../../../../docs/framework/wcf/samples/custom-service-host.md)
