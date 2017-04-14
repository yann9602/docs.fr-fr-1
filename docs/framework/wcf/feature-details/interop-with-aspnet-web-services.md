---
title: "Interop&#233;rabilit&#233; avec les services Web ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Interop&#233;rabilit&#233; avec les services Web ASP.NET
L'interopérabilité entre les services Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et les services Web [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] peut être accomplie en s'assurant que les services implémentés à l'aide des deux technologies se conforment à la spécification WS\-I Basic Profile 1.1.Les services Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] qui se conforment à WS\-I Basic Profile 1.1 sont interopérables avec les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] grâce à l'utilisation de la liaison fournie par le système [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Utilisez l'option [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] d'ajout des attributs <xref:System.Web.Services.WebService> et <xref:System.Web.Services.WebMethodAttribute> à une interface plutôt qu'à une classe et d'écriture d'une classe pour implémenter l'interface, comme le montre l'exemple de code suivant.  
  
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
  
 L'utilisation de cette option est recommandée, car l'interface avec l'attribut <xref:System.Web.Services.WebService> constitue un contrat pour les opérations exécutées par le service qui peut être réutilisé avec différentes classes, qui peuvent implémenter ce même contrat de différentes façons.  
  
 Évitez d'utiliser l'attribut <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> pour router des messages vers des méthodes basées sur le nom qualifié complet de l'élément de corps du message SOAP plutôt que l'en\-tête HTTP `SOAPAction`.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise l'en\-tête HTTP `SOAPAction` pour acheminer les messages.  
  
 Le XML dans lequel <xref:System.Xml.Serialization.XmlSerializer> sérialise un type par défaut est sémantiquement identique au XML dans lequel <xref:System.Runtime.Serialization.DataContractSerializer> sérialise un type, à condition que l'espace de noms du XML soit défini explicitement.Lorsque vous définissez un type de données pour une utilisation avec les services Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] avant d'adopter [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], procédez comme suit :  
  
-   Définissez le type à l'aide des classes .NET Framework plutôt que XML Schema.  
  
-   Ajoutez uniquement <xref:System.SerializableAttribute> et <xref:System.Xml.Serialization.XmlRootAttribute> à la classe, en utilisant ce dernier pour définir explicitement l'espace de noms du type.N'ajoutez pas d'attribut supplémentaire à partir de l'espace de noms <xref:System.Xml.Serialization> pour contrôler la manière dont la classe .NET Framework sera traduite dans XML.  
  
-   En adoptant cette approche, vous devez être en mesure de créer ultérieurement les classes .NET dans des contrats de données avec l'ajout de <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> sans modifier de manière significative le XML dans lequel les classes sont sérialisées pour la transmission.Les types utilisés dans les messages par les services Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] peuvent être traités comme des contrats de données par les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ce qui produit, entre autres avantages, des applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] plus performantes.  
  
 Évitez d'utiliser les options d'authentification fournies par des services IIS \(Internet Information Services\).Les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne les prennent pas en charge.Si un service doit être sécurisé, utilisez les options fournies par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], car ces options sont fiables et sont basées sur des protocoles standard.  
  
## Impact sur les performances causé par le chargement de ServiceModel HttpModule  
 Dans le .NET Framework 3.0, `HttpModule` WCF a été installé dans le fichier Web.config racine pour que chaque application ASP.NET soit compatible WCF.Cela peut affecter les performances, vous pouvez donc supprimer  `ServiceModel` pour le fichier Web.config comme illustré dans l'exemple suivant.  
  
```  
<httpModules>  
    <remove name=”ServiceModel” />  
<httpModules/>  
  
```  
  
## Voir aussi  
 [Comment : configurer le service WCF pour interagir avec des clients du service Web ASP.NET](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)