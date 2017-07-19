---
title: "Comment&#160;: ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Comment&#160;: ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vous permet de créer un service qui expose un point de terminaison activé ASP.NET AJAX pouvant être appelé à partir de JavaScript sur un site Web client. Pour créer ce point de terminaison, vous pouvez utiliser un fichier de configuration, comme pour tous les autres points de terminaison WCF, ou utiliser une méthode qui ne requiert aucun élément de configuration. Cette rubrique décrit la deuxième approche.  
  
 Pour créer des services avec les points de terminaison ASP.NET AJAX sans configuration, les services doivent être hébergés par les services IIS (Internet Information Services). Pour activer un point de terminaison ASP.NET AJAX à l’aide de cette approche, spécifiez la <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> comme paramètre Factory dans le [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive dans le fichier .svc. Cette fabrication personnalisée est le composant qui configure automatiquement un point de terminaison ASP.NET AJAX afin qu’il puisse être appelé à partir de JavaScript sur un site web client.  
  
 Pour obtenir un exemple, consultez la [AJAX Service sans Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Pour obtenir une description de la configuration d’un point de terminaison ASP.NET AJAX à l’aide des éléments de configuration, consultez [Comment : utiliser la Configuration pour ajouter un point de terminaison ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Pour créer un service WCF de base  
  
1.  Définir la base [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contrat de service avec une interface marquée avec la <xref:System.ServiceModel.ServiceContractAttribute> attribut. Marquez chaque opération avec le <xref:System.ServiceModel.OperationContractAttribute>. Veillez à définir le <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriété.  
  
    ```  
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
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  Définissez un espace de noms pour les implémentations `ICalculator` et `CalculatorService` en les encapsulant dans un bloc Namespace.  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Pour héberger le service dans les services IIS sans configuration  
  
1.  Créez un nouveau fichier pour le service avec une extension .svc dans l’application. Modifiez ce fichier en ajoutant approprié [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informations sur les directives pour le service. Spécifier que le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> doit être utilisé dans le [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive pour configurer automatiquement un point de terminaison ASP.NET AJAX.  
  
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
  
1.  Le point de terminaison est configuré avec une adresse vide relative au fichier .svc, afin que le service est désormais disponible et peut être appelé en envoyant des demandes à service.svc /<> \</> \> , par exemple, service.svc/Add pour le `Add` opération. Vous pouvez l’utiliser en entrant l’URL du service dans la collection Scripts du contrôle Script Manager ASP.NET AJAX. Pour obtenir un exemple, consultez la [AJAX Service sans Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Exemple  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
 Le point de terminaison configuré automatiquement est créé au niveau d'une adresse vide qui est fonction de l'URL de base. Un fichier de configuration peut également être ajouté et utilisé avec cette approche. Si le fichier de configuration contient des définitions de point de terminaison, ces points de terminaison sont ajoutés au point de terminaison configuré automatiquement.  
  
 Par exemple, service.svc utilise le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> et le répertoire du service contient un fichier Web.config qui définit un point de terminaison pour le même service en utilisant le <xref:System.ServiceModel.BasicHttpBinding> à l’adresse relative « soap ». Dans ce cas, le service contient deux points de terminaison : un au niveau de service.svc (qui répond aux demandes ASP.NET AJAX) et un autre au niveau de service.svc/soap (qui répond aux demandes SOAP).  
  
 Si le fichier de configuration définit un point de terminaison avec une adresse relative vide et le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est utilisé, une exception est levée et le service ne parvient pas à démarrer.  
  
 Vous ne pouvez pas utiliser de configuration pour modifier des paramètres sur le point de terminaison configuré automatiquement. Si un paramètre (par exemple, un quota de lecteur) doit être modifié, vous ne devez pas utiliser l’approche sans configuration en supprimant le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dans le fichier .svc et en créant une entrée de configuration pour le point de terminaison.  
  
 Si votre service requiert en Mode de compatibilité ASP.NET, par exemple, s’il utilise le <xref:System.Web.HttpContext> classe ou les mécanismes d’autorisation ASP.NET, un fichier de configuration est requis pour activer ce mode. L’élément de configuration requise est la [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) élément, qui doit être ajouté comme suit.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled=”true” /> </system.serviceModel>`  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]le [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) rubrique.  
  
 Le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> classe est une classe dérivée de <xref:System.ServiceModel.Activation.ServiceHostFactory>. Pour obtenir une explication détaillée de la méthode de fabrique hôte service, consultez la [extension de ServiceHostFactory à l’aide d’hébergement](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de Services WCF pour ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)   
 [Comment : migrer les Services Web ASP.NET compatible AJAX vers WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)