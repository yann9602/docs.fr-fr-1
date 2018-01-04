---
title: "Anticipation de l‘adoption de Windows Communication Foundation : faciliter la future migration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76770eff76a7a641ee853f314b5d2c14a56737c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Anticipation de l‘adoption de Windows Communication Foundation : faciliter la future migration
Pour faciliter une future migration des nouvelles applications ASP.NET vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], suivez les recommandations précédentes ainsi que les recommandations suivantes.  
  
## <a name="protocols"></a>Protocoles  
 Désactivez la prise en charge d'ASP.NET 2.0 pour SOAP 1.2 :  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>    
      </webServices>  
     </system.web>   
</configuration>  
```  
  
 Cette procédure est recommandée parce que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert des messages qui se conforment à différents protocoles, tels que SOAP 1.1 et SOAP 1.2, et utilisent différents points de terminaison. Si un service Web ASP.NET 2.0 est configuré pour prendre en charge SOAP 1.1 et SOAP 1.2 (configuration par défaut), celui-ci ne peut pas effectuer une migration en avant vers un point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] unique à l'adresse originale qui serait certainement compatible avec tous les clients existants du service Web ASP.NET. De plus, le choix de SOAP 1.2 au lieu de 1.1 restreint davantage la clientèle du service.  
  
## <a name="service-development"></a>Développement des services  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vous permet de définir des contrats de service en appliquant <xref:System.ServiceModel.ServiceContractAttribute> aux interfaces ou aux classes. Il est recommandé d'appliquer l'attribut à une interface plutôt qu'à une classe, afin de créer une définition d'un contrat qui peut être implémenté de différentes façons par un nombre illimité de classes. ASP.NET 2.0 prend en charge la possibilité d'appliquer l'attribut <xref:System.Web.Services.WebService> aux interfaces aussi bien qu'aux classes. Toutefois, comme indiqué précédemment, ASP.NET 2.0 présente un défaut qui fait que le paramètre Namespace de l'attribut <xref:System.Web.Services.WebService> n'a aucun effet lorsque cet attribut est appliqué à une interface plutôt qu'à une classe. Comme il est généralement recommandé de remplacer la valeur par défaut de l'espace de noms d'un service, http://tempuri.org, par le paramètre Namespace de l'attribut <xref:System.Web.Services.WebService>, il faut continuer à définir des services Web ASP.NET en appliquant l'attribut <xref:System.ServiceModel.ServiceContractAttribute> aux interfaces ou aux classes.  
  
-   Les méthodes chargées de définir ces interfaces doivent contenir un minimum de code. Faites-les déléguer leur tâche à d'autres classes. Les nouveaux types de services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent aussi déléguer par la suite les tâches importantes à ces classes.  
  
-   Fournissez des noms explicites pour les opérations d'un service à l'aide du paramètre `MessageName` de <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Ce procédé est important parce que les noms par défaut pour les opérations dans ASP.NET sont différents des noms par défaut fournis par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. En fournissant des noms explicites, vous n'avez pas à vous reposer sur les noms par défaut.  
  
-   N'implémentez pas d'opérations de service Web ASP.NET avec des méthodes polymorphes, car [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas en charge l'implémentation des opérations ayant des méthodes polymorphes.  
  
-   Utilisez le <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> afin de fournir des valeurs explicites pour les en-têtes HTTP SOAPAction chargés d'acheminer les demandes HTTP aux méthodes.  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Cette approche évite de dépendre des valeurs SOAPAction par défaut utilisées par ASP.NET et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui sont identiques.  
  
-   Évitez l'utilisation des extensions SOAP. Si les extensions SOAP sont requises, déterminez si leur choix correspond à une fonctionnalité déjà fournie par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Si tel est le cas, reconsidérez le choix de ne pas adopter [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] immédiatement.  
  
## <a name="state-management"></a>Gestion des états  
 Évitez de devoir maintenir l'état dans les services. La maintenance de l'état tend non seulement à compromettre l'évolutivité d'une application, mais les mécanismes de gestion d'état d'ASP.NET et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont très différents, bien que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prenne en charge les mécanismes ASP.NET en mode de compatibilité ASP.NET.  
  
## <a name="exception-handling"></a>Gestion des exceptions  
 Lors de la conception des structures des types de données à envoyer et à recevoir par un service, concevez aussi des structures pour représenter les divers types d'exceptions qui peuvent se produire dans un service et qu'il faut décrire éventuellement à un client.  
  
```  
[Serializable]  
[XmlRoot(  
     Namespace="ExplicitNamespace", IsNullable=true)]  
    public partial class AnticipatedException {  
  
     private string anticipatedExceptionInformationField;  
  
     public string AnticipatedExceptionInformation {  
      get {  
          return this.anticipatedExceptionInformationField;  
          }  
      set {  
          this.anticipatedExceptionInformationField = value;  
          }  
     }  
}  
```  
  
 Donnez à ces classes la possibilité de se sérialiser en code XML :  
  
```  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 Ces classes peuvent ensuite servir à fournir les détails pour les instances <xref:System.Web.Services.Protocols.SoapException> levées explicitement :  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Ces classes d'exception sont réutilisables avec la classe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.FaultException%601> pour lever une nouvelle `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Sécurité  
 Les éléments suivants sont des recommandations de sécurité.  
  
-   Évitez d'utiliser des profils ASP.NET 2.0, car leur utilisation peut restreindre l'utilisation du mode intégration ASP.NET si le service a été migré vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Évitez d'utiliser les listes de contrôle d'accès pour contrôler l'accès aux services, car les services Web ASP.NET prennent en charge ces listes à l'aide des services Internet (IIS), ce qui n'est pas le cas de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. En effet, les services Web ASP.NET dépendent d'IIS pour l'hébergement et il n'est pas forcément nécessaire d'héberger WCF dans IIS.  
  
-   Vous pouvez faire appel à des fournisseurs de rôles ASP.NET 2.0 pour autoriser l'accès aux ressources d'un service.  
  
## <a name="see-also"></a>Voir aussi  
 [Anticipation de l’adoption de Windows Communication Foundation : faciliter l’intégration future](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
