---
title: "Interopérabilité avec les services Web ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef174f457114003e5b2783b50040424d9a96945c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="6e18a-102">Interopérabilité avec les services Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6e18a-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="6e18a-103">L'interopérabilité entre les services Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et les services Web [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] peut être accomplie en s'assurant que les services implémentés à l'aide des deux technologies se conforment à la spécification WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="6e18a-103">Interoperability between [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="6e18a-104">Les services Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] qui se conforment à WS-I Basic Profile 1.1 sont interopérables avec les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] grâce à l'utilisation de la liaison fournie par le système [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="6e18a-104">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services that conform to WS-I Basic Profile 1.1 are interoperable with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients by using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="6e18a-105">Utilisez l'option [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] d'ajout des attributs <xref:System.Web.Services.WebService> et <xref:System.Web.Services.WebMethodAttribute> à une interface plutôt qu'à une classe et d'écriture d'une classe pour implémenter l'interface, comme le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="6e18a-105">Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```  
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="6e18a-106">L'utilisation de cette option est recommandée, car l'interface avec l'attribut <xref:System.Web.Services.WebService> constitue un contrat pour les opérations exécutées par le service qui peut être réutilisé avec différentes classes, qui peuvent implémenter ce même contrat de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="6e18a-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="6e18a-107">Évitez d'utiliser l'attribut <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> pour router des messages vers des méthodes basées sur le nom qualifié complet de l'élément de corps du message SOAP plutôt que l'en-tête HTTP `SOAPAction`.</span><span class="sxs-lookup"><span data-stu-id="6e18a-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6e18a-108"> utilise l'en-tête HTTP `SOAPAction` pour acheminer les messages.</span><span class="sxs-lookup"><span data-stu-id="6e18a-108"> uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="6e18a-109">Le XML dans lequel <xref:System.Xml.Serialization.XmlSerializer> sérialise un type par défaut est sémantiquement identique au XML dans lequel <xref:System.Runtime.Serialization.DataContractSerializer> sérialise un type, à condition que l'espace de noms du XML soit défini explicitement.</span><span class="sxs-lookup"><span data-stu-id="6e18a-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="6e18a-110">Lors de la définition d’un type de données pour une utilisation avec [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web services en prévision de l’adoption de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6e18a-110">When defining a data type for use with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web services in anticipation of adopting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], do the following:</span></span>  
  
-   <span data-ttu-id="6e18a-111">Définissez le type à l'aide des classes .NET Framework plutôt que XML Schema.</span><span class="sxs-lookup"><span data-stu-id="6e18a-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
-   <span data-ttu-id="6e18a-112">Ajoutez uniquement <xref:System.SerializableAttribute> et <xref:System.Xml.Serialization.XmlRootAttribute> à la classe, en utilisant ce dernier pour définir explicitement l'espace de noms du type.</span><span class="sxs-lookup"><span data-stu-id="6e18a-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="6e18a-113">N'ajoutez pas d'attribut supplémentaire à partir de l'espace de noms <xref:System.Xml.Serialization> pour contrôler la manière dont la classe .NET Framework sera traduite dans XML.</span><span class="sxs-lookup"><span data-stu-id="6e18a-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
-   <span data-ttu-id="6e18a-114">En adoptant cette approche, vous devez être en mesure de créer ultérieurement les classes .NET dans des contrats de données avec l'ajout de <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> sans modifier de manière significative le XML dans lequel les classes sont sérialisées pour la transmission.</span><span class="sxs-lookup"><span data-stu-id="6e18a-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="6e18a-115">Les types utilisés dans les messages par les services Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] peuvent être traités comme des contrats de données par les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ce qui produit, entre autres avantages, des applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] plus performantes.</span><span class="sxs-lookup"><span data-stu-id="6e18a-115">The types used in messages by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services can be processed as data contracts by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications, yielding, among other benefits, better performance in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
 <span data-ttu-id="6e18a-116">Évitez d'utiliser les options d'authentification fournies par des services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="6e18a-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="6e18a-117">Les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne les prennent pas en charge.</span><span class="sxs-lookup"><span data-stu-id="6e18a-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients do not support them.</span></span> <span data-ttu-id="6e18a-118">Si un service doit être sécurisé, utilisez les options fournies par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], car ces options sont fiables et sont basées sur des protocoles standard.</span><span class="sxs-lookup"><span data-stu-id="6e18a-118">If a service must be secured, use the options provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="6e18a-119">Impact sur les performances causé par le chargement de ServiceModel HttpModule</span><span class="sxs-lookup"><span data-stu-id="6e18a-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="6e18a-120">Dans le .NET Framework 3.0, `HttpModule` WCF a été installé dans le fichier Web.config racine pour que chaque application ASP.NET soit compatible WCF.</span><span class="sxs-lookup"><span data-stu-id="6e18a-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="6e18a-121">Cela peut affecter les performances, vous pouvez donc supprimer  `ServiceModel` pour le fichier Web.config comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="6e18a-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e18a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e18a-122">See Also</span></span>  
 [<span data-ttu-id="6e18a-123">Guide pratique pour configurer le service WCF pour interagir avec des clients du service web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6e18a-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
