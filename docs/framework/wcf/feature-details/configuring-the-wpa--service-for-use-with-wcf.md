---
title: Configuration du service d'activation de processus de Windows pour son utilisation dans Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12df9e3760774b4dc8d4e8f73a09df5e79c2453e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="b3864-102">Configuration du service d'activation de processus de Windows pour son utilisation dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="b3864-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="b3864-103">Cette rubrique décrit les étapes requises pour configurer le service d'activation de processus de Windows (également appelé service WAS) dans [!INCLUDE[wv](../../../../includes/wv-md.md)] pour héberger des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] qui ne communiquent pas sur des protocoles réseau HTTP.</span><span class="sxs-lookup"><span data-stu-id="b3864-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in [!INCLUDE[wv](../../../../includes/wv-md.md)] to host [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="b3864-104">Les sections suivantes définissent les étapes pour cette configuration :</span><span class="sxs-lookup"><span data-stu-id="b3864-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="b3864-105">Installez (ou vérifiez l'installation) les composants d'activation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requis.</span><span class="sxs-lookup"><span data-stu-id="b3864-105">Install (or confirm the installation of) the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] activation components required.</span></span>  
  
-   <span data-ttu-id="b3864-106">Créez un site WAS avec les liaisons de protocole réseau que vous souhaitez utiliser ou ajoutez un nouveau protocole qui crée une liaison vers un site existant.</span><span class="sxs-lookup"><span data-stu-id="b3864-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
-   <span data-ttu-id="b3864-107">Créez une application pour héberger vos services et permettre à cette application d'utiliser les protocoles réseau requis.</span><span class="sxs-lookup"><span data-stu-id="b3864-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
-   <span data-ttu-id="b3864-108">Générez un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui expose un point de terminaison non http.</span><span class="sxs-lookup"><span data-stu-id="b3864-108">Build a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="b3864-109">Configuration d'un site avec des liaisons non HTTP</span><span class="sxs-lookup"><span data-stu-id="b3864-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="b3864-110">Pour utiliser une liaison non HTTP avec le service WAS, la liaison de site doit être ajoutée à la configuration WAS.</span><span class="sxs-lookup"><span data-stu-id="b3864-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="b3864-111">Le magasin de configurations pour le service WAS est le fichier applicationHost.config situé dans le répertoire %windir%\system32\inetsrv\config.</span><span class="sxs-lookup"><span data-stu-id="b3864-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="b3864-112">Ce magasin de configurations est partagé à la fois par le service WAS et le service IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="b3864-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="b3864-113">applicationHost.config est un fichier texte XML qui peut être ouvert avec un éditeur de texte standard (tel que le Bloc-notes).</span><span class="sxs-lookup"><span data-stu-id="b3864-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="b3864-114">Toutefois, l'outil de configuration de la ligne de commande [!INCLUDE[iisver](../../../../includes/iisver-md.md)] (appcmd.exe) est la meilleure méthode pour ajouter des liaisons de site non HTTP.</span><span class="sxs-lookup"><span data-stu-id="b3864-114">However, the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="b3864-115">La commande suivante ajoute une liaison de site net.tcp au site web par défaut à l’aide de appcmd.exe (cette commande est entrée comme une ligne unique).</span><span class="sxs-lookup"><span data-stu-id="b3864-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="b3864-116">Cette commande ajoute la nouvelle liaison net.tcp au site web par défaut en ajoutant la ligne indiquée ci-dessous au fichier applicationHost.config.</span><span class="sxs-lookup"><span data-stu-id="b3864-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="b3864-117">Activation de l'utilisation des protocoles non HTTP par une application</span><span class="sxs-lookup"><span data-stu-id="b3864-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="b3864-118">Vous pouvez activer ou désactiver le réseau individuelles, protocolsat niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="b3864-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="b3864-119">La commande suivante montre comment activer à la fois les protocoles HTTP et net.tcp pour une application qui s'exécute dans le `Default Web Site`.</span><span class="sxs-lookup"><span data-stu-id="b3864-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="b3864-120">La liste des protocoles actifs permettre également être définie dans le \<applicationDefaults > élément de la configuration du site XML stockée dans ApplicationHost.config.</span><span class="sxs-lookup"><span data-stu-id="b3864-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="b3864-121">Le code XML suivant issu du fichier applicationHost.config illustre un site lié à la fois à des protocoles HTTP et non HTTP.</span><span class="sxs-lookup"><span data-stu-id="b3864-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="b3864-122">La configuration supplémentaire requise pour la prise en charge de protocoles non HTTP est appelée avec des commentaires.</span><span class="sxs-lookup"><span data-stu-id="b3864-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
    <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
    </application>  
       <bindings>  
            //The following two lines are added by the command.  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile   
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging   
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults   
      applicationPool="DefaultAppPool"   
      //The following line is inserted by the command.  
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 <span data-ttu-id="b3864-123">Si vous tentez d'activer un service en utilisant WAS pour l'activation non-HTTP et vous n'avez pas installé et configuré WAS, l'erreur suivante s'affiche :</span><span class="sxs-lookup"><span data-stu-id="b3864-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="b3864-124">Si cette erreur s'affiche, assurez-vous que WAS pour l'activation non HTTP est installé et configuré correctement.</span><span class="sxs-lookup"><span data-stu-id="b3864-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b3864-125">[Comment : installer et configurer les composants d’Activation WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="b3864-125"> [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="b3864-126">Génération d'un service WCF qui utilise le service WAS pour l'activation non HTTP</span><span class="sxs-lookup"><span data-stu-id="b3864-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="b3864-127">Une fois que vous effectuez les étapes pour installer et configurer le service WAS (consultez [Comment : installer et configurer les composants d’Activation WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuration d’un service pour utiliser les services WAS pour l’activation est similaire à la configuration d’un service hébergé dans IIS.</span><span class="sxs-lookup"><span data-stu-id="b3864-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="b3864-128">Pour obtenir des instructions détaillées sur la création d’un objet activé par le service WAS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de service, consultez [Comment : héberger un Service WCF dans WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span><span class="sxs-lookup"><span data-stu-id="b3864-128">For detailed instructions about building a WAS-activated [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3864-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3864-129">See Also</span></span>  
 [<span data-ttu-id="b3864-130">Hébergement dans le service d’activation des processus Windows</span><span class="sxs-lookup"><span data-stu-id="b3864-130">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 [<span data-ttu-id="b3864-131">Fonctionnalités d’hébergement de Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="b3864-131">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
