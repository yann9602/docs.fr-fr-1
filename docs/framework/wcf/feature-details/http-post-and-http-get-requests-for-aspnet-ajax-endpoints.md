---
title: "Comment : choisir entre des demandes HTTP POST et HTTP GET pour des points de terminaison AJAX ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 340f06c760ec4af6427343578790a8dad2d5dd62
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="7d45e-102">Comment : choisir entre des demandes HTTP POST et HTTP GET pour des points de terminaison AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7d45e-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="7d45e-103"> vous permet de créer un service qui expose un point de terminaison activé ASP.NET AJAX pouvant être appelé à partir de JavaScript sur un site Web client.</span><span class="sxs-lookup"><span data-stu-id="7d45e-103"> allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="7d45e-104">Les procédures de base pour la création de ces services est décrite dans [Comment : utiliser la Configuration pour ajouter un point de terminaison ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) et [Comment : ajouter un point de terminaison du AJAX ASP.NET sans Configuration à l’aide de](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="7d45e-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="7d45e-105">ASP.NET AJAX prend en charge des opérations utilisant les verbes HTTP POST et HTTP GET, avec HTTP POST comme valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="7d45e-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="7d45e-106">Lors de la création d'une opération qui n'a pas d'effets secondaires et qui retourne des données qui changent rarement, voire jamais, utilisez HTTP GET à la place.</span><span class="sxs-lookup"><span data-stu-id="7d45e-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="7d45e-107">Les résultats des opérations GET peuvent être mis en cache, ce qui signifie que les conversations multiples vers la même opération peuvent aboutir à une seule demande à votre service.</span><span class="sxs-lookup"><span data-stu-id="7d45e-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="7d45e-108">La mise en cache n'est pas effectuée par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mais peut avoir lieu à tout niveau (dans le navigateur d'un utilisateur, sur un serveur proxy et à d'autres niveaux). La mise en cache est avantageuse si vous souhaitez augmenter la performance du service, mais peut ne pas convenir si les données changent fréquemment ou si l'opération effectue une action.</span><span class="sxs-lookup"><span data-stu-id="7d45e-108">The caching is not done by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="7d45e-109">Par exemple, si vous destinez le service à la gestion de la médiathèque d'un utilisateur, une opération qui recherche les artistes par titre d'album peut utiliser avantageusement GET, mais une opération qui ajoute un album à la collection personnelle de l'utilisateur doit utiliser POST.</span><span class="sxs-lookup"><span data-stu-id="7d45e-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="7d45e-110">Pour contrôler la durée de vie du cache, utilisez le type <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="7d45e-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="7d45e-111">Par exemple, lorsque vous concevez un service qui retourne des prévisions météorologiques mises à jour toutes les heures, vous pouvez utiliser GET mais il convient de limiter la durée de mise en cache à une heure ou moins pour éviter que les utilisateurs du service accèdent à des données périmées.</span><span class="sxs-lookup"><span data-stu-id="7d45e-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="7d45e-112">Lors de l'utilisation de services à partir d'une page ASP.NET AJAX utilisant le contrôle Script Manager ASP.Net AJAX, c'est égal si les opérations utilisent GET ou POST, le mécanisme du gestionnaire de script garantit que le type de demande correct est publié.</span><span class="sxs-lookup"><span data-stu-id="7d45e-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="7d45e-113">Les opérations HTTP GET utilisent tous les paramètres d'entrée pris en charge par les opérations POST, y compris les types de contrat de données complexes.</span><span class="sxs-lookup"><span data-stu-id="7d45e-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="7d45e-114">Toutefois, il est recommandé dans la plupart des cas d'éviter un trop grand nombre de paramètres ou des paramètres trop complexes dans les opérations GET parce que cela réduit l'efficacité de la mise en cache.</span><span class="sxs-lookup"><span data-stu-id="7d45e-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="7d45e-115">Cette rubrique explique comment sélectionner GET et POST en ajoutant les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> aux opérations pertinentes dans le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="7d45e-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="7d45e-116">Les autres étapes requises pour obtenir l'exécution du service (implémentation, configuration et hébergement du service) sont semblables à celles utilisées par tout service ASP.NET AJAX dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7d45e-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="7d45e-117">Une opération marquée avec <xref:System.ServiceModel.Web.WebGetAttribute> utilise toujours une demande GET.</span><span class="sxs-lookup"><span data-stu-id="7d45e-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="7d45e-118">Une opération marquée avec <xref:System.ServiceModel.Web.WebInvokeAttribute> ou une opération qu n'est marquée avec aucun des deux attributs, utilise une demande POST.</span><span class="sxs-lookup"><span data-stu-id="7d45e-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="7d45e-119"><xref:System.ServiceModel.Web.WebInvokeAttribute> autorise l'utilisation de verbes HTTP autres que GET et POST (tels que PUT et DELETE) à travers la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d45e-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="7d45e-120">Toutefois, ces verbes ne sont pas pris en charge par ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="7d45e-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="7d45e-121">Si vous projetez d'utiliser le service à partir des pages ASP.NET à l'aide du contrôle Script Manager ASP.Net AJAX, n'utilisez pas la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d45e-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="7d45e-122">Pour obtenir un exemple de commutation à GET, consultez le [servie AJAX de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="7d45e-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="7d45e-123">Pour obtenir un exemple qui utilise POST, consultez la [AJAX Service utilisant HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="7d45e-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="7d45e-124">Pour créer un service WCF qui répond aux demandes HTTP GET ou HTTP POST</span><span class="sxs-lookup"><span data-stu-id="7d45e-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>  
  
1.  <span data-ttu-id="7d45e-125">Définissez un contrat de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de base en utilisant une interface marquée avec l'attribut <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7d45e-125">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="7d45e-126">Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7d45e-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="7d45e-127">Ajoutez l'attribut <xref:System.ServiceModel.Web.WebGetAttribute> pour stipuler qu'une opération doit répondre aux demandes HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="7d45e-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="7d45e-128">Vous pouvez également ajouter l'attribut <xref:System.ServiceModel.Web.WebInvokeAttribute> pour spécifier explicitement HTTP POST ou ne pas spécifier d'attribut, dans ce cas la valeur par défaut est HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="7d45e-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>  
  
    ```  
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="7d45e-129">Implémentez le contrat de service `IMusicService` avec un `MusicService`.</span><span class="sxs-lookup"><span data-stu-id="7d45e-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>  
  
    ```  
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3.  <span data-ttu-id="7d45e-130">Créez un nouveau fichier pour le service avec une extension .svc dans l’application.</span><span class="sxs-lookup"><span data-stu-id="7d45e-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="7d45e-131">Modifier ce fichier en ajoutant les [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informations directives pour le service.</span><span class="sxs-lookup"><span data-stu-id="7d45e-131">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="7d45e-132">Spécifier que le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> doit être utilisé dans le [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) la directive pour configurer automatiquement un point de terminaison ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="7d45e-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
### <a name="to-call-the-service"></a><span data-ttu-id="7d45e-133">Pour appeler le service</span><span class="sxs-lookup"><span data-stu-id="7d45e-133">To call the service</span></span>  
  
1.  <span data-ttu-id="7d45e-134">Vous pouvez tester les opérations GET de votre service sans aucun code client, en utilisant le navigateur.</span><span class="sxs-lookup"><span data-stu-id="7d45e-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="7d45e-135">Par exemple, si votre service est configuré à l'adresse "http://example.com/service.svc", en tapant "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" dans la barre d'adresses du navigateur, vous appelez le service et la réponse est téléchargée ou affichée.</span><span class="sxs-lookup"><span data-stu-id="7d45e-135">For example, if your service is configured at the "http://example.com/service.svc" address, then typing "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>  
  
2.  <span data-ttu-id="7d45e-136">Vous pouvez utiliser les services avec les opérations GET de la même façon que tous les autres services ASP.NET AJAX, en tapant l'URL du service dans la collection Scripts du contrôle Script Manager ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="7d45e-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="7d45e-137">Pour obtenir un exemple, consultez la [servie AJAX de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="7d45e-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d45e-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d45e-138">See Also</span></span>  
 [<span data-ttu-id="7d45e-139">Création de Services WCF pour ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="7d45e-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="7d45e-140">Comment : migrer les Services Web ASP.NET compatible AJAX vers WCF</span><span class="sxs-lookup"><span data-stu-id="7d45e-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
