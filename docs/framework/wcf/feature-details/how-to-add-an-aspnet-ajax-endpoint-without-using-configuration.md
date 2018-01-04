---
title: "Comment : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b90ecd94f439472c89d0c075c8b7486abeacf38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Comment : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vous permet de créer un service qui expose un point de terminaison activé ASP.NET AJAX pouvant être appelé à partir de JavaScript sur un site Web client. Pour créer ce point de terminaison, vous pouvez utiliser un fichier de configuration, comme pour tous les autres points de terminaison WCF, ou utiliser une méthode qui ne requiert aucun élément de configuration. Cette rubrique décrit la deuxième approche.  
  
 Pour créer des services avec les points de terminaison ASP.NET AJAX sans configuration, les services doivent être hébergés par les services IIS (Internet Information Services). Pour activer un point de terminaison ASP.NET AJAX à l’aide de cette approche, vous devez spécifier le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> comme paramètre fabrique dans la [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive dans le fichier .svc. Cette fabrication personnalisée est le composant qui configure automatiquement un point de terminaison ASP.NET AJAX afin qu’il puisse être appelé à partir de JavaScript sur un site web client.  
  
 Pour obtenir un exemple, consultez la [AJAX Service sans Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Pour obtenir une description de la configuration d’un point de terminaison ASP.NET AJAX à l’aide des éléments de configuration, consultez [Comment : utiliser la Configuration pour ajouter un point de terminaison ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Pour créer un service WCF de base  
  
1.  Définissez un contrat de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de base en utilisant une interface marquée avec l'attribut <xref:System.ServiceModel.ServiceContractAttribute>. Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>. Assurez-vous de définir la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  Implémentez le contrat de service `ICalculator` avec un `CalculatorService`.  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  Définissez un espace de noms pour les implémentations `ICalculator` et `CalculatorService` en les encapsulant dans un bloc Namespace.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Pour héberger le service dans les services IIS sans configuration  
  
1.  Créez un nouveau fichier pour le service avec une extension .svc dans l’application. Modifier ce fichier en ajoutant les [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informations directives pour le service. Spécifier que le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> doit être utilisé dans le [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) la directive pour configurer automatiquement un point de terminaison ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  Générez le service et appelez-le à partir du client. Les services IIS (Internet Information Services) activent le service lorsqu'il est appelé. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]hébergement dans IIS, consultez [Comment : héberger un Service WCF dans IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Pour appeler le service  
  
1.  Le point de terminaison est configuré avec une adresse vide renvoyant au fichier .svc, afin que le service est maintenant disponible et peut être appelé en envoyant des demandes à service.svc /\<opération >, par exemple, service.svc/Add pour le `Add` opération. Vous pouvez l’utiliser en entrant l’URL du service dans la collection Scripts du contrôle Script Manager ASP.NET AJAX. Pour obtenir un exemple, consultez la [AJAX Service sans Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Exemple  
  
 Le point de terminaison configuré automatiquement est créé au niveau d'une adresse vide qui est fonction de l'URL de base. Un fichier de configuration peut également être ajouté et utilisé avec cette approche. Si le fichier de configuration contient des définitions de point de terminaison, ces points de terminaison sont ajoutés au point de terminaison configuré automatiquement.  
  
 Par exemple, service.svc utilise <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> et le répertoire du service contient un fichier Web.config qui définit un point de terminaison pour le même service en utilisant <xref:System.ServiceModel.BasicHttpBinding> au niveau de l'adresse relative « soap ». Dans ce cas, le service contient deux points de terminaison : un au niveau de service.svc (qui répond aux demandes ASP.NET AJAX) et un autre au niveau de service.svc/soap (qui répond aux demandes SOAP).  
  
 Si le fichier de configuration définit un point de terminaison au niveau d'une adresse relative vide et <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est utilisé, une exception est levée et le service ne peut pas démarrer.  
  
 Vous ne pouvez pas utiliser de configuration pour modifier des paramètres sur le point de terminaison configuré automatiquement. Si un paramètre (tel qu'un quota de lecteur) doit être modifié, vous ne devez pas utiliser l'approche sans configuration en supprimant <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dans le fichier .svc et en créant une entrée de configuration pour le point de terminaison.  
  
 Si votre service requiert le mode de compatibilité ASP.NET, par exemple, s'il utilise la classe <xref:System.Web.HttpContext> ou les mécanismes d'autorisation ASP.NET, un fichier de configuration est néanmoins requis pour activer ce mode. L’élément de configuration requise est la [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) élément, qui doit être ajouté comme suit.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]le [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) rubrique.  
  
 La classe <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est dérivée de la classe <xref:System.ServiceModel.Activation.ServiceHostFactory>. Pour obtenir une explication détaillée de la méthode de fabrique hôte service, consultez le [extension de ServiceHostFactory à l’aide d’hébergement](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de services WCF pour ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Guide pratique pour migrer des services web ASP.NET compatibles AJAX vers WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
