---
title: "Comment : migrer le code d'un service Web ASP.NET vers Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e56d2481785a9a8486174e611001b9d800c7c869
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a><span data-ttu-id="8a89d-102">Comment : migrer le code d'un service Web ASP.NET vers Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="8a89d-102">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="8a89d-103">La procédure suivante décrit comment migrer un service Web ASP.NET vers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a89d-103">The following procedure describes how to migrate an ASP.NET Web Service to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="8a89d-104">Procédure</span><span class="sxs-lookup"><span data-stu-id="8a89d-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a><span data-ttu-id="8a89d-105">Pour migrer le code de service Web ASP.NET vers WCF</span><span class="sxs-lookup"><span data-stu-id="8a89d-105">To migrate ASP.NET Web service code to WCF</span></span>  
  
1.  <span data-ttu-id="8a89d-106">Assurez-vous qu'il existe un ensemble de tests complet pour le service.</span><span class="sxs-lookup"><span data-stu-id="8a89d-106">Ensure that a comprehensive set of tests exist for the service.</span></span>  
  
2.  <span data-ttu-id="8a89d-107">Générez le fichier WSDL pour le service et enregistrez une copie dans le même dossier que le fichier .asmx du service.</span><span class="sxs-lookup"><span data-stu-id="8a89d-107">Generate the WSDL for the service and save a copy in the same folder as the service’s .asmx file.</span></span>  
  
