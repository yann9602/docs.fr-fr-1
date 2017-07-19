---
title: "D&#233;pannage du didacticiel de mise en route | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# D&#233;pannage du didacticiel de mise en route
Cette rubrique décrit les problèmes les plus courants rencontrés pendant l'exécution du didacticiel de prise en main et comment les résoudre.  
  
1.  [Je n'arrive pas à trouver les fichiers projet sur mon disque dur.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q1)  
  
2.  [Tentative d'exécution de l'application de service : HTTP n'a pas pu inscrire l'URL http://+:8000/ServiceModelSamples/Service/.Le processus n'a pas de droits d'accès à cet espace de noms.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q2)  
  
3.  [Tentative d'utilisation de l'outil Svcutil.exe : 'svcutil' n'est pas reconnu en tant que commande interne ou externe, un programme exécutable ou un fichier de commandes.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q3)  
  
4.  [Impossible de trouver le fichier App.config généré par Svcutil.exe.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q4)  
  
5.  [Compilation de l'application cliente : 'CalculatorClient' ne contient pas de définition pour '&lt;nom de méthode&gt;' et aucune méthode d'extension '&lt;nom de méthode&gt;' acceptant un premier argument de type 'CalculatorClient' n'est détectée (une directive using ou une référence d'assembly est-elle manquante ?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q5)  
  
6.  [Compilation de l'application cliente : Le type ou le nom d'espace de noms 'CalculatorClient' est introuvable (une directive using ou une référence d'assembly est-elle manquante ?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q6)  
  
7.  [Exécution du client : Exception non prise en charge : System.ServiceModel.EndpointNotFoundException : Connexion à http://localhost:8000/ServiceModelSamples/Service/CalculatorService impossible.Code d'erreur TCP 10061 : Aucune connexion n'a pu être établie car l'ordinateur cible l'a refusée activement.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q7)  
  
<a name="BKMK_q1"></a>   
## Je n'arrive pas à trouver les fichiers projet sur mon disque dur.  
 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] enregistre les fichiers projet dans c:\\Utilisateurs\\\<nom d'utilisateur\\Documents\\\<version de Visual Studio\>\\Projects dans [!INCLUDE[wv](../../../includes/wv-md.md)] et [!INCLUDE[win7_client_secondref](../../../includes/win7-client-secondref-md.md)], et c:\\Documents and Settings\\\<nom d'utilisateur\>\\Mes Documents\\\<version de Visual Studio\>\\Projects dans les versions antérieures de Windows.  
  
<a name="BKMK_q2"></a>   
## Tentative d'exécution de l'application de service : HTTP n'a pas pu inscrire l'URL http:\/\/\+:8000\/ServiceModelSamples\/Service\/.Le processus n'a pas de droits d'accès à cet espace de noms.  
 Le processus qui héberge un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] doit être exécuté avec les privilèges d'administrateur.Si vous exécutez le service à partir de [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], vous devez exécuter [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] en tant qu'Administrateur.Pour ce faire, cliquez sur **Démarrer**, cliquez avec le bouton droit sur [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], puis sélectionnez **Exécuter en tant qu'administrateur**.Si vous exécutez le service à partir d'une invite de ligne de commande, vous devez démarrer cette invite en tant qu'administrateur de la même façon.Cliquez sur **Démarrer**, cliquez avec le bouton droit sur **Invite de commandes**, puis sélectionnez **Exécuter en tant qu'administrateur**.  
  
<a name="BKMK_q3"></a>   
## Tentative d'utilisation de l'outil Svcutil.exe : 'svcutil' n'est pas reconnu en tant que commande interne ou externe, un programme exécutable ou un fichier de commandes.  
 Svcutil.exe doit figurer dans le chemin d'accès système.La solution la plus simple consiste à utiliser l'invite de commandes.Cliquez sur **Démarrer**, puis sélectionnez **Tous les programmes**, [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], **Visual Studio Tools** et **Invite de commandes**[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].Cette invite de commandes affecte au chemin d'accès système les emplacements corrects de tous les outils livrés avec [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
<a name="BKMK_q4"></a>   
## Impossible de trouver le fichier App.config généré par Svcutil.exe.  
 La boîte de dialogue **Ajouter un élément existant** n'affiche par défaut que les fichiers portant les extensions suivantes : .cs, .resx, .settings, .xsd, .wsdl.Vous pouvez préciser que vous souhaitez consulter tous les types de fichier en sélectionnant **Tous les fichiers \(\*.\*\)** dans la zone de liste déroulante qui se trouve dans l'angle inférieur droit de la boîte de dialogue **Ajouter un élément existant**.  
  
<a name="BKMK_q5"></a>   
## Compilation de l'application cliente : 'CalculatorClient' ne contient pas de définition pour '\<nom de méthode\>' et aucune méthode d'extension '\<nom de méthode\>' acceptant un premier argument de type 'CalculatorClient' n'est détectée \(une directive using ou une référence d'assembly est\-elle manquante ?\)  
 Seules les méthodes marquées avec `ServiceOperationAttribute` sont exposées au monde extérieur.Si vous avez omis l'attribut `ServiceOperationAttribute` de l'une des méthodes dans l'interface `ICalculator`, vous obtenez ce message d'erreur lors de la compilation d'une application cliente qui appelle l'opération à laquelle manque l'attribut.  
  
<a name="BKMK_q6"></a>   
## Compilation de l'application cliente : Le type ou le nom d'espace de noms 'CalculatorClient' est introuvable \(une directive using ou une référence d'assembly est\-elle manquante ?\)  
 Vous obtenez cette erreur si vous n'ajoutez pas le fichier Proxy.cs ou Proxy.vb à votre projet client.  
  
<a name="BKMK_q7"></a>   
## Exécution du client : Exception non prise en charge : System.ServiceModel.EndpointNotFoundException : Connexion à http:\/\/localhost:8000\/ServiceModelSamples\/Service\/CalculatorService impossible.Code d'erreur TCP 10061 : Aucune connexion n'a pu être établie car l'ordinateur cible l'a refusée activement.  
 Cette erreur se produit si vous exécutez l'application cliente sans exécuter le service.  
  
<a name="BKMK_q8"></a>   
## Exception non gérée : System.ServiceModel.Security.SecurityNegotiationException : Échec de la négociation de sécurité SOAP avec « http:\/\/localhost:8000\/ServiceModelSamples\/Service\/CalculatorService » pour la cible « http:\/\/localhost:8000\/ServiceModelSamples\/Service\/CalculatorService »  
 Cette erreur se produit sur un ordinateur appartenant à un domaine qui ne bénéficie d'aucune connectivité réseau.Soit vous connectez votre ordinateur au réseau, soit vous désactivez la sécurité à la fois pour le client et le service.Pour le service, modifiez le code qui crée WSHttpBinding par ce qui suit.  
  
```  
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
  
```  
  
 Pour le client, remplacez l'élément **\<sécurité\>** sous l'élément **\<liaison\>** par ce qui suit :  
  
```  
<security mode="Node" />  
```  
  
## Voir aussi  
 [Didacticiel de mise en route](../../../docs/framework/wcf/getting-started-tutorial.md)   
 [Démarrage rapide de la résolution des problèmes WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)   
 [Résolution des problèmes d'installation](../../../docs/framework/wcf/troubleshooting-setup-issues.md)