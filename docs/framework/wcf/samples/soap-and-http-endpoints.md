---
title: "Points de terminaison SOAP et HTTP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Points de terminaison SOAP et HTTP
Cet exemple montre comment implémenter un service RPC, et l'exposer aux formats SOAP et POX \(Plain Old XML\) à l'aide du modèle de programmation Web [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  Pour plus d'informations sur la liaison HTTP du service, consultez l'exemple [Service HTTP de base](../../../../docs/framework/wcf/samples/basic-http-service.md).  Cet exemple se concentre sur les détails ayant trait à l'exposition du même service sur SOAP et HTTP au moyen de différentes liaisons.  
  
## Démonstrations  
 Exposition d'un service RPC sur SOAP et HTTP à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## Discussion  
 Cet exemple est constitué de deux composants : un projet d'application Web \(Service\) qui contient un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et une application console \(Client\) qui appelle des opérations de service à l'aide de  liaisons SOAP et HTTP.  
  
 Le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expose 2 opérations, `GetData` et `PutData`, qui renvoient la chaîne passée en entrée.  Les opérations de service sont annotées avec <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute>.  Ces attributs contrôlent la projection HTTP de ces opérations.  Elles sont aussi annotées avec <xref:System.ServiceModel.OperationContractAttribute>, ce qui permet leur exposition sur des liaisons SOAP.  La méthode `PutData` du service lève un <xref:System.ServiceModel.Web.WebFaultException>, qui est renvoyé sur HTTP avec le code d'état HTTP et sur SOAP en tant qu'erreur SOAP.  
  
 Le fichier Web.config configure le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec 3 points de terminaison :  
  
-   le point de terminaison ~\/service.svc\/mex qui expose les métadonnées du service pour l'accès des clients SOAP ;  
  
-   le point de terminaison ~\/service.svc\/http qui permet aux clients d'accéder au service en utilisant la liaison HTTP ;  
  
-   le point de terminaison ~\/service.svc\/soap qui permet aux clients d'accéder au service en utilisant la liaison SOAP sur HTTP.  
  
 Le point de terminaison HTTP est configuré avec un point de terminaison \<`webHttp`\> standard où `helpEnabled` a la valeur `true`.  Par conséquent, le service expose sous ~\/service.svc\/http\/help une page d'aide XHTML que les clients HTTP peuvent utiliser pour accéder au service.  
  
 Le projet client illustre l'accès au service à l'aide d'un proxy SOAP \(généré via **Ajouter une référence de service**\) et à l'aide de <xref:System.Net.WebClient>.  
  
 L'exemple se compose d'un service hébergé sur le Web et d'une application console.  Lorsque l'application console s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.  
  
#### Pour exécuter l'exemple  
  
1.  Ouvrez la solution de l'exemple des points de terminaison SOAP et HTTP.  
  
2.  Appuyez sur Ctrl\+Maj\+B pour générer la solution.  
  
3.  Si la fenêtre **Explorateur de solutions** n'est pas déjà ouverte, appuyez sur CTRL\+W\+S pour l'ouvrir.  
  
4.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **Service** et placez le curseur sur l'option de menu contextuel **Débogage** pour faire apparaître le menu contextuel **Démarrer une nouvelle instance**.  Cliquez sur **Démarrer une nouvelle instance**.  Cette opération lance le serveur de développement ASP.NET, qui héberge le service.  
  
5.  Dans les fenêtres de l'Explorateur de solutions, cliquez avec le bouton droit sur le projet Client et placez le curseur sur l'option de menu contextuel **Débogage** pour faire apparaître le menu contextuel **Démarrer une nouvelle instance**.  Cliquez sur **Démarrer une nouvelle instance**.  
  
6.  La fenêtre de console du client apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML.  Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur.  
  
7.  Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.  
  
8.  Appuyez sur une touche quelconque pour arrêter l'application console Client.  
  
9. Appuyez sur MAJ\+F5 pour arrêter le débogage du service.  
  
10. Dans la zone de notification Windows, cliquez avec le bouton droit sur l'icône du serveur de développement ASP.NET et sélectionnez **Arrêter** dans le menu contextuel.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`