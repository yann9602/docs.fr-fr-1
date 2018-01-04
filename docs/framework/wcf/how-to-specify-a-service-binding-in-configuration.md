---
title: "Comment : spécifier une liaison de service dans la configuration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea54b2f84c9de233ff2560795dc97f79c15aa0af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a><span data-ttu-id="0c5a1-102">Comment : spécifier une liaison de service dans la configuration</span><span class="sxs-lookup"><span data-stu-id="0c5a1-102">How to: Specify a Service Binding in Configuration</span></span>
<span data-ttu-id="0c5a1-103">Dans cet exemple, un contrat `ICalculator` est défini pour un service de calculatrice de base, le service est implémenté dans la classe `CalculatorService`, puis son point de terminaison est configuré dans le fichier Web.config, où il est spécifié que le service utilise <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="0c5a1-103">In this example, an `ICalculator` contract is defined for a basic calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is configured in the Web.config file, where it is specified that the service uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="0c5a1-104">Pour obtenir une description de la configuration de ce service à l’aide de code au lieu d’une configuration, consultez [Comment : spécifier une liaison de Service dans le Code](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="0c5a1-104">For a description of how to configure this service using code instead of a configuration, see [How to: Specify a Service Binding in Code](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).</span></span>  
  
 <span data-ttu-id="0c5a1-105">Il est généralement conseillé de spécifier de façon déclarative les informations de liaison et d’adresse dans la configuration plutôt que de manière impérative dans le code.</span><span class="sxs-lookup"><span data-stu-id="0c5a1-105">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="0c5a1-106">La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service.</span><span class="sxs-lookup"><span data-stu-id="0c5a1-106">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="0c5a1-107">Plus généralement, le fait de laisser les informations de liaison et d’adresse hors du code leur permet de changer sans nécessiter de recompilation ou de redéploiement de l’application.</span><span class="sxs-lookup"><span data-stu-id="0c5a1-107">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="0c5a1-108">Toutes les étapes de configuration suivantes peuvent être entreprises à l’aide de la [l’outil Éditeur de Configuration (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0c5a1-108">All of the following configuration steps can be undertaken using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="0c5a1-109">Pour la copie de la source de cet exemple, consultez [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0c5a1-109">For the source copy of this example, see [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).</span></span>  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a><span data-ttu-id="0c5a1-110">Pour spécifier le BasicHttpBinding à utiliser pour configurer le service</span><span class="sxs-lookup"><span data-stu-id="0c5a1-110">To specify the BasicHttpBinding to use to configure the service</span></span>  
  
1.  <span data-ttu-id="0c5a1-111">Définissez un contrat de service pour le type de service.</span><span class="sxs-lookup"><span data-stu-id="0c5a1-111">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2.  <span data-ttu-id="0c5a1-112">Implémentez le contrat de service dans une classe de service.</span><span class="sxs-lookup"><span data-stu-id="0c5a1-112">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  <span data-ttu-id="0c5a1-113">Les informations de liaison ou d’adresse ne sont pas spécifiées dans l’implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="0c5a1-113">Address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="0c5a1-114">De plus, il n'est pas nécessaire d'écrire du code pour extraire ces informations du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0c5a1-114">Also, code does not have to be written to fetch that information from the configuration file.</span></span>  
  
3.  <span data-ttu-id="0c5a1-115">Créez un fichier Web.config pour configurer un point de terminaison pour le `CalculatorService` qui utilise le <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="0c5a1-115">Create a Web.config file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <-- Leave the address blank to be populated by default-->  
            <--from the hosting environment,in this case IIS, so -->  
            <-- the address will just be that of the IIS Virtual -->  
            <--Directory.-->  
                address=""   
            <--Specify the binding type -->  
                binding="wsHttpBinding"  
            <--Specify the binding configuration name for that -->  
            <--binding type. This is optional but useful if you  -->  
            <--want to modify the properties of the binding. -->  
            <--The bindingConfiguration name Binding1 is defined  -->  
            <--below in the bindings element.  -->  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <-- Binding property values can be modified here. -->  
              <--See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  <span data-ttu-id="0c5a1-116">Créez un fichier Service.svc qui contient la ligne suivante et placez-le dans votre répertoire virtuel des services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="0c5a1-116">Create a Service.svc file that contains the following line and place it in your Internet Information Services (IIS) virtual directory.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="0c5a1-117">Pour modifier les valeurs par défaut des propriétés de liaison</span><span class="sxs-lookup"><span data-stu-id="0c5a1-117">To modify the default values of the binding properties</span></span>  
  
1.  <span data-ttu-id="0c5a1-118">Pour modifier l’une des valeurs de propriété par défaut de la <xref:System.ServiceModel.WSHttpBinding>, créez un nouveau nom de configuration de liaison - `<binding name="Binding1">` - dans le [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) élément et définissez les nouvelles valeurs pour les attributs de la Dans cet élément de liaison de liaison.</span><span class="sxs-lookup"><span data-stu-id="0c5a1-118">To modify one of the default property values of the <xref:System.ServiceModel.WSHttpBinding>, create a new binding configuration name - `<binding name="Binding1">` - within the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element and set the new values for the attributes of the binding in this binding element.</span></span> <span data-ttu-id="0c5a1-119">Par exemple, pour modifier les valeurs par défaut de délai d'attente d'ouverture et de fermeture de 1 minute à 2 minutes, ajoutez le code suivant au fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0c5a1-119">For example, to change the default open and close timeout values of 1 minute to 2 minutes, add the following to the configuration file.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0c5a1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c5a1-120">See Also</span></span>  
 [<span data-ttu-id="0c5a1-121">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="0c5a1-121">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="0c5a1-122">Spécification d’une adresse de point de terminaison</span><span class="sxs-lookup"><span data-stu-id="0c5a1-122">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
