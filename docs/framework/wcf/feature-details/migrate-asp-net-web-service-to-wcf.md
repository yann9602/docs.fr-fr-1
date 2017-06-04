---
title: "Comment&#160;: migrer le code d&#39;un service Web ASP.NET vers Windows Communication Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Comment&#160;: migrer le code d&#39;un service Web ASP.NET vers Windows Communication Foundation
La procédure suivante décrit comment migrer un service Web ASP.NET vers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## Procédure  
  
#### Pour migrer le code de service Web ASP.NET vers WCF  
  
1.  Assurez\-vous qu'il existe un ensemble de tests complet pour le service.  
  
2.  Générez le fichier WSDL pour le service et enregistrez une copie dans le même dossier que le fichier .asmx du service.  
  
3.  Mettez à niveau le service Web ASP.NET pour utiliser .NET 2.0.  Déployez d'abord .NET Framework 2.0 sur l'application dans IIS, puis utilisez Visual Studio 2005 pour automatiser le processus de conversion de code, tel que décrit dans le [guide pas à pas relatif à la conversion de projets web de Visual Studio .NET 2002\/2003 vers Visual Studio 2005.](http://go.microsoft.com/fwlink/?LinkId=96492).  Exécutez l'ensemble des tests.  
  
4.  Fournissez des valeurs explicites pour les paramètres `Namespace` et `Name` des attributs <xref:System.Web.Services.WebService> si elles ne sont pas déjà fournies.  Faites de même pour le paramètre `MessageName` de <xref:System.Web.Services.WebMethodAttribute>.  Si des valeurs explicites ne sont pas déjà fournies pour les en\-têtes HTTP SOAPAction par l'intermédiaire desquels les demandes sont routées ver les méthodes, alors spécifiez de manière explicite la valeur par défaut du paramètre `Action` avec une valeur <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
5.  Testez la modification.  
  
6.  Déplacez tout code substantiel dans le corps des méthodes de la classe vers une classe distincte que la classe d'origine est tenue d'utiliser.  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
    }  
  
    internal class ActualAdder  
    {  
         internal double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
7.  Testez la modification.  
  
8.  Ajoutez des références aux assemblys [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] System.ServiceModel et System.Runtime.Serialization au projet de service Web ASP.NET.  
  
9. Exécutez l'[Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer une classe de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à partir de WSDL.  Ajoutez le module de classe généré à la solution.  
  
10. Le module de classe généré à l'étape précédente contient la définition d'une interface.  
  
    ```  
    [System.ServiceModel.ServiceContractAttribute()]  
    public interface AdderSoap  
    {  
         [System.ServiceModel.OperationContractAttribute(  
          Action="http://tempuri.org/Add",   
          ReplyAction="http://tempuri.org/Add")]  
         AddResponse Add(AddRequest request);  
    }  
    ```  
  
     Modifiez la définition de la classe de service Web ASP.NET afin que la classe soit définie de manière à implémenter cette interface, tel que le montre l'exemple de code suivant.  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder: AdderSoap  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
            return new AddResponse(  
            new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
11. Compilez le projet.  Des erreurs peuvent se produire en raison du code généré à l'étape neuf qui dupliquait certaines définitions de type.  Réparez ces erreurs, normalement en supprimant les définitions préexistantes des types.  Testez la modification.  
  
12. Supprimez les attributs spécifiques à ASP.NET, tels que <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> et <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.  
  
    ```  
    public class Adder: AdderSoap  
    {  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
              return new AddResponse(  
             new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
13. Configurez la classe, qui est maintenant un type de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], pour requérir le mode de compatibilité ASP.NET [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] si le service Web ASP.NET était basé sur l'un des éléments suivants :  
  
    -   La classe <xref:System.Web.HttpContext>.  
  
    -   Les profils ASP.NET.  
  
    -   Les listes de contrôle d'accès \(ACL\) sur les fichiers .asmx.  
  
    -   Les options d'authentification IIS.  
  
    -   Les options d'emprunt d'identité ASP.NET.  
  
    -   La globalisation ASP.NET.  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. Renommez le nom du fichier .asmx d'origine avec .asmx .old.  
  
15. Créez un fichier de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour le service, attribuez\-lui l'extension .asmx et enregistrez\-le à la racine de l'application dans IIS.  
  
    ```  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. Ajoutez une configuration [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour le service à son fichier Web.config.  Configurez le service de manière à ce qu'il utilise [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) et le fichier de service avec l'extension .asmx créé aux étapes précédentes, et de manière à qu'il ne se génère pas de fichier WSDL, mais qu'il utilise plutôt celui créé à l'étape deux.  Par ailleurs, configurez\-le pour qu'il utilise le mode de compatibilité ASP.NET si nécessaire.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
     <system.web>  
      <compilation>  
      <buildProviders>  
       <remove extension=".asmx" />  
       <add extension=".asmx"   
        type=  
        "System.ServiceModel.Activation.ServiceBuildProvider,  
        T:System.ServiceModel, Version=2.0.0.0,   
       Culture=neutral,   
       PublicKeyToken=b77a5c561934e089" />  
      </buildProviders>  
      </compilation>  
     </system.web>  
     <system.serviceModel>  
      <services>  
      <service name="MyOrganization.Adder "  
        behaviorConfiguration="AdderBehavior">  
       <endpoint   
        address="”  
        binding="basicHttpBinding"  
        contract="AdderSoap "/>  
       </service>  
      </services>  
      <behaviors>  
      <behavior name="AdderBehavior">  
       <metadataPublishing   
        enableMetadataExchange="true"   
        enableGetWsdl="true"   
        enableHelpPage="true"   
        metadataLocation=  
        "http://MyHost.com/AdderService/Service.WSDL"/>  
      </behavior>  
      </behaviors>  
      <serviceHostingEnvironment   
       aspNetCompatibilityEnabled ="true"/>  
     </system.serviceModel>  
    </configuration>  
  
    ```  
  
17. Enregistrez la configuration.  
  
18. Compilez le projet.  
  
19. Exécutez l'ensemble des tests pour vérifier que toutes les modifications fonctionnent.  
  
## Voir aussi  
 [Comment : migrer le code client des services Web ASP.NET vers Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)