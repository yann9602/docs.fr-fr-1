---
title: "Services WCF et ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
caps.latest.revision: 24
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 24
---
# Services WCF et ASP.NET
Cette rubrique présente les services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] d'hébergement côte à côte avec ASP.NET et leur hébergement en mode de compatibilité ASP.NET.  
  
## Hébergement côte à côte de WCF avec ASP.NET  
 Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans les services IIS \(Internet Information Services\) peuvent être localisés avec les pages.ASPX et les services Web ASMX dans un domaine d'application unique et commun.  ASP.NET fournit des services d'infrastructure communs tels que la gestion AppDomain et la compilation dynamique pour [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et l'exécution d'ASP.NET http à la fois.  La configuration par défaut de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est côte à côte avec ASP.NET.  
  
 ![Services WCF et ASP .NET : état de partage](../../../../docs/framework/wcf/feature-details/media/hostingwcfwithaspnet.gif "HostingWCFwithASPNET")  
  
 L'exécution d'ASP.NET HTTP gère des demandes ASP.NET mais ne participe pas au traitement des demandes destinées aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bien que ces services soient hébergés dans le même AppDomain que le contenu ASP.NET.  À la place, le modèle de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] intercepte les messages adressés aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et les route à travers le transport\/pile de canaux de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Les résultats du modèle côte à côte est le suivant :  
  
-   ASP.NET et les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent partager l'état AppDomain.  Parce que les deux infrastructures peuvent coexister dans le même AppDomain, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut également partager l'état AppDomain avec ASP.NET \(y compris les variables statiques, les événements et ainsi de suite\).  
  
-   Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se comportent de façon cohérente, indépendamment de l'environnement d'hébergement et du transport.  L'exécution d'ASP.NET HTTP est intentionnellement associée à l'environnement d'hébergement de IIS\/ASP.NET et à la communication HTTP.  Inversement, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est conçu pour se comporter de façon cohérente à travers les environnements d'hébergement \([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se comporte de façon cohérente à la fois à l'intérieur et en dehors d'IIS\) et à travers le transport \(un service hébergé dans IIS 7.0 et version ultérieure a un comportement cohérent à travers tous les points de terminaison qu'il expose, même si quelques\-uns de ces points utilisent des protocoles autres que HTTP\).  
  
-   Dans un AppDomain, les fonctionnalités implémentées par l'exécution de HTTP s'appliquent au contenu ASP.NET mais pas à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  De nombreuses fonctionnalités de la plate\-forme d'application ASP.NET spécifiques à HTTP ne s'appliquent pas aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans un AppDomain qui contient le contenu ASP.NET.  Voici des exemples de ces fonctionnalités :  
  
    -   HttpContext : <xref:System.Web.HttpContext.Current%2A> est toujours `null` lorsqu'il est accédé à partir d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  Utilisez plutôt <xref:System.ServiceModel.OperationContext.Current.RequestContext>.  
  
    -   Autorisation basée sur des fichiers : le modèle de sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'autorise pas l'application de la liste de contrôle d'accès \(ACL, Access Control List\) au fichier .svc du service lorsqu'il faut décider si une demande de service est autorisée.  
  
    -   Autorisation URL basée sur la configuration : de la même façon, le modèle de sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'adhère à aucune règle d'autorisation basée sur la configuration spécifiée dans l'élément de configuration \<authorization\> de System.Web.  Ces paramètres sont ignorés pour les demandes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] si un service réside dans un espace d'URL sécurisé par les règles d'autorisation d'URL de ASP.NET.  
  
    -   Extensibilité HttpModule : l'infrastructure d'hébergement de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] intercepte les demandes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lorsque l'événement <xref:System.Web.HttpApplication.PostAuthenticateRequest> est déclenché et ne retourne pas de traitement au pipeline de ASP.NET HTTP.  Les modules encodés pour intercepter des demandes aux étapes ultérieures du pipeline n'interceptent pas les demandes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
    -   Emprunt d'identité ASP.NET : par défaut, les demandes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécutent toujours comme l'identité de processus IIS, même si ASP.NET est configuré pour activer l'emprunt d'identité à l'aide de l'option de configuration \<identity impersonate\=”true” \/\> de System.Web.  
  
 Ces restrictions s'appliquent uniquement aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés dans l'application IIS.  Le comportement du contenu ASP.NET n'est pas affecté par la présence de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui requièrent les fonctionnalités traditionnellement fournies par le pipeline HTTP doivent envisager d'utiliser les équivalents [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] indépendants de l'hôte et du transport :  
  
-   <xref:System.ServiceModel.OperationContext> plutôt que <xref:System.Web.HttpContext>.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> au lieu de l'autorisation de fichier\/URL de ASP.NET.  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> ou des canaux en couche personnalisés au lieu des modules HTTP.  
  
