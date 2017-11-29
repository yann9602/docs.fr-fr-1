---
title: "Intégration de System.Web.Routing"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d1c1493e344bfe60a12ad16e3c0d257392b3545a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="15329-102">Intégration de System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="15329-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="15329-103">Lorsque vous hébergez un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dans les services IIS (Internet Information Services), vous placez un fichier .svc dans le répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="15329-103">When hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="15329-104">Ce fichier .svc spécifie la fabrique hôte de service à utiliser ainsi que la classe qui implémente le service.</span><span class="sxs-lookup"><span data-stu-id="15329-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="15329-105">Lorsque vous faites des demandes au service, vous spécifiez le fichier .svc dans l'URI, par exemple: http://contoso.com/EmployeeServce.svc.</span><span class="sxs-lookup"><span data-stu-id="15329-105">When making requests to the service you specify the .svc file in the URI, for example: http://contoso.com/EmployeeServce.svc.</span></span> <span data-ttu-id="15329-106">Pour les programmeurs qui écrivent des services REST, ce type d'URI n'est pas optimal.</span><span class="sxs-lookup"><span data-stu-id="15329-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="15329-107">Les URI des services REST spécifient une ressource spécifique et n'ont généralement pas d'extension.</span><span class="sxs-lookup"><span data-stu-id="15329-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="15329-108">La fonctionnalité d'intégration <xref:System.Web.Routing> vous permet d'héberger un service REST [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui répond aux URI sans extension.</span><span class="sxs-lookup"><span data-stu-id="15329-108">The <xref:System.Web.Routing> integration feature allows you to host a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST service that responds to URIs without an extension.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="15329-109">Voir routage [le routage ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660) et [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="15329-109"> routing see [ASP.NET Routing](http://go.microsoft.com/fwlink/?LinkId=184660) and the [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) sample.</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="15329-110">Utilisation de l'intégration System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="15329-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="15329-111">Pour utiliser la fonctionnalité d'intégration <xref:System.Web.Routing>, vous utilisez la classe <xref:System.ServiceModel.Activation.ServiceRoute> pour créer un ou plusieurs itinéraires et les ajouter à l'objet <xref:System.Web.Routing.RouteTable> dans un fichier Global.asax.</span><span class="sxs-lookup"><span data-stu-id="15329-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="15329-112">Ces itinéraires spécifient les URI relatifs auxquels le service répond.</span><span class="sxs-lookup"><span data-stu-id="15329-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="15329-113">L'exemple suivant montre comment effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="15329-113">The following example shows how to do this.</span></span>  
  
```  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));   
   }  
</script>  
```  
  
 <span data-ttu-id="15329-114">Ce code route toutes les demandes avec un URI relatif commençant par Customers vers le service `Service`.</span><span class="sxs-lookup"><span data-stu-id="15329-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="15329-115">Dans votre fichier Web.config, vous devez ajouter le module `System.Web.Routing.UrlRoutingModule`, affecter à l'attribut `runAllManagedModulesForAllRequests` la valeur `true` et ajouter le gestionnaire `UrlRoutingHandler` à l'élément `<system.webServer>`, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="15329-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 <span data-ttu-id="15329-116">Ce code charge un module et un gestionnaire nécessaires pour le routage.</span><span class="sxs-lookup"><span data-stu-id="15329-116">This loads a module and handler required for routing.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="15329-117">[Routage](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="15329-117"> [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="15329-118">Vous devez également affecter à l'attribut `aspNetCompatibilityEnabled` la valeur `true` dans l'élément `<serviceHostingEnvironment>`, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="15329-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="15329-119">La classe qui implémente le service doit activer les exigences de compatibilité ASP.NET, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="15329-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="15329-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15329-120">See Also</span></span>  
 [<span data-ttu-id="15329-121">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="15329-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="15329-122">Le routage ASP.NET</span><span class="sxs-lookup"><span data-stu-id="15329-122">ASP.NET Routing</span></span>](http://go.microsoft.com/fwlink/?LinkId=184660)
