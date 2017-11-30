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
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Anticipation de l‘adoption de Windows Communication Foundation : faciliter l‘intégration future
Si vous utilisez ASP.NET aujourd'hui et prévoyez d'utiliser [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans le futur, cette rubrique fournit des informations permettant de garantir que les nouveaux services Web ASP.NET fonctionneront correctement avec les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="general-recommendations"></a>Recommandations générales  
 Adoptez ASP.NET 2.0 pour les nouveaux services. Vous pourrez ainsi accéder aux améliorations et enrichissements de la nouvelle version. Toutefois, l'utilisation des composants ASP.NET 2.0 avec des composants [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans la même application sera également possible.  
  
## <a name="protocols"></a>Protocoles  
 Utilisez la nouvelle fonctionnalité d'ASP.NET 2.0 pour valider la conformité au profil WS-I Basic Profile 1.1 :  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 Les services Web ASP.NET conformes au profil WS-I Basic Profile 1.1 seront interopérables avec les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en utilisant la liaison prédéfinie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.BasicHttpBinding>.  
  
## <a name="service-development"></a>Développement des services  
 Évitez d'utiliser l'attribut <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> pour router des messages vers des méthodes basées sur le nom qualifié complet de l'élément de corps du message SOAP plutôt que l'en-tête HTTP SOAPAction. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise l'en-tête HTTP SOAPAction pour acheminer les messages.  
  
## <a name="data-representation"></a>Représentation des données  
 Le XML dans lequel <xref:System.Xml.Serialization.XmlSerializer> sérialise un type par défaut est sémantiquement identique au XML dans lequel <xref:System.Runtime.Serialization.DataContractSerializer> sérialise un type, à condition que l'espace de noms du XML soit défini explicitement. Lorsque vous définissez un type de données à utiliser avec les services Web ASP.NET en prévision de l'adoption future de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], procédez comme suit :  
  
1.  Définissez le type à l'aide des classes .NET Framework plutôt que XML Schema.  
  
2.  Ajoutez uniquement <xref:System.SerializableAttribute> et <xref:System.Xml.Serialization.XmlRootAttribute> à la classe, en utilisant ce dernier pour définir explicitement l'espace de noms du type. N'ajoutez pas d'attribut supplémentaire à partir de l'espace de noms <xref:System.Xml.Serialization> pour contrôler la manière dont la classe .NET Framework sera traduite dans XML.  
  
 En adoptant cette approche, vous devez être en mesure de créer ultérieurement les classes .NET dans des contrats de données avec l'ajout de <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> sans modifier de manière significative le XML dans lequel les classes sont sérialisées pour la transmission. Les types utilisés dans les messages par les services Web ASP.NET pourront être traités comme des contrats de données par les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], en offrant, entre autres avantages, de meilleures performances dans les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="security"></a>Sécurité  
 Évitez d'utiliser les options d'authentification fournies par des services IIS (Internet Information Services). Les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne les prennent pas en charge. Si un service doit être sécurisé, utilisez les options fournies par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], car ces options sont plus complètes et sont basées sur des protocoles standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Anticipation de l’adoption de Windows Communication Foundation : faciliter la Future Migration](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
