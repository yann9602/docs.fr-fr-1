---
title: WebContentTypeMapper, exemple
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27342076290ca40abefea63edcc5f5c7186c4256
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="84e6e-102">WebContentTypeMapper, exemple</span><span class="sxs-lookup"><span data-stu-id="84e6e-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="84e6e-103">Cet exemple illustre comment mapper les nouveaux types de contenu aux formats du corps des messages [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="84e6e-103">This sample demonstrates how to map new content types to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] message body formats.</span></span>  
  
 <span data-ttu-id="84e6e-104">L'élément <xref:System.ServiceModel.Description.WebHttpEndpoint> se connecte à l'encodeur de message Web, permettant ainsi à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de recevoir des messages JSON, des messages XML ou des messages binaires bruts au niveau du même point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="84e6e-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="84e6e-105">L'encodeur détermine le format du corps des messages en examinant le type de contenu HTTP des demandes.</span><span class="sxs-lookup"><span data-stu-id="84e6e-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="84e6e-106">Cet exemple introduit la classe <xref:System.ServiceModel.Channels.WebContentTypeMapper>, laquelle permet à l'utilisateur de contrôler le mappage entre le type de contenu et le format du corps des messages.</span><span class="sxs-lookup"><span data-stu-id="84e6e-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="84e6e-107"> fournit un ensemble de mappages par défaut destinés aux types de contenu.</span><span class="sxs-lookup"><span data-stu-id="84e6e-107"> provides a set of default mappings for content types.</span></span> <span data-ttu-id="84e6e-108">Par exemple, les mappages `application/json` et `text/xml` permettent de mapper les messages aux formats JSON et XML respectivement.</span><span class="sxs-lookup"><span data-stu-id="84e6e-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="84e6e-109">Les types de contenu qui ne sont pas mappés aux formats JSON ou XML sont mappés au format binaire brut.</span><span class="sxs-lookup"><span data-stu-id="84e6e-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="84e6e-110">Dans certaines situations (par exemple, avec des API de type push), les développeurs de service ne contrôlent pas le type de contenu retourné par le client.</span><span class="sxs-lookup"><span data-stu-id="84e6e-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="84e6e-111">Par exemple, les clients peuvent retourner le format JSON comme `text/javascript` au lieu de retourner `application/json`.</span><span class="sxs-lookup"><span data-stu-id="84e6e-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="84e6e-112">Dans ce cas de figure, le développeur de service doit fournir un type qui dérive de <xref:System.ServiceModel.Channels.WebContentTypeMapper> pour pouvoir gérer correctement ce type de contenu, tel qu'illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="84e6e-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="84e6e-113">Ce type doit se substituer à la méthode <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="84e6e-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="84e6e-114">La méthode doit évaluer l'argument `contentType` et retourner l'une des valeurs suivantes : <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw> ou <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span><span class="sxs-lookup"><span data-stu-id="84e6e-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="84e6e-115">Lorsque cette méthode retourne la valeur <xref:System.ServiceModel.Channels.WebContentFormat.Default>, les mappages d'encodeur de message Web par défaut sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="84e6e-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="84e6e-116">Dans l'exemple de code précédent, le type de contenu `text/javascript` est mappé au format JSON. Tous les autres mappages restent, en revanche, inchangés.</span><span class="sxs-lookup"><span data-stu-id="84e6e-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="84e6e-117">Pour utiliser la classe `JsonContentTypeMapper`, utilisez ce qui suit dans votre Web.config :</span><span class="sxs-lookup"><span data-stu-id="84e6e-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="84e6e-118">Pour vérifier les conditions requises à l'utilisation du JsonContentTypeMapper, supprimez l'attribut contentTypeMapper du fichier de configuration ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="84e6e-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="84e6e-119">La page du client ne parvient pas à se charger lorsqu'elle essaie d'utiliser `text/javascript` pour envoyer le contenu JSON.</span><span class="sxs-lookup"><span data-stu-id="84e6e-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="84e6e-120">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="84e6e-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="84e6e-121">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="84e6e-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="84e6e-122">Générez la solution WebContentTypeMapperSample.sln comme décrit dans [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="84e6e-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="84e6e-123">Naviguez jusqu'à http://localhost/ServiceModelSamples/JCTMClientPage.htm (n'ouvrez pas JCTMClientPage.htm à l'aide d'un navigateur à partir du répertoire de projet).</span><span class="sxs-lookup"><span data-stu-id="84e6e-123">Navigate to http://localhost/ServiceModelSamples/JCTMClientPage.htm (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="84e6e-124">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="84e6e-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="84e6e-125">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="84e6e-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="84e6e-126">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="84e6e-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="84e6e-127">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="84e6e-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a><span data-ttu-id="84e6e-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84e6e-128">See Also</span></span>
