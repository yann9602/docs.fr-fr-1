---
title: "Anticipation de l‘adoption de Windows Communication Foundation : faciliter l‘intégration future"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8f60b2566895acfd7d2b749729fab9c3f5deb20c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="6a5e0-102">Anticipation de l‘adoption de Windows Communication Foundation : faciliter l‘intégration future</span><span class="sxs-lookup"><span data-stu-id="6a5e0-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>
<span data-ttu-id="6a5e0-103">Si vous utilisez ASP.NET aujourd'hui et prévoyez d'utiliser [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans le futur, cette rubrique fournit des informations permettant de garantir que les nouveaux services Web ASP.NET fonctionneront correctement avec les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a5e0-103">If you use ASP.NET today, and anticipate using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="6a5e0-104">Recommandations générales</span><span class="sxs-lookup"><span data-stu-id="6a5e0-104">General Recommendations</span></span>  
 <span data-ttu-id="6a5e0-105">Adoptez ASP.NET 2.0 pour les nouveaux services.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-105">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="6a5e0-106">Vous pourrez ainsi accéder aux améliorations et enrichissements de la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-106">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="6a5e0-107">Toutefois, l'utilisation des composants ASP.NET 2.0 avec des composants [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans la même application sera également possible.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-107">However, it will also allow for the possibility of using ASP.NET 2.0 components together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="6a5e0-108">Protocoles</span><span class="sxs-lookup"><span data-stu-id="6a5e0-108">Protocols</span></span>  
 <span data-ttu-id="6a5e0-109">Utilisez la nouvelle fonctionnalité d'ASP.NET 2.0 pour valider la conformité au profil WS-I Basic Profile 1.1 :</span><span class="sxs-lookup"><span data-stu-id="6a5e0-109">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="6a5e0-110">Les services Web ASP.NET conformes au profil WS-I Basic Profile 1.1 seront interopérables avec les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en utilisant la liaison prédéfinie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-110">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients by using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="6a5e0-111">Développement des services</span><span class="sxs-lookup"><span data-stu-id="6a5e0-111">Service Development</span></span>  
 <span data-ttu-id="6a5e0-112">Évitez d'utiliser l'attribut <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> pour router des messages vers des méthodes basées sur le nom qualifié complet de l'élément de corps du message SOAP plutôt que l'en-tête HTTP SOAPAction.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-112">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6a5e0-113"> utilise l'en-tête HTTP SOAPAction pour acheminer les messages.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-113"> uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="6a5e0-114">Représentation des données</span><span class="sxs-lookup"><span data-stu-id="6a5e0-114">Data Representation</span></span>  
 <span data-ttu-id="6a5e0-115">Le XML dans lequel <xref:System.Xml.Serialization.XmlSerializer> sérialise un type par défaut est sémantiquement identique au XML dans lequel <xref:System.Runtime.Serialization.DataContractSerializer> sérialise un type, à condition que l'espace de noms du XML soit défini explicitement.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-115">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="6a5e0-116">Lorsque vous définissez un type de données à utiliser avec les services Web ASP.NET en prévision de l'adoption future de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6a5e0-116">When defining a data type for use with ASP.NET Web services in anticipation of adopting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, do the following:</span></span>  
  
1.  <span data-ttu-id="6a5e0-117">Définissez le type à l'aide des classes .NET Framework plutôt que XML Schema.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-117">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2.  <span data-ttu-id="6a5e0-118">Ajoutez uniquement <xref:System.SerializableAttribute> et <xref:System.Xml.Serialization.XmlRootAttribute> à la classe, en utilisant ce dernier pour définir explicitement l'espace de noms du type.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-118">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="6a5e0-119">N'ajoutez pas d'attribut supplémentaire à partir de l'espace de noms <xref:System.Xml.Serialization> pour contrôler la manière dont la classe .NET Framework sera traduite dans XML.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-119">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="6a5e0-120">En adoptant cette approche, vous devez être en mesure de créer ultérieurement les classes .NET dans des contrats de données avec l'ajout de <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> sans modifier de manière significative le XML dans lequel les classes sont sérialisées pour la transmission.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-120">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="6a5e0-121">Les types utilisés dans les messages par les services Web ASP.NET pourront être traités comme des contrats de données par les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], en offrant, entre autres avantages, de meilleures performances dans les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a5e0-121">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications, yielding, amongst other benefits, better performance in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="6a5e0-122">Sécurité</span><span class="sxs-lookup"><span data-stu-id="6a5e0-122">Security</span></span>  
 <span data-ttu-id="6a5e0-123">Évitez d'utiliser les options d'authentification fournies par des services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="6a5e0-123">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="6a5e0-124">Les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne les prennent pas en charge.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-124">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients do not support them.</span></span> <span data-ttu-id="6a5e0-125">Si un service doit être sécurisé, utilisez les options fournies par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], car ces options sont plus complètes et sont basées sur des protocoles standard.</span><span class="sxs-lookup"><span data-stu-id="6a5e0-125">If a service needs to be secured, use the options provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5e0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a5e0-126">See Also</span></span>  
 [<span data-ttu-id="6a5e0-127">Anticipation de l’adoption de Windows Communication Foundation : faciliter la Future Migration</span><span class="sxs-lookup"><span data-stu-id="6a5e0-127">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