3.  <span data-ttu-id="8a89d-108">Mettez à niveau le service Web ASP.NET pour utiliser .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="8a89d-108">Upgrade the ASP.NET Web service to use .NET 2.0.</span></span> <span data-ttu-id="8a89d-109">Tout d’abord déployer le .NET Framework 2.0 à l’application dans IIS et utilisez Visual Studio 2005 pour automatiser le processus de conversion de code, comme décrit dans [Guide pas à pas pour la conversion de projets Web à partir de Visual Studio .NET 2002/2003 vers Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span><span class="sxs-lookup"><span data-stu-id="8a89d-109">First deploy the .NET Framework 2.0 to the application in IIS, and then use Visual Studio 2005 to automate the code conversion process, as documented in [Step-By-Step Guide to Converting Web Projects from Visual Studio .NET 2002/2003 to Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span></span> <span data-ttu-id="8a89d-110">Exécutez l'ensemble des tests.</span><span class="sxs-lookup"><span data-stu-id="8a89d-110">Run the set of tests.</span></span>  
  
4.  <span data-ttu-id="8a89d-111">Fournissez des valeurs explicites pour les paramètres `Namespace` et `Name` des attributs <xref:System.Web.Services.WebService> si elles ne sont pas déjà fournies.</span><span class="sxs-lookup"><span data-stu-id="8a89d-111">Provide explicit values for the `Namespace` and `Name` parameters of the <xref:System.Web.Services.WebService> attributes if they are not provided already.</span></span> <span data-ttu-id="8a89d-112">Faites de même pour le paramètre `MessageName` de <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8a89d-112">Do the same for the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span> <span data-ttu-id="8a89d-113">Si des valeurs explicites ne sont pas déjà fournies pour les en-têtes HTTP SOAPAction par l'intermédiaire desquels les demandes sont routées ver les méthodes, alors spécifiez de manière explicite la valeur par défaut du paramètre `Action` avec une valeur <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8a89d-113">If explicit values are not already provided for the SOAPAction HTTP headers by which requests are routed to methods, then explicitly specify the default value of the `Action` parameter with a <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
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
  
5.  <span data-ttu-id="8a89d-114">Testez la modification.</span><span class="sxs-lookup"><span data-stu-id="8a89d-114">Test the change.</span></span>  
  
6.  <span data-ttu-id="8a89d-115">Déplacez tout code substantiel dans le corps des méthodes de la classe vers une classe distincte que la classe d'origine est tenue d'utiliser.</span><span class="sxs-lookup"><span data-stu-id="8a89d-115">Move any substantive code in the bodies of the methods of the class to a separate class that the original class is made to use.</span></span>  
  
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
  
7.  <span data-ttu-id="8a89d-116">Testez la modification.</span><span class="sxs-lookup"><span data-stu-id="8a89d-116">Test the change.</span></span>  
  
8.  <span data-ttu-id="8a89d-117">Ajoutez des références aux assemblys [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] System.ServiceModel et System.Runtime.Serialization au projet de service Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8a89d-117">Add references to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assemblies System.ServiceModel and System.Runtime.Serialization to the ASP.NET Web service project.</span></span>  
  
9. <span data-ttu-id="8a89d-118">Exécutez [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classe de client à partir de WSDL.</span><span class="sxs-lookup"><span data-stu-id="8a89d-118">Run [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class from the WSDL.</span></span> <span data-ttu-id="8a89d-119">Ajoutez le module de classe généré à la solution.</span><span class="sxs-lookup"><span data-stu-id="8a89d-119">Add the generated class module to the solution.</span></span>  
  
10. <span data-ttu-id="8a89d-120">Le module de classe généré à l'étape précédente contient la définition d'une interface.</span><span class="sxs-lookup"><span data-stu-id="8a89d-120">The class module generated in the preceding step contains the definition of an interface.</span></span>  
  
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
  
     <span data-ttu-id="8a89d-121">Modifiez la définition de la classe de service Web ASP.NET afin que la classe soit définie de manière à implémenter cette interface, tel que le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="8a89d-121">Modify the definition of the ASP.NET Web service class so that the class is defined as implementing that interface, as shown in the following sample code.</span></span>  
  
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
  
11. <span data-ttu-id="8a89d-122">Compilez le projet.</span><span class="sxs-lookup"><span data-stu-id="8a89d-122">Compile the project.</span></span> <span data-ttu-id="8a89d-123">Des erreurs peuvent se produire en raison du code généré à l'étape neuf qui dupliquait certaines définitions de type.</span><span class="sxs-lookup"><span data-stu-id="8a89d-123">There may be some errors due to the code generated in step nine that duplicated some type definitions.</span></span> <span data-ttu-id="8a89d-124">Réparez ces erreurs, normalement en supprimant les définitions préexistantes des types.</span><span class="sxs-lookup"><span data-stu-id="8a89d-124">Repair those errors, usually by deleting the pre-existing definitions of the types.</span></span> <span data-ttu-id="8a89d-125">Testez la modification.</span><span class="sxs-lookup"><span data-stu-id="8a89d-125">Test the change.</span></span>  
  
12. <span data-ttu-id="8a89d-126">Supprimez les attributs spécifiques à ASP.NET, tels que <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> et <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8a89d-126">Remove the ASP.NET-specific attributes, such as the <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> and <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
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
  
13. <span data-ttu-id="8a89d-127">Configurez la classe, qui est maintenant un type de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], pour requérir le mode de compatibilité ASP.NET [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] si le service Web ASP.NET était basé sur l'un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="8a89d-127">Configure the class, which is now a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service type, to require [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode if the ASP.NET Web service relied on any of the following:</span></span>  
  
    -   <span data-ttu-id="8a89d-128">La classe <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="8a89d-128">The <xref:System.Web.HttpContext> class.</span></span>  
  
    -   <span data-ttu-id="8a89d-129">Les profils ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8a89d-129">The ASP.NET Profiles.</span></span>  
  
    -   <span data-ttu-id="8a89d-130">Les listes de contrôle d'accès (ACL) sur les fichiers .asmx.</span><span class="sxs-lookup"><span data-stu-id="8a89d-130">ACLs on .asmx files.</span></span>  
  
    -   <span data-ttu-id="8a89d-131">Les options d'authentification IIS.</span><span class="sxs-lookup"><span data-stu-id="8a89d-131">IIS authentication options.</span></span>  
  
    -   <span data-ttu-id="8a89d-132">Les options d'emprunt d'identité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8a89d-132">ASP.NET impersonation options.</span></span>  
  
    -   <span data-ttu-id="8a89d-133">La globalisation ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8a89d-133">ASP.NET globalization.</span></span>  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. <span data-ttu-id="8a89d-134">Renommez le nom du fichier .asmx d'origine avec .asmx .old.</span><span class="sxs-lookup"><span data-stu-id="8a89d-134">Rename the original .asmx file to .asmx.old.</span></span>  
  
15. <span data-ttu-id="8a89d-135">Créez un fichier de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour le service, attribuez-lui l'extension .asmx et enregistrez-le à la racine de l'application dans IIS.</span><span class="sxs-lookup"><span data-stu-id="8a89d-135">Create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service file for the service, give it the extension, .asmx, and save it into the application root in IIS.</span></span>  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. <span data-ttu-id="8a89d-136">Ajoutez une configuration [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour le service à son fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="8a89d-136">Add a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration for the service to its Web.config file.</span></span> <span data-ttu-id="8a89d-137">Configurer le service pour utiliser le [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), à utiliser le fichier de service avec l’extension .asmx créée dans les étapes précédentes et ne pas générer le WSDL pour lui-même, mais pour utiliser le fichier WSDL à partir de l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="8a89d-137">Configure the service to use the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), to use the service file with the .asmx extension created in the preceding steps, and to not generate WSDL for itself, but to use the WSDL from step two.</span></span> <span data-ttu-id="8a89d-138">Par ailleurs, configurez-le pour qu'il utilise le mode de compatibilité ASP.NET si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8a89d-138">Also configure it to use ASP.NET compatibility mode if necessary.</span></span>  
  
    ```xml  
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
        address=""  
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
  
17. <span data-ttu-id="8a89d-139">Enregistrez la configuration.</span><span class="sxs-lookup"><span data-stu-id="8a89d-139">Save the configuration.</span></span>  
  
18. <span data-ttu-id="8a89d-140">Compilez le projet.</span><span class="sxs-lookup"><span data-stu-id="8a89d-140">Compile the project.</span></span>  
  
19. <span data-ttu-id="8a89d-141">Exécutez l'ensemble des tests pour vérifier que toutes les modifications fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="8a89d-141">Run the set of tests to make sure all the changes work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a89d-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a89d-142">See Also</span></span>  
 [<span data-ttu-id="8a89d-143">Guide pratique pour migrer le code client des services web ASP.NET vers Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="8a89d-143">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
