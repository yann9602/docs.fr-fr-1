---
title: "ASP.NET Caching Integration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ASP.NET Caching Integration
Cet exemple montre comment utiliser le cache de sortie ASP.NET avec le modèle de programmation HTTP Web WCF.  Consultez l'exemple [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) pour obtenir une version auto\-hébergée de ce scénario qui traite en détail de l'implémentation du service.  Cette rubrique met l'accent sur la fonctionnalité d'intégration du cache de sortie ASP.NET.  
  
## Démonstrations  
 Intégration au cache de sortie ASP.NET  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## Discussion  
 L'exemple emploie l'<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> pour utiliser la mise en cache de sortie ASP.NET avec le service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  L'<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> est appliqué aux opérations de service et fournit le nom d'un profil de cache dans un fichier de configuration qui doit être appliqué aux réponses de l'opération donnée.  
  
 Dans le fichier Service.cs de l'exemple de projet Service, les opérations `GetCustomers` et `GetCustomer` sont toutes deux marquées avec l'<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, qui fournit le nom de profil de cache « CacheFor60Seconds ».  Dans le fichier Web.config du projet Service, le profil de cache « CacheFor60Seconds » est fourni sous l'élément \<`caching`\> de \<`system.web`\>.  Pour ce profil de cache, la valeur de l'attribut `duration` est « 60 », de sorte que les réponses associées à ce profil sont placées dans le cache de sortie ASP.NET pour une durée de 60 secondes.  De même, pour ce profil de cache, l'attribut `varmByParam` a la valeur « format », de sorte que les réponses aux demandes présentant différentes valeurs pour le paramètre de chaîne de requête `format` sont mises en cache séparément.  Enfin, l'attribut `varyByHeader` du profil de cache a la valeur « Accept », de sorte que les réponses aux demandes présentant différentes valeurs d'en\-tête Accept sont mises en cache séparément.  
  
 Le fichier program.cs du projet Client montre comment un tel client peut être créé à l'aide de <xref:System.Net.HttpWebRequest>.  Notez qu'il ne s'agit là que de l'un des moyens d'accéder à un service WCF.  Il est également possible d'accéder au service à l'aide d'autres classes .NET Framework, comme la fabrique de canaux [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et <xref:System.Net.WebClient>.  D'autres exemples du Kit de développement logiciel \(SDK\) \(comme les exemples [Service HTTP de base](../../../../docs/framework/wcf/samples/basic-http-service.md) et [Sélection automatique du format](../../../../docs/framework/wcf/samples/automatic-format-selection.md)\) montrent comment utiliser ces classes pour communiquer avec un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## Pour exécuter l'exemple  
 Cet exemple est composé de trois projets :  
  
-   **Service** Projet d'application Web qui inclut un service HTTP WCF hébergé dans ASP.NET.  
  
-   **Client** Projet d'application console qui passe des appels au service.  
  
-   **Common** Bibliothèque partagée qui contient le type Customer utilisé par le client et le service.  
  
 Lorsque l'application console Client s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.  
  
#### Pour exécuter l'exemple  
  
1.  Ouvrez la solution de l'exemple ASP.NET Caching Integration.  
  
2.  Appuyez sur Ctrl\+Maj\+B pour générer la solution.  
  
3.  Si la fenêtre **Explorateur de solutions** n'est pas déjà ouverte, appuyez sur CTRL\+W\+S.  
  
4.  Dans la fenêtre **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **Service** et sélectionnez **Démarrer une nouvelle instance**.  Cette opération lance le serveur de développement ASP.NET, qui héberge le service.  
  
5.  Dans la fenêtre **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **Client** et sélectionnez **Démarrer une nouvelle instance**.  
  
6.  La fenêtre de console du client apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML.  Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur.  
  
7.  Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.  
  
8.  Appuyez sur une touche quelconque pour arrêter l'application console Client.  
  
9. Appuyez sur MAJ\+F5 pour arrêter le débogage du service.  
  
10. Dans la zone de notification Windows, cliquez avec le bouton droit sur l'icône du serveur de développement ASP.NET et sélectionnez **Arrêter**.