---
title: PII Security Lockdown
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
caps.latest.revision: "25"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 39f805da7570b81ff1f6593e82f5d0a9310ee9c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="fd23c-102">PII Security Lockdown</span><span class="sxs-lookup"><span data-stu-id="fd23c-102">PII Security Lockdown</span></span>
<span data-ttu-id="fd23c-103">Cet exemple illustre les diverses fonctionnalités de sécurité des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="fd23c-103">This sample demonstrates how to control several security-related features of a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service by:</span></span>  
  
-   <span data-ttu-id="fd23c-104">Chiffrement des informations sensibles dans le fichier de configuration du service.</span><span class="sxs-lookup"><span data-stu-id="fd23c-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
-   <span data-ttu-id="fd23c-105">Verrouillage de certains éléments du fichier de configuration afin que les sous-répertoires de service imbriqués ne puissent pas se substituer aux paramètres.</span><span class="sxs-lookup"><span data-stu-id="fd23c-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
-   <span data-ttu-id="fd23c-106">Contrôle de l'enregistrement des informations d'identification personnelle (PII, Personally Identifiable Information) dans les journaux de suivi et de message.</span><span class="sxs-lookup"><span data-stu-id="fd23c-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fd23c-107">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fd23c-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fd23c-108">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="fd23c-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fd23c-109">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fd23c-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fd23c-110">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="fd23c-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="fd23c-111">Discussion</span><span class="sxs-lookup"><span data-stu-id="fd23c-111">Discussion</span></span>  
 <span data-ttu-id="fd23c-112">Chacune de ces fonctionnalités peut être utilisée séparément ou simultanément afin de contrôler les divers aspects relatifs à la sécurité des services.</span><span class="sxs-lookup"><span data-stu-id="fd23c-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="fd23c-113">Cet exemple ne constitue pas un guide définitif en matière de sécurisation des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd23c-113">This is not a definitive guide to securing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="fd23c-114">Les fichiers de configuration .NET Framework peuvent contenir des informations sensibles telles que les chaînes de connexion permettant de se connecter aux bases de données.</span><span class="sxs-lookup"><span data-stu-id="fd23c-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="fd23c-115">Dans le cadre de services partagés et hébergés par le Web, le chiffrement de ces informations dans le fichier de configuration des services concernés peut s'avérer souhaitable pour assurer leur protection en cas de consultation informelle.</span><span class="sxs-lookup"><span data-stu-id="fd23c-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="fd23c-116">.NET Framework 2.0 et ses versions ultérieures permettent de chiffrer certains passages des fichiers de configuration à l'aide de l'interface de programmation d'applications de protection des données Windows (Data Protection Application Programming Interface, DPAPI) ou du fournisseur de services de chiffrement RSA.</span><span class="sxs-lookup"><span data-stu-id="fd23c-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="fd23c-117">Le programme aspnet_regiis.exe peut chiffrer les sections choisies d'un fichier de configuration donné à l'aide de l'interface ou du fournisseur ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="fd23c-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="fd23c-118">Dans le cadre de scénarios hébergés par le Web, il est possible de placer ces services dans les sous-répertoires d'autres services.</span><span class="sxs-lookup"><span data-stu-id="fd23c-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="fd23c-119">La valeur par défaut sémantique définissant les valeurs de configuration permet aux fichiers de configuration figurant dans les répertoires imbriqués de se substituer aux valeurs de configuration figurant dans le répertoire parent.</span><span class="sxs-lookup"><span data-stu-id="fd23c-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="fd23c-120">Dans certaines situations et pour diverses raisons, il peut s'avérer préférable qu'une telle substitution ne soit pas possible.</span><span class="sxs-lookup"><span data-stu-id="fd23c-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="fd23c-121">La configuration des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge une fonctionnalité de verrouillage de valeurs de configuration. Cette fonctionnalité activée, la configuration imbriquée génère des exceptions lorsqu'un service imbriqué s'exécute à l'aide des valeurs de configuration substituées.</span><span class="sxs-lookup"><span data-stu-id="fd23c-121">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="fd23c-122">Cet exemple illustre comment contrôler la fonctionnalité d'enregistrement des informations d'identification personnelle connues, telles que le nom d'utilisateur et le mot de passe, dans les journaux de suivi et de message.</span><span class="sxs-lookup"><span data-stu-id="fd23c-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="fd23c-123">Par défaut, l'enregistrement des PII connues est désactivé. Toutefois, dans certaines situations, leur enregistrement peut s'avérer essentiel lors du débogage des applications.</span><span class="sxs-lookup"><span data-stu-id="fd23c-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="fd23c-124">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="fd23c-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="fd23c-125">En outre, cet exemple utilise l'enregistrement des suivis et des messages.</span><span class="sxs-lookup"><span data-stu-id="fd23c-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="fd23c-126">Pour plus d’informations, consultez la [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="fd23c-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="fd23c-127">Chiffrement des éléments de fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="fd23c-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="fd23c-128">Pour des raisons de sécurité, dans le cadre d'un environnement partagé avec hébergement Web, le chiffrement de certains éléments de configuration tels que les chaînes de connexion aux bases de données, susceptibles de contenir des informations sensibles, peut s'avérer souhaitable.</span><span class="sxs-lookup"><span data-stu-id="fd23c-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="fd23c-129">De tels éléments peuvent être chiffrés à l'aide de l'outil aspnet_regiis.exe figurant dans le dossier .NET Framework, WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span><span class="sxs-lookup"><span data-stu-id="fd23c-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="fd23c-130">Pour chiffrer les valeurs dans la section appSettings du fichier Web.config de l'exemple</span><span class="sxs-lookup"><span data-stu-id="fd23c-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1.  <span data-ttu-id="fd23c-131">Ouvrez une invite de commandes à l'aide de Démarrer->Exécuter....</span><span class="sxs-lookup"><span data-stu-id="fd23c-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="fd23c-132">Tapez dans `cmd` et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fd23c-132">Type in `cmd` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="fd23c-133">Naviguez jusqu'au répertoire .NET Framework actuel en publiant la commande suivante : `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span><span class="sxs-lookup"><span data-stu-id="fd23c-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3.  <span data-ttu-id="fd23c-134">Chiffrez les paramètres de configuration appSettings du dossier Web.config en publiant la commande suivante : `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="fd23c-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="fd23c-135">Vous trouverez plus d’informations sur le chiffrement des sections des fichiers de configuration en lisant un savoir-faire sur DPAPI dans la configuration d’ASP.NET ([création d’Applications ASP.NET sécurisées : authentification, autorisation et Communication sécurisée](http://go.microsoft.com/fwlink/?LinkId=95137)) et une procédure RSA dans la configuration d’ASP.NET ([Comment : chiffrer des Sections de Configuration dans ASP.NET 2.0 à l’aide de RSA](http://go.microsoft.com/fwlink/?LinkId=95138)).</span><span class="sxs-lookup"><span data-stu-id="fd23c-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](http://go.microsoft.com/fwlink/?LinkId=95137)) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](http://go.microsoft.com/fwlink/?LinkId=95138)).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="fd23c-136">Verrouillage des éléments de fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="fd23c-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="fd23c-137">Dans le cadre de services hébergés par le Web, il est possible de placer ces services dans les sous-répertoires d'autres services.</span><span class="sxs-lookup"><span data-stu-id="fd23c-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="fd23c-138">Dans ce genre de situation, les valeurs de configuration des services placés dans ces sous-répertoires sont calculées en examinant les valeurs du fichier Machine.config. Ces valeurs sont ensuite fusionnées avec les valeurs des éventuels fichiers Web.config figurant dans les répertoires parents en descendant la hiérarchie de l'arborescence de répertoires jusqu'au fichier Web.config du répertoire contenant les services concernés.</span><span class="sxs-lookup"><span data-stu-id="fd23c-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="fd23c-139">Le comportement par défaut de la plupart des éléments de configuration permet aux fichiers de configuration des sous-répertoires de se substituer aux valeurs définies dans leurs répertoires parents.</span><span class="sxs-lookup"><span data-stu-id="fd23c-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="fd23c-140">Dans certains cas, il peut s'avérer préférable d'empêcher une telle substitution.</span><span class="sxs-lookup"><span data-stu-id="fd23c-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="fd23c-141">Le .NET Framework propose une fonctionnalité permettant de verrouiller les éléments de configuration, provoquant ainsi la levée d'exception pendant l'exécution lorsque les fichiers de configuration des sous-répertoires tentent de se substituer aux éléments verrouillés.</span><span class="sxs-lookup"><span data-stu-id="fd23c-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="fd23c-142">Les éléments de configuration peuvent être verrouillés en spécifiant l'attribut `lockItem` pour un nœud du fichier de configuration. Par exemple, pour verrouiller le nœud CalculatorServiceBehavior afin que les services de calculatrice des fichiers de configuration imbriqués ne puissent pas modifier ce comportement, la configuration suivante peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="fd23c-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>   
          <serviceBehaviors>   
             <behavior name="CalculatorServiceBehavior" lockItem="true">   
               <serviceMetadata httpGetEnabled="True"/>   
               <serviceDebug includeExceptionDetailInFaults="False" />   
             </behavior>   
          </serviceBehaviors>   
       </behaviors>   
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="fd23c-143">Le verrouillage des éléments de configuration peut être plus spécifique.</span><span class="sxs-lookup"><span data-stu-id="fd23c-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="fd23c-144">La valeur à laquelle `lockElements` est appliqué peut être spécifiée sous la forme d'une liste d'éléments afin de verrouiller un ensemble d'éléments au sein d'une collection de sous-éléments.</span><span class="sxs-lookup"><span data-stu-id="fd23c-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="fd23c-145">La valeur à laquelle `lockAttributes` est appliqué peut être définie sous la forme d'une liste d'attributs pour verrouiller un ensemble d'attributs au sein d'un élément.</span><span class="sxs-lookup"><span data-stu-id="fd23c-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="fd23c-146">Une collection entière d'éléments ou d'attributs peut être verrouillée à l'exception d'une liste spécifiée au niveau des attributs `lockAllElementsExcept` ou `lockAllAttributesExcept` sur un nœud.</span><span class="sxs-lookup"><span data-stu-id="fd23c-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="fd23c-147">Configuration de l'enregistrement des informations d'identification personnelle</span><span class="sxs-lookup"><span data-stu-id="fd23c-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="fd23c-148">L'enregistrement des PII est contrôlé par deux commutateurs : paramètre à l'échelle de l'ordinateur situé dans le fichier Machine.config permettant à l'administrateur de cet ordinateur d'autoriser ou non leur enregistrement et paramètre d'application permettant aux administrateurs d'application d'activer ou non leur enregistrement pour chaque source dans les fichiers Web.config ou App.config.</span><span class="sxs-lookup"><span data-stu-id="fd23c-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="fd23c-149">Le paramètre à l'échelle de l'ordinateur est contrôlé en affectant à `enableLoggingKnownPii` la valeur `true` ou `false` au niveau de l'élément `machineSettings` du fichier Machine.config. Par exemple, le code suivant permet aux applications d'activer l'enregistrement des PII.</span><span class="sxs-lookup"><span data-stu-id="fd23c-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="fd23c-150">Le fichier Machine.config se trouve dans un emplacement par défaut : %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="fd23c-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="fd23c-151">Si l'attribut `enableLoggingKnownPii` n'est pas présent dans le fichier Machine.config, l'enregistrement des PII n'est pas autorisé.</span><span class="sxs-lookup"><span data-stu-id="fd23c-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="fd23c-152">L'enregistrement des PII pour une application est activé en affectant à l'attribut `logKnownPii` de l'élément source la valeur `true` ou `false` dans les fichiers Web.config ou App.config.</span><span class="sxs-lookup"><span data-stu-id="fd23c-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="fd23c-153">Par exemple, le code suivant active l'enregistrement des PII à la fois pour l'enregistrement des messages et des suivis.</span><span class="sxs-lookup"><span data-stu-id="fd23c-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel.MessageLogging" logKnownPii="true">  
                <listeners>   
                ...   
                </listeners>  
            </source>  
            <source name="System.ServiceModel" switchValue="Verbose, ActivityTracing">  
            <listeners>  
        ...   
            </listeners>  
            </source>  
        </sources>  
    </system.diagnostics>  
</configuration>  
```  
  
 <span data-ttu-id="fd23c-154">Si l'attribut `logKnownPii` n'est pas spécifié, les PII ne sont pas enregistrées.</span><span class="sxs-lookup"><span data-stu-id="fd23c-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="fd23c-155">Les PII sont uniquement enregistrées si  `enableLoggingKnownPii` a la valeur `true` et si `logKnownPii` a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="fd23c-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd23c-156">System.Diagnostics ignore tous les attributs de toutes les sources, sauf le premier attribut répertorié dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="fd23c-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="fd23c-157">L'ajout de l'attribut `logKnownPii` à la seconde source du fichier de configuration est sans effet.</span><span class="sxs-lookup"><span data-stu-id="fd23c-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fd23c-158">L'exécution de cet exemple implique de modifier manuellement le fichier Machine.config. Vous devez faire très attention lorsque vous modifiez le fichier Machine.config, toutes valeurs ou syntaxes incorrectes étant susceptibles d'empêcher l'exécution des applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd23c-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="fd23c-159">Les éléments de fichier de configuration peuvent également être chiffrés à l'aide de DPAPI et RSA.</span><span class="sxs-lookup"><span data-stu-id="fd23c-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="fd23c-160">Pour plus d'informations, consultez les liens suivants :</span><span class="sxs-lookup"><span data-stu-id="fd23c-160">For more information, see the following links:</span></span>  
  
-   [<span data-ttu-id="fd23c-161">Génération d’Applications ASP.NET sécurisées : Authentification, l’autorisation et Communication sécurisée</span><span class="sxs-lookup"><span data-stu-id="fd23c-161">Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication</span></span>](http://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [<span data-ttu-id="fd23c-162">Comment : Chiffrer des Sections de Configuration dans ASP.NET 2.0 à l’aide de RSA</span><span class="sxs-lookup"><span data-stu-id="fd23c-162">How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA</span></span>](http://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fd23c-163">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="fd23c-163">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="fd23c-164">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fd23c-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="fd23c-165">Modifiez le fichier Machine.config pour affecter à l'attribut `enableLoggingKnownPii` la valeur `true` en ajoutant les nœuds parents, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fd23c-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3.  <span data-ttu-id="fd23c-166">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fd23c-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="fd23c-167">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fd23c-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="fd23c-168">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="fd23c-168">To clean up the sample</span></span>  
  
1.  <span data-ttu-id="fd23c-169">Modifiez le fichier Machine.config pour affecter à l'attribut `enableLoggingKnownPii` la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="fd23c-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd23c-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd23c-170">See Also</span></span>  
 [<span data-ttu-id="fd23c-171">Exemples d’analyse AppFabric</span><span class="sxs-lookup"><span data-stu-id="fd23c-171">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
