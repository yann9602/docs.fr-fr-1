---
title: "Comment : créer un flux RSS de base"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79e5bc1bedbe6fd0911931c83878ed20bc4bd17e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-basic-rss-feed"></a><span data-ttu-id="c8b40-102">Comment : créer un flux RSS de base</span><span class="sxs-lookup"><span data-stu-id="c8b40-102">How to: Create a Basic RSS Feed</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="c8b40-103"> vous permet de créer un service qui expose un flux de syndication.</span><span class="sxs-lookup"><span data-stu-id="c8b40-103"> allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="c8b40-104">Cette rubrique explique comment créer un service de syndication qui expose un flux de syndication RSS.</span><span class="sxs-lookup"><span data-stu-id="c8b40-104">This topic discusses how to create a syndication service that exposes an RSS syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="c8b40-105">Pour créer un service de syndication de base</span><span class="sxs-lookup"><span data-stu-id="c8b40-105">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="c8b40-106">Définissez un contrat de service utilisant une interface marquée avec l'attribut <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c8b40-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="c8b40-107">Chaque opération exposée comme un flux de syndication doit retourner un objet <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="c8b40-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> object.</span></span>  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="c8b40-108">Toutes les opérations du service qui appliquent l'attribut <xref:System.ServiceModel.Web.WebGetAttribute> sont mappées aux demandes HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="c8b40-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> attribute are mapped to HTTP GET requests.</span></span> <span data-ttu-id="c8b40-109">Pour mapper votre opération à une méthode HTTP différente, utilisez <xref:System.ServiceModel.Web.WebInvokeAttribute> à la place.</span><span class="sxs-lookup"><span data-stu-id="c8b40-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="c8b40-110">[Comment : créer un Service Web HTTP de WCF de base](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span><span class="sxs-lookup"><span data-stu-id="c8b40-110"> [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2.  <span data-ttu-id="c8b40-111">Implémentez le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="c8b40-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3.  <span data-ttu-id="c8b40-112">Créez un objet <xref:System.ServiceModel.Syndication.SyndicationFeed> et ajoutez un auteur, une catégorie et une description.</span><span class="sxs-lookup"><span data-stu-id="c8b40-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4.  <span data-ttu-id="c8b40-113">Créez plusieurs objets <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="c8b40-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5.  <span data-ttu-id="c8b40-114">Ajoutez le flux <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="c8b40-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> to the feed.</span></span>  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6.  <span data-ttu-id="c8b40-115">Retournez le flux.</span><span class="sxs-lookup"><span data-stu-id="c8b40-115">Return the feed.</span></span>  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a><span data-ttu-id="c8b40-116">Pour héberger un service</span><span class="sxs-lookup"><span data-stu-id="c8b40-116">To host a service</span></span>  
  
1.  <span data-ttu-id="c8b40-117">Créez un objet <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c8b40-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2.  <span data-ttu-id="c8b40-118">Ouvrez l'hôte de service et attendez jusqu'à ce que l'utilisateur appuie sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="c8b40-118">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="c8b40-119">Pour appeler GetBlog() avec un HTTP GET</span><span class="sxs-lookup"><span data-stu-id="c8b40-119">To call GetBlog() with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="c8b40-120">Ouvrez Internet Explorer, tapez l'URL suivante et appuyez sur ENTRÉE : http://localhost:8000/BlogService/GetBlog.</span><span class="sxs-lookup"><span data-stu-id="c8b40-120">Open Internet Explorer, type the following URL, and press ENTER: http://localhost:8000/BlogService/GetBlog.</span></span> <span data-ttu-id="c8b40-121">L'URL contient l'adresse de base du service (http://localhost:8000/BlogService), l'adresse relative du point de terminaison et l'opération de service à appeler.</span><span class="sxs-lookup"><span data-stu-id="c8b40-121">The URL contains the base address of the service (http://localhost:8000/BlogService), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="c8b40-122">Pour appeler GetBlog() à partir d'un code</span><span class="sxs-lookup"><span data-stu-id="c8b40-122">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="c8b40-123">Créez un <xref:System.Xml.XmlReader> avec l'adresse de base et la méthode que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="c8b40-123">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="c8b40-124">Appelez la méthode <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> statique, en passant dans le <xref:System.Xml.XmlReader> que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="c8b40-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="c8b40-125">Cela appelle l'opération de service et remplit un nouvel objet <xref:System.ServiceModel.Syndication.SyndicationFeed> avec le module de formatage retourné à partir de l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="c8b40-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="c8b40-126">Accédez à l'objet de flux.</span><span class="sxs-lookup"><span data-stu-id="c8b40-126">Access the feed object.</span></span>  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="c8b40-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="c8b40-127">Example</span></span>  
 <span data-ttu-id="c8b40-128">Les éléments suivants représentent l'intégralité du code pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="c8b40-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c8b40-129">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="c8b40-129">Compiling the Code</span></span>  
 <span data-ttu-id="c8b40-130">Lors de la compilation du code précédent, référencez System.ServiceModel.dll et System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="c8b40-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b40-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8b40-131">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
