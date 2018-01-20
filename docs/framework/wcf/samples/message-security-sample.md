---
title: Message Security, exemple
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
caps.latest.revision: "33"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: efad1940def2c27d57bb1e9da28e51362de5b237
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="message-security-sample"></a><span data-ttu-id="fa843-102">Message Security, exemple</span><span class="sxs-lookup"><span data-stu-id="fa843-102">Message Security Sample</span></span>
<span data-ttu-id="fa843-103">Cet exemple montre comment implémenter une application qui utilise `basicHttpBinding` et la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="fa843-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="fa843-104">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="fa843-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa843-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="fa843-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fa843-106">Le mode de sécurité de `basicHttpBinding` peut avoir les valeurs suivantes : `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` et `None`.</span><span class="sxs-lookup"><span data-stu-id="fa843-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="fa843-107">Dans l'exemple de fichier App.config de service suivant, la définition de point de terminaison spécifie `basicHttpBinding` et référence une configuration de liaison appelée `Binding1`, tel qu'indiqué dans l'exemple de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="fa843-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>   …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="fa843-108">Les jeux de configuration de liaison le `mode` attribut de la [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) à `Message` et définit les `clientCredentialType` attribut de la [ \<message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)à `Certificate` comme indiqué dans l’exemple de configuration suivantes :</span><span class="sxs-lookup"><span data-stu-id="fa843-108">The binding configuration sets the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="fa843-109">Le certificat que le service utilise pour s'authentifier auprès du client est défini dans la section des comportements du fichier de configuration située sous l'élément `serviceCredentials`.</span><span class="sxs-lookup"><span data-stu-id="fa843-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="fa843-110">Le mode de validation qui s'applique au certificat que le client utilise pour s'authentifier auprès du service est également défini dans la section des comportements située sous l'élément `clientCertificate`.</span><span class="sxs-lookup"><span data-stu-id="fa843-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"   
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication   
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="fa843-111">Les mêmes détails sur la liaison et la sécurité sont spécifiés dans le fichier de configuration client.</span><span class="sxs-lookup"><span data-stu-id="fa843-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="fa843-112">L'identité de l'appelant s'affiche dans la fenêtre de console du service à l'aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="fa843-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  
  
```  
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```  
  
 <span data-ttu-id="fa843-113">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="fa843-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fa843-114">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="fa843-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="fa843-115">Pour configurer et générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="fa843-115">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="fa843-116">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fa843-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="fa843-117">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fa843-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="fa843-118">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="fa843-118">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="fa843-119">Exécutez Setup.bat à partir du dossier d'installation de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="fa843-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="fa843-120">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="fa843-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fa843-121">Le fichier de commandes Setup.bat est conçu pour s'exécuter à partir d'une invite de commandes du Kit de développement Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="fa843-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="fa843-122">La variable d'environnement du Kit de développement MS SDK doit pointer vers le répertoire d'installation du Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="fa843-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="fa843-123">Cette variable est définie automatiquement dans une invite de commandes du Kit de développement logiciel Windows.</span><span class="sxs-lookup"><span data-stu-id="fa843-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2.  <span data-ttu-id="fa843-124">Exécutez l'application de service à partir de \service\bin.</span><span class="sxs-lookup"><span data-stu-id="fa843-124">Run the service application from \service\bin.</span></span>  
  
3.  <span data-ttu-id="fa843-125">Exécutez l'application cliente à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="fa843-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="fa843-126">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="fa843-126">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="fa843-127">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="fa843-127">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
5.  <span data-ttu-id="fa843-128">Supprimez les certificats en exécutant Cleanup.bat une fois l'exemple terminé.</span><span class="sxs-lookup"><span data-stu-id="fa843-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="fa843-129">D'autres exemples de sécurité utilisent ces mêmes certificats.</span><span class="sxs-lookup"><span data-stu-id="fa843-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="fa843-130">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="fa843-130">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="fa843-131">Créez un répertoire sur l'ordinateur de service destiné aux fichiers binaires de service.</span><span class="sxs-lookup"><span data-stu-id="fa843-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2.  <span data-ttu-id="fa843-132">Copiez les fichiers programme du service dans le répertoire de service sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="fa843-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="fa843-133">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportClientCert.bat sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="fa843-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3.  <span data-ttu-id="fa843-134">Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.</span><span class="sxs-lookup"><span data-stu-id="fa843-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4.  <span data-ttu-id="fa843-135">Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="fa843-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="fa843-136">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.</span><span class="sxs-lookup"><span data-stu-id="fa843-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="fa843-137">Sur le serveur, exécutez `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="fa843-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="fa843-138">En cours d’exécution `setup.bat` avec la `service` argument crée un certificat de service portant le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé Service.cer.</span><span class="sxs-lookup"><span data-stu-id="fa843-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="fa843-139">Modifier Service.exe.config pour refléter le nouveau nom de certificat (dans le `findValue` d’attribut dans le [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) élément) qui est le même que le nom de domaine complet de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fa843-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="fa843-140">Modifiez également la valeur de l'adresse de base afin de remplacer localhost par un nom d'ordinateur complet`.`</span><span class="sxs-lookup"><span data-stu-id="fa843-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7.  <span data-ttu-id="fa843-141">Copiez le fichier Service.cer du répertoire de service dans le répertoire client sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="fa843-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8.  <span data-ttu-id="fa843-142">Sur le client, exécutez `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="fa843-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="fa843-143">L'exécution de `setup.bat` à l'aide de l'argument `client` crée un certificat client appelé client.com, puis exporte ce certificat vers un fichier nommé Client.cer.</span><span class="sxs-lookup"><span data-stu-id="fa843-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="fa843-144">Dans le fichier Client.exe.config sur l'ordinateur client, modifiez la valeur d'adresse du point de terminaison pour qu'il corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="fa843-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="fa843-145">Pour ce faire, remplacez localhost par le nom de domaine complet du serveur.</span><span class="sxs-lookup"><span data-stu-id="fa843-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="fa843-146">Également modifier le `findValue` attribut de la [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) le nouveau nom de certificat de service qui est le nom de domaine complet du serveur.</span><span class="sxs-lookup"><span data-stu-id="fa843-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="fa843-147">Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="fa843-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="fa843-148">Sur le client, exécutez ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="fa843-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="fa843-149">Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="fa843-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="fa843-150">Sur le serveur, exécutez ImportClientCert.bat. Cette opération importe le certificat client du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="fa843-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="fa843-151">Sur l'ordinateur de service, exécutez Service.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="fa843-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="fa843-152">Sur l'ordinateur du client, lancez Client.exe à partir d'une fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="fa843-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1.  <span data-ttu-id="fa843-153">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="fa843-153">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="fa843-154">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="fa843-154">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="fa843-155">Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.</span><span class="sxs-lookup"><span data-stu-id="fa843-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fa843-156">Ce script ne supprime pas les certificats de service figurant sur le client lorsque l'exemple est exécuté sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="fa843-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="fa843-157">Si vous avez exécuté des exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] qui utilisent des certificats sur plusieurs ordinateurs, assurez-vous d'effacer les certificats de service installés dans le magasin CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="fa843-157">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="fa843-158">Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="fa843-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fa843-159">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fa843-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fa843-160">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="fa843-160">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fa843-161">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fa843-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fa843-162">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="fa843-162">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
  
## <a name="see-also"></a><span data-ttu-id="fa843-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa843-163">See Also</span></span>
