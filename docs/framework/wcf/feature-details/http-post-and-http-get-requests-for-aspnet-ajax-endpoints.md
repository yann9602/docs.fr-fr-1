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
ms.workload: dotnet
ms.openlocfilehash: fa8aceace03d1abb3bb83de1262331485f12ded3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Comment : choisir entre des demandes HTTP POST et HTTP GET pour des points de terminaison AJAX ASP.NET
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vous permet de créer un service qui expose un point de terminaison activé ASP.NET AJAX pouvant être appelé à partir de JavaScript sur un site Web client. Les procédures de base pour la création de ces services est décrite dans [Comment : utiliser la Configuration pour ajouter un point de terminaison ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) et [Comment : ajouter un point de terminaison du AJAX ASP.NET sans Configuration à l’aide de](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX prend en charge des opérations utilisant les verbes HTTP POST et HTTP GET, avec HTTP POST comme valeur par défaut. Lors de la création d'une opération qui n'a pas d'effets secondaires et qui retourne des données qui changent rarement, voire jamais, utilisez HTTP GET à la place. Les résultats des opérations GET peuvent être mis en cache, ce qui signifie que les conversations multiples vers la même opération peuvent aboutir à une seule demande à votre service. La mise en cache n'est pas effectuée par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mais peut avoir lieu à tout niveau (dans le navigateur d'un utilisateur, sur un serveur proxy et à d'autres niveaux). La mise en cache est avantageuse si vous souhaitez augmenter la performance du service, mais peut ne pas convenir si les données changent fréquemment ou si l'opération effectue une action.  
  
 Par exemple, si vous destinez le service à la gestion de la médiathèque d'un utilisateur, une opération qui recherche les artistes par titre d'album peut utiliser avantageusement GET, mais une opération qui ajoute un album à la collection personnelle de l'utilisateur doit utiliser POST.  
  
 Pour contrôler la durée de vie du cache, utilisez le type <xref:System.ServiceModel.Web.OutgoingWebResponseContext>. Par exemple, lorsque vous concevez un service qui retourne des prévisions météorologiques mises à jour toutes les heures, vous pouvez utiliser GET mais il convient de limiter la durée de mise en cache à une heure ou moins pour éviter que les utilisateurs du service accèdent à des données périmées.  
  
 Lors de l'utilisation de services à partir d'une page ASP.NET AJAX utilisant le contrôle Script Manager ASP.Net AJAX, c'est égal si les opérations utilisent GET ou POST, le mécanisme du gestionnaire de script garantit que le type de demande correct est publié.  
  
 Les opérations HTTP GET utilisent tous les paramètres d'entrée pris en charge par les opérations POST, y compris les types de contrat de données complexes. Toutefois, il est recommandé dans la plupart des cas d'éviter un trop grand nombre de paramètres ou des paramètres trop complexes dans les opérations GET parce que cela réduit l'efficacité de la mise en cache.  
  
 Cette rubrique explique comment sélectionner GET et POST en ajoutant les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> aux opérations pertinentes dans le contrat de service. Les autres étapes requises pour obtenir l'exécution du service (implémentation, configuration et hébergement du service) sont semblables à celles utilisées par tout service ASP.NET AJAX dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Une opération marquée avec <xref:System.ServiceModel.Web.WebGetAttribute> utilise toujours une demande GET. Une opération marquée avec <xref:System.ServiceModel.Web.WebInvokeAttribute> ou une opération qu n'est marquée avec aucun des deux attributs, utilise une demande POST. <xref:System.ServiceModel.Web.WebInvokeAttribute> autorise l'utilisation de verbes HTTP autres que GET et POST (tels que PUT et DELETE) à travers la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A>. Toutefois, ces verbes ne sont pas pris en charge par ASP.NET AJAX. Si vous projetez d'utiliser le service à partir des pages ASP.NET à l'aide du contrôle Script Manager ASP.Net AJAX, n'utilisez pas la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A>.  
  
 Pour obtenir un exemple de commutation à GET, consultez le [servie AJAX de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemple.  
  
 Pour obtenir un exemple qui utilise POST, consultez la [AJAX Service utilisant HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) exemple.  
  
### <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Pour créer un service WCF qui répond aux demandes HTTP GET ou HTTP POST  
  
1.  Définissez un contrat de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de base en utilisant une interface marquée avec l'attribut <xref:System.ServiceModel.ServiceContractAttribute>. Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>. Ajoutez l'attribut <xref:System.ServiceModel.Web.WebGetAttribute> pour stipuler qu'une opération doit répondre aux demandes HTTP GET. Vous pouvez également ajouter l'attribut <xref:System.ServiceModel.Web.WebInvokeAttribute> pour spécifier explicitement HTTP POST ou ne pas spécifier d'attribut, dans ce cas la valeur par défaut est HTTP POST.  
  
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
  
2.  Implémentez le contrat de service `IMusicService` avec un `MusicService`.  
  
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
  
3.  Créez un nouveau fichier pour le service avec une extension .svc dans l’application. Modifier ce fichier en ajoutant les [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informations directives pour le service. Spécifier que le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> doit être utilisé dans le [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) la directive pour configurer automatiquement un point de terminaison ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
### <a name="to-call-the-service"></a>Pour appeler le service  
  
1.  Vous pouvez tester les opérations GET de votre service sans aucun code client, en utilisant le navigateur. Par exemple, si votre service est configuré à l'adresse "http://example.com/service.svc", en tapant "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" dans la barre d'adresses du navigateur, vous appelez le service et la réponse est téléchargée ou affichée.  
  
2.  Vous pouvez utiliser les services avec les opérations GET de la même façon que tous les autres services ASP.NET AJAX, en tapant l’URL du service dans la collection Scripts du contrôle Script Manager ASP.NET AJAX. Pour obtenir un exemple, consultez la [servie AJAX de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création de services WCF pour ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Guide pratique pour migrer des services web ASP.NET compatibles AJAX vers WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