-   Emprunt d'identité pour chaque opération à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] au lieu de l'emprunt d'identité System.Web.  
  
 Vous pouvez également envisager d'exécuter vos services en mode de compatibilité ASP.NET de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## Hébergement des services WCF en mode de compatibilité ASP.NET  
 Bien que le modèle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] soit conçu pour se comporter de façon cohérente à travers les environnements d'hébergement et les transports, souvent, dans certains scénarios, une application ne requiert pas ce degré de souplesse.  Le mode de compatibilité ASP.NET de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est approprié pour les scénarios qui ne requièrent pas d'hébergement en dehors d'IIS ni de communication sur des protocoles autres que HTTP, mais qui utilisent toutes les fonctionnalités de la plate\-forme d'application Web ASP.NET.  
  
 Contrairement à la configuration côte à côte par défaut, où l'infrastructure d'hébergement [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] intercepte les messages [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et les route hors du pipeline HTTP, les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui s'exécutent en mode de compatibilité ASP.NET participent pleinement au cycle de vie de la demande HTTP ASP.NET.  En mode de compatibilité, les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilisent le pipeline HTTP à travers une implémentation <xref:System.Web.IHttpHandler>, semblable à la façon dont sont gérées les demandes pour les pages ASPX et les services Web ASMX.  En conséquence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se comporte de façon identique à ASMX en ce qui concerne fonctionnalités ASP.NET suivantes :  
  
-   <xref:System.Web.HttpContext> : les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui s'exécutent en mode de compatibilité ASP.NET peuvent accéder à <xref:System.Web.HttpContext.Current%2A> et à son état associé.  
  
-   Autorisation basée sur des fichiers : les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui s'exécutent en mode de compatibilité ASP.NET peuvent être sécurisés en joignant des listes de contrôle d'accès de système de fichiers \(ACL\) au fichier .svc du service.  
  
-   Autorisation d'URL configurable : les règles d'autorisation d'URL de ASP.NET sont appliquées pour les demandes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lorsque le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécute en mode de compatibilité ASP.NET.  
  
-   Extensibilité <xref:System.Web.HttpModuleCollection> : parce que les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui s'exécutent en mode de compatibilité ASP.NET participent pleinement au cycle de vie de la demande HTTP ASP.NET, tout module HTTP configuré dans le pipeline HTTP est en mesure de fonctionner sur les demandes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à la fois avant et après l'appel du service.  
  
-   Emprunt d'identité ASP.NET : les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'exécutent avec l'identité actuelle du thread qui a emprunté l'identité de ASP.NET ; celle\-ci peut être différente de l'identité du processus IIS si l'emprunt d'identité ASP.NET a été activé pour l'application.  Si l'emprunt d'identité ASP.NET et l'emprunt d'identité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont activés à la fois pour une opération de service particulière, l'implémentation du service s'exécute finalement à l'aide de l'identité obtenue de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Le mode de compatibilité ASP.NET de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est activé au niveau de l'application à travers la configuration suivante \(localisée dans le fichier Web.config de l'application\) :  
  
```  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />  
</system.serviceModel>  
```  
  
 Cette valeur est par défaut "`true`" si non spécifiée.  L'affectation de la valeur `false` indique que tous les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui s'exécutent dans l'application s'exécutent en mode de compatibilité ASP.NET.  
  
 Parce que le mode de compatibilité ASP.NET implique des sémantiques de traitement de la demande fondamentalement différentes de la valeur par défaut de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les implémentations de service individuelles peuvent contrôler si elles s'exécutent dans une application pour laquelle le mode de compatibilité ASP.NET a été activé.  Les services peuvent utiliser <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> pour indiquer s'ils prennent en charge le mode de compatibilité ASP.NET.  La valeur par défaut de cet attribut est <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode>.  
  
 `[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]`  
  
 `public class CalculatorService : ICalculatorSession`  
  
 `{//Implement calculator service methods.}`  
  
 Le tableau suivant illustre comment le paramètre de mode de compatibilité défini au niveau de l'application interagit avec le niveau de prise en charge déclaré du service :  
  
|Paramètre de mode de compatibilité défini au niveau de l'application|\[AspNetCompatibilityRequirementsMode\]<br /><br /> Paramètre|Résultat observé|  
|--------------------------------------------------------------------------|-----------------------------------------------------------|----------------------|  
|aspNetCompatibilityEnabled \= "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode>|Le service est activé.|  
|aspNetCompatibilityEnabled \= "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode>|Le service est activé.|  
|aspNetCompatibilityEnabled \= "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode>|Une erreur d'activation se produit lorsque le service reçoit un message.|  
|aspNetCompatibilityEnabled \= "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode>|Une erreur d'activation se produit lorsque le service reçoit un message.|  
|aspNetCompatibilityEnabled \= "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode>|Le service est activé.|  
|aspNetCompatibilityEnabled \= "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode>|Le service est activé.|  
  
> [!NOTE]
>  IIS 7.0 et WAS autorisent la communication des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sur des protocoles autres que HTTP.  Toutefois, les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui s'exécutent dans les applications qui ont activé le mode de compatibilité ASP.NET ne sont pas autorisés à exposer des points de terminaison non\-HTTP.  Une telle configuration génère une exception d'activation lorsque le service reçoit son premier message.  
  
 Pour plus d'informations sur l'activation du mode de compatibilité ASP.NET pour les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> et l'exemple [ASP.NET Compatibility](../../../../docs/framework/wcf/samples/aspnet-compatibility.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>   
 [Fonctionnalités d'hébergement de Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=201276)