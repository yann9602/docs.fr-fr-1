---
title: "S&#233;lection automatique du format | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dab51e56-8517-4a6a-bb54-b55b15ab37bb
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# S&#233;lection automatique du format
Cet exemple montre comment activer la sélection automatique du format \(XML ou JSON\) avec le modèle de programmation REST [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et comment définir explicitement le format dans le code d'opération.  
  
## Détails de l'exemple  
 L'exemple se compose d'un service et du code client qui adresse des requêtes au service.  Le service prend en charge une seule opération HTTP `GET` \(`EchoWithGet`\) et une seule opération HTTP `POST` \(`EchoWithPost`\).  Les deux opérations attendent une chaîne, qu'elles retournent dans la réponse.  Avec l'opération `GET`, la chaîne est fournie dans un paramètre de chaîne de requête URI.  Avec l'opération `POST`, la chaîne est fournie dans le corps de la requête, sérialisé en XML.  Le service est en mesure de retourner des réponses au format XML ou JSON, en utilisant les nouvelles fonctionnalités de sélection automatique du format et de sélection impérative du format de [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
 Dans l'exemple, la sélection automatique du format est activée au moyen du fichier App.config.  Sur le point de terminaison HTTP Web par défaut, la valeur `true` a été affectée à l'attribut `automaticFormatSelectionEnabled`.  Avec la sélection automatique du format activée, l'infrastructure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sélectionne le format de réponse le plus approprié \(XML ou JSON\) en fonction des en\-têtes HTTP Accept ou Content\-Type de la requête.  Le développeur n'est pas obligé de fournir de code ou de configuration supplémentaire ; il lui suffit d'affecter à l'attribut `automaticFormatSelectionEnabled` la valeur `true` pour utiliser cette nouvelle fonctionnalité.  Dans le code client de Program.cs, les requêtes sont envoyées aux opérations `POST` et `GET` du service avec l'en\-tête HTTP Accept spécifié comme « application\/xml » ou « application\/json » et le service retourne une réponse dans le format en question.  
  
 La sélection impérative du format est aussi utilisée dans l'opération `GET`.  L'opération `GET` recherche un paramètre de chaîne de requête `format` facultatif et si elle en trouve, définit le format de réponse dans la propriété <xref:System.ServiceModel.Web.WebOperationContext.OutgoingResponse%2A>.  Définir impérativement le format de réponse de cette façon substitue la sélection automatique du format effectuée par l'infrastructure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 L'exemple est constitué d'un service auto\-hébergé et d'un client qui s'exécute dans une application console.  Lorsque l'application console s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.  
  
#### Pour utiliser cet exemple  
  
1.  Ouvrez la solution de l'exemple Automatic Format Selection.  Pour que l'exemple fonctionne correctement, vous devez exécuter [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] en tant qu'administrateur.  Pour ce faire, cliquez avec le bouton droit sur l'icône [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] et sélectionnez **Exécuter en tant qu'administrateur** dans le menu contextuel.  
  
2.  Appuyez sur CTRL\+MAJT\+B pour générer la solution, puis appuyez sur Ctrl\+F5 pour exécuter le projet d'application console AutomaticFormatSelection.  La fenêtre de console apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML.  
  
3.  Lorsque l'exemple s'exécute, le client envoie des requêtes au service et affiche les réponses dans la fenêtre de console.  Remarquez les différents formats des réponses, XML et JSON.  
  
4.  Appuyez sur une touche quelconque pour arrêter l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, accédez à la page des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Web\AutomaticFormatSelection`  
  
## Voir aussi