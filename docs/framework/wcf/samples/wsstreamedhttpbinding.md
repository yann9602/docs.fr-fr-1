---
title: WSStreamedHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
caps.latest.revision: "27"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8238ede6fd43cc5cca2df1f8c7f9162f9c4a1302
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="e7ded-102">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e7ded-102">WSStreamedHttpBinding</span></span>
<span data-ttu-id="e7ded-103">Cet exemple montre comment créer une liaison conçue pour prendre en charge des scénarios de diffusion en continu lorsque le transport HTTP est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e7ded-103">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7ded-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e7ded-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e7ded-105">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e7ded-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e7ded-106">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="e7ded-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e7ded-107">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e7ded-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e7ded-108">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="e7ded-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 <span data-ttu-id="e7ded-109">Les étapes de la création et de la configuration d’une nouvelle liaison standard sont les suivantes.</span><span class="sxs-lookup"><span data-stu-id="e7ded-109">The steps to create and configure a new standard binding are as follows.</span></span>  
  
1.  <span data-ttu-id="e7ded-110">Créez une liaison standard</span><span class="sxs-lookup"><span data-stu-id="e7ded-110">Create a new standard binding</span></span>  
  
     <span data-ttu-id="e7ded-111">Les liaisons standard dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] telles que basicHttpBinding et netTcpBinding configurent les transports sous-jacents et la pile de canaux pour des besoins spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e7ded-111">The standard bindings in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="e7ded-112">Dans cet exemple, `WSStreamedHttpBinding` configure la pile de canaux pour prendre en charge la diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="e7ded-112">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="e7ded-113">Par défaut, WS-Security et messagerie fiable ne sont pas ajoutés à la pile de canaux car ces deux fonctionnalités ne sont pas prises en charge par la diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="e7ded-113">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="e7ded-114">La nouvelle liaison est implémentée dans la classe `WSStreamedHttpBinding` qui dérive de <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="e7ded-114">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="e7ded-115">`WSStreamedHttpBinding` contient les éléments de liaison suivants : <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> et <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="e7ded-115">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="e7ded-116">La classe fournit une méthode `CreateBindingElements()` permettant de configurer la pile de liaison résultante, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="e7ded-116">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>  
  
    ```  
    public override BindingElementCollection CreateBindingElements()  
    {  
         // return collection of BindingElements  
         BindingElementCollection bindingElements = new BindingElementCollection();  
  
        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by  
        // the message encoder, and finally the transport at the end  
        if (flowTransactions)  
        {  
            bindingElements.Add(transactionFlow);  
        }  
        bindingElements.Add(textEncoding);  
  
        // add transport (http or https)  
        bindingElements.Add(transport);  
        return bindingElements.Clone();  
    }  
    ```  
  
