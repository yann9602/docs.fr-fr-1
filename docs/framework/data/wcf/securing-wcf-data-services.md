---
title: "Sécurisation de WCF Data Services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c45da4ec1fa5d111be19437dde54035a89f9162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="securing-wcf-data-services"></a>Sécurisation de WCF Data Services
Cette rubrique décrit les considérations sur la sécurité qui sont spécifiques au développement, au déploiement et à l'exécution de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] et des applications qui accèdent aux services prenant en charge l'[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. Vous devez également suivre ces recommandations pour créer des applications [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sécurisées.  
  
 Lors de la planification de la sécurité d'un service [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] basé sur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], vous devez résoudre l'authentification, le processus de découverte et de vérification de l'identité d'un principal et également son autorisation, en déterminant si un principal authentifié est autorisé à accéder aux ressources demandées. Vous devez également déterminer si chiffrer le message à l'aide de SSL.  
  
## <a name="authenticating-client-requests"></a>Authentification des demandes du client  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] n'implémente aucun type d'authentification en lui-même, mais repose plutôt sur les dispositions d'authentification de l'hôte du service de données. Cela signifie que le service présume que toute demande qu'il reçoit a déjà été authentifiée par l'hôte réseau et que l'hôte a correctement identifié le principal de la demande via les interfaces fournies par [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Ces options d’authentification et les approches sont détaillées dans [série OData et l’authentification](http://go.microsoft.com/fwlink/?LinkId=200381).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Options d'authentification pour un service de données WCF  
 Le tableau suivant répertorie une partie des mécanismes d'authentification qui s'offrent à vous pour authentifier les demandes à un service de données WCF.  
  
|Options d’authentification|Description|  
|----------------------------|-----------------|  
|Authentification anonyme|Lorsque l'authentification anonyme HTTP est activée, n'importe quel principal est en mesure de se connecter au service de données. Les informations d'identification ne sont pas requises pour un accès anonyme. Utilisez cette option uniquement lorsque vous souhaitez autoriser tout le monde à accéder au service de données.|  
|Authentification de base et condensé|Les informations d'identification comprenant un nom d'utilisateur et un mot de passe sont requises pour l'authentification. Prend en charge l'authentification des clients non Windows. **Note de sécurité :** informations d’identification de l’authentification de base (nom d’utilisateur et mot de passe) sont envoyées en texte clair et peuvent être interceptées. L’authentification Digest envoie un hachage en fonction des informations d’identification fournies, les sécurisant davantage par rapport à une authentification basique. Ces deux authentifications sont vulnérables aux attaques de l'intercepteur (« Man-in-the-Middle »). Lorsque vous utilisez ces méthodes d'authentification, nous vous conseillons d'utiliser une communication chiffrée entre le client et le service de données à l'aide de SSL (Secure Sockets Layer). <br /><br /> Microsoft Internet Information Services (IIS) fournit l'implémentation à la fois de l'authentification de base et condensée pour les demandes HTTP dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. L'implémentation de ce fournisseur d'authentification Windows permet à une application cliente .NET Framework de fournir les informations d'identification dans l'en-tête HTTP de la demande au service de données pour négocier de façon transparente l'authentification d'un utilisateur Windows. Pour plus d’informations, consultez [référence technique de l’authentification Digest](http://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Lorsque vous souhaitez que votre service de données utilise l'authentification de base reposant sur un service d'authentification personnalisé et non les informations d'identification Windows, vous devez implémenter un module HTTP [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pour l'authentification.<br /><br /> [!INCLUDE[crexample](../../../../includes/crexample-md.md)]comment utiliser un schéma d’authentification de base personnalisée avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], consultez le billet sur [l’authentification de base personnalisée](http://go.microsoft.com/fwlink/?LinkID=200388) dans le [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] et la série de l’authentification.|  
|Authentification Windows|Les informations d'identification basées sur Windows sont échangées à l'aide de NTLM ou Kerberos. Ce mécanisme est plus sécurisé que l'authentification de base ou condensée, mais requiert que le client soit une application basée sur Windows. IIS fournit également l'implémentation de l'authentification Windows pour les demandes HTTP dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Pour plus d’informations, consultez [vue d’ensemble de l’authentification de formulaires ASP.NET](http://msdn.microsoft.com/library/099c1587-6934-476e-ac95-28f534bc9708).<br /><br /> [!INCLUDE[crexample](../../../../includes/crexample-md.md)]comment utiliser l’authentification Windows avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], consultez le billet sur [l’authentification Windows](http://go.microsoft.com/fwlink/?LinkID=200384) dans le [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] et la série de l’authentification.|  
|Authentification par formulaire [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]|L'authentification par formulaire vous permet d'authentifier des utilisateurs à l'aide de votre propre code puis de conserver un jeton d'authentification dans un cookie ou dans l'URL de la page. Vous authentifiez le nom d'utilisateur et le mot de passe de vos utilisateurs en créant un formulaire de connexion. Les demandes non authentifiées sont redirigées vers une page de connexion, où l'utilisateur fournit des informations d'identification et envoie le formulaire. Si l'application authentifie la demande, le système délivre un ticket qui contient une clé pour rétablir l'identité pour les demandes suivantes. Pour plus d’informations, consultez [fournisseur d’authentification Forms](http://msdn.microsoft.com/library/77e21ba2-bad1-4967-a8ec-74942dea7e47). **Note de sécurité :** par défaut, le cookie qui contient le ticket d’authentification de formulaires n’est pas sécurisé lorsque vous utilisez l’authentification par formulaire dans un [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application Web. Vous devriez considérer l'utilisation de SSL pour protéger le ticket d'authentification et les informations d'identification de la connexion initiale. <br /><br /> [!INCLUDE[crexample](../../../../includes/crexample-md.md)]l’utilisation de formulaires de l’authentification avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], consultez le billet sur [l’authentification par formulaire](http://go.microsoft.com/fwlink/?LinkID=200389) dans le [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] et la série de l’authentification.|  
|Authentification basée sur les revendications|Dans l’authentification basée sur les revendications, le service de données s’appuie sur un service de fournisseur d’identité « tiers » approuvé pour authentifier l’utilisateur. Le fournisseur d'identité authentifie positivement l'utilisateur qui demande l'accès aux ressources du service de données et émet un jeton qui accorde l'accès aux ressources demandées. Ce jeton est ensuite présenté au service de données, qui accorde ensuite l'accès à l'utilisateur en fonction de la relation d'approbation avec le service d'identité qui émet le jeton d'accès.<br /><br /> L'avantage d'utiliser un fournisseur d'authentification basée sur les revendications est que celles-ci peuvent être utilisées pour authentifier différents types de clients entre plusieurs domaines approuvés. En utilisant un tel fournisseur tiers, un service de données peut décharger les revendications de gestion et authentification des utilisateurs. OAuth 2.0 est un protocole d'authentification basée sur les revendications pris en charge par le contrôle d'accès Microsoft Azure AppFabric pour l'autorisation fédérée en tant que service. Ce protocole prend en charge les services REST. [!INCLUDE[crexample](../../../../includes/crexample-md.md)]l’utilisation de OAuth 2.0 avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], consultez le billet sur [OData et OAuth](http://go.microsoft.com/fwlink/?LinkId=200514) dans le [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] et la série de l’authentification.|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>Authentification dans la bibliothèque cliente  
 Par défaut, la bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ne fournit aucune information d'identification lors d'une demande à un service [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Lorsque les informations de connexions sont demandées par le service de données pour authentifier un utilisateur, elles peuvent être fournies par un <xref:System.Net.NetworkCredential> accédé depuis la propriété <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> du <xref:System.Data.Services.Client.DataServiceContext>, comme dans l'exemple suivant :  
  
```csharp  
// Set the client authentication credentials.  
context.Credentials =  
    new NetworkCredential(userName, password, domain);  
```  
  
```vb  
' Set the client authentication credentials.  
context.Credentials = _  
    New NetworkCredential(userName, password, domain)  
```  
  
 Pour plus d’informations, consultez [Comment : spécifier des informations d’identification Client pour une demande de Service de données](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Lorsque le service de données demande des informations de connexion qui ne peuvent pas être spécifiées à l'aide d'un objet <xref:System.Net.NetworkCredential>, comme un jeton ou un cookie basé sur des revendications, vous devez définir manuellement les en-têtes, généralement les en-têtes `Authorization` et `Cookie`, dans la demande HTTP. Pour plus d’informations sur ce type de scénario d’authentification, consultez le billet [OData et l’authentification : raccordements côté Client](http://go.microsoft.com/fwlink/?LinkID=200385). Pour obtenir un exemple montrant comment définir des en-têtes HTTP dans un message de demande, consultez [Comment : définir des en-têtes dans la demande du Client](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Emprunt d'identité  
 Généralement, le service de données accède aux ressources demandées, comme les fichiers sur le serveur ou la base de données, à l'aide des informations d'authentification du processus de travail qui héberge actuellement le service de données. Lors de l'utilisation de l'emprunt d'identité, les applications [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] peuvent s'exécuter avec l'identité Windows (compte d'utilisateur) de l'utilisateur qui fait la requête. L'emprunt d'identité est utilisé couramment dans les applications qui reposent sur IIS pour authentifier l'utilisateur et les informations d'identification de ce principal sont utilisées pour accéder aux ressources demandées. Pour plus d’informations, consultez [emprunt d’identité ASP.NET](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d).  
  
## <a name="configuring-data-service-authorization"></a>Configuration de l'autorisation du service de données  
 L'autorisation est le fait d'autoriser l'accès aux ressources d'une application à un principal ou à un processus identifié sur la base d'une authentification précédemment réussie. En règle générale, vous ne devriez accorder aux utilisateurs du service de données que des droits suffisants pour exécuter les opérations requises par les applications clientes.  
  
### <a name="restrict-access-to-data-service-resources"></a>Restriction d'accès aux ressources du service de données  
 Par défaut, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet d'accorder à n'importe quel utilisateur pouvant accéder au service de données un accès en lecture et écriture commun aux ressources du service de données (jeu d'entités et opérations de service). Les règles qui définissent l'accès en lecture et écriture peuvent être définies séparément pour chaque jeu d'entité exposé par le service de données, tout comme toute opération de service. Nous vous recommandons de limiter l'accès en lecture et écriture aux seules ressources requises par l'application cliente. Pour plus d’informations, consultez [accès de ressource requise](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Implémentation d'intercepteurs basés sur le rôle  
 Les intercepteurs vous permettent d'intercepter les demandes adressées aux ressources du service de données avant qu'elles ne soient traitées par le service de données. Pour plus d’informations, consultez [intercepteurs](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md). Les intercepteurs vous permettent de prendre des décisions d'autorisation en fonction de l'utilisateur authentifié qui effectue la demande. [!INCLUDE[crexample](../../../../includes/crexample-md.md)]Comment restreindre l’accès aux ressources de service de données basée sur une identité de l’utilisateur authentifié, consultez [Comment : intercepter des Messages de Service de données](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Restriction d'accès aux ressources d'un magasin de données persistantes ou aux ressources locales  
 Les comptes que vous utilisez pour accéder au magasin de données persistantes doivent disposer uniquement des autorisations minimales pour prendre en charge les spécifications du service de données dans la base de données ou le système de fichiers. Lorsque vous utilisez une authentification anonyme, il s'agit du compte utilisé pour exécuter l'application d'hébergement. Pour plus d'informations, consultez [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md). Lorsque vous utilisez l'emprunt d'identité, les utilisateurs authentifiés doivent être autorisés à accéder à ces ressources, généralement dans le cadre d'un groupe Windows.  
  
## <a name="other-security-considerations"></a>Autres considérations à propos de la sécurité  
  
### <a name="secure-the-data-in-the-payload"></a>Sécurisation des données dans la charge utile  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] est basé sur le protocole HTTP. Dans un message HTTP, l'en-tête peut contenir des informations d'identification utiles concernant l'utilisateur, selon l'authentification implémentée par le service de données. Le corps du message peut également contenir des données utiles sur le client, qu'il convient de protéger. Dans ces deux cas, nous vous recommandons d'utiliser SSL pour protéger ces informations lors de la transmission.  
  
### <a name="ignored-message-headers-and-cookies"></a>En-têtes et cookies de message ignorés  
 Les en-têtes des demandes HTTP autres que celles qui déclarent des types de contenu et des emplacements de ressources, sont ignorés et ne sont jamais définis par le service de données.  
  
 Les cookies peuvent également être utilisés dans le cadre d'un schéma d'authentification, comme avec l'authentification par formulaire [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Toutefois, les cookies HTTP définis sur une demande entrante sont ignorés par [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. L'hôte d'un service de données peut traiter le cookie, mais le runtime [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] n'analyse ni ne retourne jamais de cookies. La bibliothèque du client [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ne traite pas les cookies envoyés dans la réponse.  
  
### <a name="custom-hosting-requirements"></a>Conditions d'hébergement personnalisé  
 Par défaut, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] est créé dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hébergée dans IIS. Cela permet au service de données de tirer parti des comportements de sécurité de cette plateforme. Vous pouvez définir les services [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] hébergés par un hôte client. Pour plus d’informations, consultez [qui héberge le Service de données](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md). Les composants et la plateforme qui hébergent un service de données doivent assurer les comportements de sécurité suivants pour empêcher des attaques sur le service de données :  
  
-   Limiter la longueur de l'URI accepté dans une demande de service de données pour toutes les opérations possibles.  
  
-   Limiter la taille des messages HTTP entrants et sortants.  
  
-   Limiter le nombre total de demandes sortantes à tout moment.  
  
-   Limiter la taille des en-têtes HTTP et leurs valeurs, et fournir à [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] un accès aux données d'en-tête.  
  
-   Détecter et répertorier les attaques connues, telles que TCP SYN et les attaques de relecture de message.  
  
### <a name="values-are-not-further-encoded"></a>Les valeurs ne sont pas encodées ultérieurement.  
 Les valeurs de propriété envoyées au service de données ne sont pas encodées ultérieurement par le runtime de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Par exemple, lorsqu'une propriété de chaîne d'une entité inclut un contenu HTML formaté, les balises ne sont pas encodées en HTML par le service de données. De même, le service de données n'encode pas ultérieurement les valeurs de propriété dans la réponse. La bibliothèque du client n'exécute aucun encodage supplémentaire.  
  
### <a name="considerations-for-client-applications"></a>Considérations pour les applications clientes  
 Les considérations sur la sécurité suivantes s'appliquent aux applications qui utilisent le client [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour accéder aux services [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] :  
  
-   La bibliothèque du client suppose que les protocoles utilisés pour accéder au service de données fournissent un niveau de sécurité suffisant.  
  
-   La bibliothèque du client utilise toutes les valeurs par défaut des délais d'attente et des options d'analyse des piles de transport fournies par la plateforme sous-jacente.  
  
-   La bibliothèque du client ne lit aucun paramètre des fichiers de configuration de l'application.  
  
-   La bibliothèque du client n'implémente aucun mécanisme d'accès entre domaines. En revanche, elle utilise les mécanismes fournis par la pile HTTP sous-jacente.  
  
-   La bibliothèque du client ne dispose d'aucun élément d'interface utilisateur et elle ne tente jamais d'afficher ou de restituer les données qu'elle reçoit ou envoie.  
  
-   Nous recommandons que les applications clientes valident toujours les entrées utilisateur et les données acceptées provenant de services non approuvés.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
