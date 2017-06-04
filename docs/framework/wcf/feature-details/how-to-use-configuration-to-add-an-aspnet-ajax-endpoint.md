---
title: "Comment&#160;: utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Comment&#160;: utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vous permet de créer un service qui rend disponible un point de terminaison compatible ASP.NET AJAX pouvant être appelé à partir de JavaScript sur un site Web client.Pour créer ce point de terminaison, vous pouvez utiliser un fichier de configuration, comme pour tous les autres points de terminaison [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], ou utiliser une méthode qui ne requiert aucun élément de configuration.Cette rubrique décrit l'approche utilisant le fichier de configuration.  
  
 La partie de la procédure qui permet de rendre le point de terminaison du service compatible ASP.NET AJAX consiste à configurer le point de terminaison pour utiliser <xref:System.ServiceModel.WebHttpBinding> et ajouter le comportement du point de terminaison [\<enableWebScript\>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md).Après avoir configuré le point de terminaison, les étapes pour implémenter et héberger le service sont semblables à celles utilisée pour tout service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Pour obtenir un exemple fonctionnel, consultez [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] comment configurer un point de terminaison ASP.NET AJAX sans utiliser la configuration, consultez [Comment : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
### Pour créer un service WCF de base  
  
1.  Définissez un contrat de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de base en utilisant une interface marquée avec l'attribut <xref:System.ServiceModel.ServiceContractAttribute>.Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>.Assurez\-vous de définir la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.  
  
    ```  
    [ServiceContract(Namespace = "MyService")]  
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
  
### Pour créer un point de terminaison ASP.NET AJAX pour le service  
  
1.  Créez une configuration de comportement et spécifiez le comportement [\<enableWebScript\>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) pour les points de terminaison compatibles ASP.NET AJAX du service.  
  
    ```  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2.  Créez un point de terminaison pour le service qui utilise <xref:System.ServiceModel.WebHttpBinding> et le comportement ASP.NET AJAX défini dans l'étape précédente.  
  
    ```  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"   
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>   
    ```  
  
### Pour héberger le service dans IIS  
  
1.  Pour héberger le service dans IIS, créez un nouveau fichier nommé "Service" avec une extension .svc dans l'application.Modifiez ce fichier en ajoutant les informations directrices [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) appropriées pour le service.Le contenu du fichier Service pour l'exemple `CalculatorService` contient les informations suivantes :  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'hébergement dans IIS, consultez [Comment : héberger un service WCF dans IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### Pour appeler le service  
  
1.  Le point de terminaison est configuré au niveau d'une adresse vide relative au fichier .svc, par conséquent, le service est maintenant disponible et peut être appelé par l'envoi de demandes à service.svc\/\<operation\>, par exemple, service.svc\/Add pour l'opération `Add`.Vous pouvez l'utiliser en entrant le point l'URL du point de terminaison dans la collection Scripts du contrôle Script Manager ASP.NET AJAX .Pour obtenir un exemple, consultez [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## Voir aussi  
 [Création de services WCF pour ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)   
 [Comment : migrer des services Web ASP.NET compatibles AJAX vers WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)