2.  <span data-ttu-id="e7ded-117">Ajoutez la prise en charge de la configuration</span><span class="sxs-lookup"><span data-stu-id="e7ded-117">Add configuration support</span></span>  
  
     <span data-ttu-id="e7ded-118">Pour exposer le transport via la configuration, l'exemple implémente deux classes : `WSStreamedHttpBindingConfigurationElement` et `WSStreamedHttpBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="e7ded-118">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="e7ded-119">La classe `WSStreamedHttpBindingSection` est un <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> qui expose `WSStreamedHttpBinding` au système de configuration [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7ded-119">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration system.</span></span> <span data-ttu-id="e7ded-120">Le bloc de l'implémentation est délégué à `WSStreamedHttpBindingConfigurationElement`, qui dérive de <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="e7ded-120">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="e7ded-121">La classe `WSStreamedHttpBindingConfigurationElement` a des propriétés qui correspondent à celles de `WSStreamedHttpBinding`, et des fonctions pour mapper chaque élément de configuration à une liaison.</span><span class="sxs-lookup"><span data-stu-id="e7ded-121">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>  
  
     <span data-ttu-id="e7ded-122">Pour enregistrer le gestionnaire avec le système de configuration, ajoutez la section suivante au fichier de configuration du service.</span><span class="sxs-lookup"><span data-stu-id="e7ded-122">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <extensions>  
          <bindingExtensions>  
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </bindingExtensions>  
        </extensions>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="e7ded-123">Il pourra ensuite être référencé à partir de la section de configuration serviceModel.</span><span class="sxs-lookup"><span data-stu-id="e7ded-123">The handler can then be referenced from the serviceModel configuration section.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint  
                    address="https://localhost/servicemodelsamples/service.svc"  
                    bindingConfiguration="Binding"  
                    binding="wsStreamedHttpBinding"  
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e7ded-124">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="e7ded-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e7ded-125">Installez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 à l'aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="e7ded-125">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="e7ded-126">Vérifiez que vous avez effectué les étapes répertoriées dans [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e7ded-126">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="e7ded-127">Assurez-vous d’avoir effectué la [Instructions d’Installation du certificat serveur Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="e7ded-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="e7ded-128">Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e7ded-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="e7ded-129">Pour exécuter l’exemple dans une configuration à plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e7ded-129">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
6.  <span data-ttu-id="e7ded-130">Lorsque la fenêtre du client s'affiche, tapez « Sample.txt ».</span><span class="sxs-lookup"><span data-stu-id="e7ded-130">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="e7ded-131">Vous devez rechercher « Copy of Sample.txt » dans votre répertoire.</span><span class="sxs-lookup"><span data-stu-id="e7ded-131">You should find a "Copy of Sample.txt" in your directory.</span></span>  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="e7ded-132">Exemple de service WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e7ded-132">The WSStreamedHttpBinding Sample Service</span></span>  
 <span data-ttu-id="e7ded-133">L'exemple de service qui utilise `WSStreamedHttpBinding` se trouve dans le sous-répertoire de service.</span><span class="sxs-lookup"><span data-stu-id="e7ded-133">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="e7ded-134">L'implémentation de `OperationContract` utilise un `MemoryStream` pour récupérer dans un premier temps toutes les données du flux entrant avant de retourner `MemoryStream`.</span><span class="sxs-lookup"><span data-stu-id="e7ded-134">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="e7ded-135">L'exemple de service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="e7ded-135">The sample service is hosted by Internet Information Services (IIS).</span></span>  
  
```  
[ServiceContract]  
public interface IStreamedEchoService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
}  
  
public class StreamedEchoService : IStreamedEchoService  
{  
    public Stream Echo(Stream data)  
    {  
        MemoryStream dataStorage = new MemoryStream();  
        byte[] byteArray = new byte[8192];  
        int bytesRead = data.Read(byteArray, 0, 8192);  
        while (bytesRead > 0)  
        {  
            dataStorage.Write(byteArray, 0, bytesRead);  
            bytesRead = data.Read(byteArray, 0, 8192);  
        }  
        data.Close();  
        dataStorage.Seek(0, SeekOrigin.Begin);  
  
        return dataStorage;  
    }  
}  
```  
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="e7ded-136">Exemple de client WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e7ded-136">The WSStreamedHttpBinding Sample Client</span></span>  
 <span data-ttu-id="e7ded-137">Le client utilisé pour interagir avec le service à l'aide de `WSStreamedHttpBinding` se trouve dans le sous-répertoire client.</span><span class="sxs-lookup"><span data-stu-id="e7ded-137">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="e7ded-138">Le certificat utilisé dans cet exemple étant un certificat de test créé avec Makecert.exe, une alerte de sécurité s'affiche lorsque vous tentez d'accéder depuis votre navigateur à une adresse HTTPS telle que https://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="e7ded-138">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="e7ded-139">Pour permettre au client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] d'utiliser un certificat de test en vigueur, du code supplémentaire a été ajouté au client pour supprimer l'alerte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e7ded-139">To allow the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="e7ded-140">Le code, et la classe qui l'accompagne, ne sont pas requis lors de l'utilisation de certificats de production.</span><span class="sxs-lookup"><span data-stu-id="e7ded-140">The code and the accompanying class are not required when using production certificates.</span></span>  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7ded-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7ded-141">See Also</span></span>
