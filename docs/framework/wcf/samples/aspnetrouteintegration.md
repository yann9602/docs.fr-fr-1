---
title: AspNetRouteIntegration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b54de1c495dee466475979db7e6ba8d8ff9cf55b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
Cet exemple montre comment héberger un service REST [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] à l'aide d'itinéraires ASP.NET. Le [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemple présente une version autonome de ce scénario et aborde l’implémentation de service en profondeur. Cette rubrique met l’accent sur la fonctionnalité d’intégration ASP.NET. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] le routage ASP.NET, consultez <xref:System.Web.Routing>.  
  
## <a name="sample-details"></a>Détails de l'exemple  
 Le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expose une collection de clients d'une manière orientée ressources/REST. Tout comme un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SOAP, le service peut être hébergé dans ASP.NET à l'aide d'un fichier .svc. Toutefois, cette façon de procéder est rarement celle à privilégier pour les scénarios HTTP, car elle implique la présence de .svc dans l'URL du service. En outre, elle requiert le déploiement d'un fichier .svc avec la bibliothèque du service. Ces limitations peuvent être évitées en hébergeant le service à l'aide d'itinéraires ASP.NET, comme le montre cet exemple.  
  
 L'exemple héberge le service dans ASP.NET en ajoutant un <xref:System.ServiceModel.Activation.ServiceRoute> dans un fichier Global.asax. Le <xref:System.ServiceModel.Activation.ServiceRoute> spécifie le type du service (‘Service’ dans ce cas), le type de la fabrique d'hôte de service à utiliser pour le service (<xref:System.ServiceModel.Activation.WebServiceHostFactory> dans ce cas) et l'adresse de base HTTP pour le service (‘~/Customers’ dans ce cas).  
  
 L'exemple inclut en outre un fichier Web.config qui ajoute l'<xref:System.Web.Routing.UrlRoutingModule> (pour activer les itinéraires ASP.NET) et comprend la configuration du service. La configuration configure en particulier le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec un <xref:System.ServiceModel.Description.WebHttpEndpoint> par défaut dont la propriété <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> a la valeur `true`. Par conséquent, l'infrastructure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] crée une page d'aide HTML automatique sous `http://localhost/Customers/help`, qui fournit des informations sur la façon de construire des requêtes HTTP adressées au service et d'accéder à la réponse HTTP du service. Il peut s'agir d'un exemple de la façon dont les informations concernant les clients sont représentées aux formats XML et JSON.  
  
 Exposer ainsi la collection customer (et plus généralement, n'importe quelle ressource) permet à un client d'interagir avec un service de façon uniforme en utilisant des URI et HTTP `GET`, `PUT`, `DELETE` et `POST`.  
  
 Le fichier program.cs du projet Client montre comment un tel client peut être créé à l'aide de <xref:System.Net.HttpWebRequest>. Notez qu'il ne s'agit là que de l'un des moyens d'accéder à un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Il est également possible d'accéder au service à l'aide d'autres classes .NET Framework, comme la fabrique de canaux [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et <xref:System.Net.WebClient>. Autres exemples du SDK (telles que la [Service HTTP de base](../../../../docs/framework/wcf/samples/basic-http-service.md) exemple et [la sélection automatique du Format](../../../../docs/framework/wcf/samples/automatic-format-selection.md) exemple) montrent comment utiliser ces classes pour communiquer avec un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.  
  
 Cet exemple est composé de 3 projets :  
  
 Service  
 Projet d'application Web qui inclut un service HTTP WCF hébergé dans ASP.NET.  
  
 Client  
 Projet d'application console qui passe des appels au service.  
  
 Commun  
 Bibliothèque partagée qui contient le type `Customer` utilisé par le client et le service. Lorsque l'application console Client s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Ouvrez la solution de l'exemple ASP.NET Routes Integration dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
3.  Si elle n’est pas déjà ouverte, appuyez sur « CTRL + W + S pour ouvrir le **l’Explorateur de solutions** fenêtre.  
  
4.  À partir de la **l’Explorateur de solutions** avec le bouton droit de windows, le **Service** de projet et placez le curseur sur le **déboguer** option de menu contextuel afin que le **Démarrer Nouvelle Instance** s’affiche et sélectionnez le menu contextuel **démarrer une nouvelle Instance**.  Cette opération lance le serveur de développement ASP.NET, qui héberge le service.  
  
5.  À partir de la **l’Explorateur de solutions** avec le bouton droit de windows, le **Client** de projet et placez le curseur sur le **déboguer** option de menu contextuel afin que le **démarrer un nouveau Instance** s’affiche et sélectionnez le menu contextuel **démarrer une nouvelle Instance**.  
  
6.  La fenêtre de console du client apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML. Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur. Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.  
  
7.  Appuyez sur une touche quelconque pour arrêter l'application console Client.  
  
8.  Appuyez sur MAJ + F5 pour arrêter le débogage du service et dans la zone de Notification Windows, cliquez sur l’icône serveur de développement ASP.NET et sélectionnez **arrêter** dans le menu contextuel.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>Voir aussi
