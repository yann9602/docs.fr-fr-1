---
title: "AspNetRouteIntegration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# AspNetRouteIntegration
Cet exemple montre comment héberger un service REST [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] à l'aide d'itinéraires ASP.NET.L'exemple [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) illustre une version auto\-hébergée de ce scénario et traite en détail de l'implémentation du service.Cette rubrique met l'accent sur la fonctionnalité d'intégration ASP.NET.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] le routage ASP.NET, consultez <xref:System.Web.Routing>.  
  
## Détails de l'exemple  
 Le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expose une collection de clients d'une manière orientée ressources\/REST.Tout comme un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SOAP, le service peut être hébergé dans ASP.NET à l'aide d'un fichier .svc.Toutefois, cette façon de procéder est rarement celle à privilégier pour les scénarios HTTP, car elle implique la présence de .svc dans l'URL du service.En outre, elle requiert le déploiement d'un fichier .svc avec la bibliothèque du service.Ces limitations peuvent être évitées en hébergeant le service à l'aide d'itinéraires ASP.NET, comme le montre cet exemple.  
  
 L'exemple héberge le service dans ASP.NET en ajoutant un <xref:System.ServiceModel.Activation.ServiceRoute> dans un fichier Global.asax.Le <xref:System.ServiceModel.Activation.ServiceRoute> spécifie le type du service \(‘Service’ dans ce cas\), le type de la fabrique d'hôte de service à utiliser pour le service \(<xref:System.ServiceModel.Activation.WebServiceHostFactory> dans ce cas\) et l'adresse de base HTTP pour le service \(‘~\/Customers’ dans ce cas\).  
  
 L'exemple inclut en outre un fichier Web.config qui ajoute l'<xref:System.Web.Routing.UrlRoutingModule> \(pour activer les itinéraires ASP.NET\) et comprend la configuration du service.La configuration configure en particulier le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec un <xref:System.ServiceModel.Description.WebHttpEndpoint> par défaut dont la propriété <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> a la valeur `true`.Par conséquent, l'infrastructure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] crée une page d'aide HTML automatique sous `http://localhost/Customers/help`, qui fournit des informations sur la façon de construire des requêtes HTTP adressées au service et d'accéder à la réponse HTTP du service. Il peut s'agir d'un exemple de la façon dont les informations concernant les clients sont représentées aux formats XML et JSON.  
  
 Exposer ainsi la collection customer \(et plus généralement, n'importe quelle ressource\) permet à un client d'interagir avec un service de façon uniforme en utilisant des URI et HTTP `GET`, `PUT`, `DELETE` et `POST`.  
  
 Le fichier program.cs du projet Client montre comment un tel client peut être créé à l'aide de <xref:System.Net.HttpWebRequest>.Notez qu'il ne s'agit là que de l'un des moyens d'accéder à un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Il est également possible d'accéder au service à l'aide d'autres classes .NET Framework, comme la fabrique de canaux [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et <xref:System.Net.WebClient>.D'autres exemples du Kit de développement logiciel \(SDK\) \(comme les exemples [Service HTTP de base](../../../../docs/framework/wcf/samples/basic-http-service.md) et [Sélection automatique du format](../../../../docs/framework/wcf/samples/automatic-format-selection.md)\) montrent comment utiliser ces classes pour communiquer avec un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Cet exemple est composé de 3 projets :  
  
 Service  
 Projet d'application Web qui inclut un service HTTP WCF hébergé dans ASP.NET.  
  
 Client  
 Projet d'application console qui passe des appels au service.  
  
 Common  
 Bibliothèque partagée qui contient le type `Customer` utilisé par le client et le service.Lorsque l'application console Client s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.  
  
#### Pour utiliser cet exemple  
  
1.  Ouvrez la solution de l'exemple ASP.NET Routes Integration dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Appuyez sur Ctrl\+Maj\+B pour générer la solution.  
  
3.  Si la fenêtre **Explorateur de solutions** n'est pas déjà ouverte, appuyez sur CTRL\+W\+S pour l'ouvrir.  
  
4.  Dans la fenêtre **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **Service** et placez le curseur sur l'option de menu contextuel **Débogage** pour faire apparaître le menu contextuel **Démarrer une nouvelle instance**, puis sélectionnez **Démarrer une nouvelle instance**.Cette opération lance le serveur de développement ASP.NET, qui héberge le service.  
  
5.  Dans la fenêtre **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **Client** et placez le curseur sur l'option de menu contextuel **Débogage** pour faire apparaître le menu contextuel **Démarrer une nouvelle instance**, puis sélectionnez **Démarrer une nouvelle instance**.  
  
6.  La fenêtre de console du client apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML.Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur.Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.  
  
7.  Appuyez sur une touche quelconque pour arrêter l'application console Client.  
  
8.  Appuyez sur Maj\+F5 pour arrêter le débogage du service puis, dans la zone de notification Windows, cliquez avec le bouton droit sur l'icône du serveur de développement ASP.NET et sélectionnez **Arrêter** dans le menu contextuel.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## Voir aussi