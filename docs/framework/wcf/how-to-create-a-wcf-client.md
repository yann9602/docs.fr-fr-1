---
title: "Comment&#160;: cr&#233;er un client Windows Communication Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "clients (WCF), exécuter"
  - "WCF (clients WCF), exécuter"
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
caps.latest.revision: 64
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 64
---
# Comment&#160;: cr&#233;er un client Windows Communication Foundation
Il s'agit de la quatrième des six tâches requises pour créer une application [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].Pour disposer d'une vue d'ensemble des six tâches, consultez la rubrique [Didacticiel de mise en route](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
 Cette rubrique décrit comment extraire les métadonnées d'un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et les utiliser pour créer un proxy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] qui peut accéder au service.Cette tâche prend fin en utilisant la fonctionnalité Ajouter une référence de service fournie par Visual Studio.Cet outil obtient les métadonnées du point de terminaison MEX du service et génère un fichier de code source managé pour un proxy client dans le langage que vous avez choisi \(C\# par défaut\).L'outil crée non seulement le proxy client, mais crée ou met également à jour le fichier de configuration pour le client qui permet à l'application cliente de se connecter au service au niveau de l'un de ses points de terminaison.  
  
> [!NOTE]
>  Vous pouvez également utiliser l'outil [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer la classe proxy et la configuration au lieu d'utiliser Ajouter une référence de service dans Visual Studio.  
  
> [!WARNING]
>  Lors de l'appel d'un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à partir d'un projet de bibliothèque de classes dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], vous pouvez utiliser la fonctionnalité Ajouter une référence de service pour générer automatiquement un proxy et le fichier de configuration associé.Le fichier de configuration ne sera pas utilisé par le projet de bibliothèque de classes.Vous devez ajouter les paramètres dans le fichier de configuration généré dans le fichier app.config pour le fichier exécutable qui appelle la bibliothèque de classes.  
  
 L'application cliente utilise la classe proxy générée pour communiquer avec le service.Cette procédure est décrite dans la rubrique [Comment : Utiliser un client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
### Pour créer un client Windows Communication Foundation  
  
1.  Créez un projet d'application console en cliquant avec le bouton droit sur la solution Mise en route, sélectionnez **Ajouter**, **Nouveau projet**.Dans la boîte de dialogue **Ajouter un nouveau projet** dans la partie gauche de la boîte de dialogue, sélectionnez **Windows** sous **C\#** ou **VB**.Dans la section centrale de la boîte de dialogue, sélectionnez **Application console**.Nommez le projet `GettingStartedClient`.  
  
2.  Définissez la version cible du .Net Framework du projet GettingStartedClient à .NET Framework 4.5 en cliquant avec le bouton droit sur **GettingStartedClient** dans l'Explorateur de solutions et en sélectionnant **Propriétés**.Dans la zone de liste déroulante **Framework cible**, sélectionnez **.NET Framework 4.5**.Définir la version cible du .Net Framework pour un projet VB est un peu différent, dans la boîte de dialogue de propriétés du projet GettingStartedClient, cliquez sur l'onglet **Compiler** à gauche de l'écran, puis sur le bouton **Options avancées de compilation** dans le coin inférieur gauche de la boîte de dialogue.Ensuite, sélectionnez **.NET Framework 4.5** dans la zone de liste déroulante **Framework cible**.  
  
     La définition de la version cible du .Net Framework déclenche le rechargement de la solution par Visual Studio 2011 ; appuyez sur **OK** à l'invite.  
  
3.  Ajoutez une référence à System.ServiceModel dans le projet GettingStartedClient en cliquant avec le bouton droit sur le dossier **Référence** sous le projet GettingStartedClient dans l'Explorateur de solutions et sélectionnez **Ajouter une référence**.Dans la boîte de dialogue **Ajouter une référence**, sélectionnez **Framework** dans la partie gauche de la boîte de dialogue.Dans la zone de texte Rechercher des assemblys, tapez `System.ServiceModel`.Dans la section centrale de la boîte de dialogue, sélectionnez **System.ServiceModel**, cliquez sur le bouton **Ajouter**, puis cliquez sur le bouton **Fermer**.Enregistrez la solution en cliquant sur le bouton **Enregistrer tout** dans le menu principal.  
  
4.  Ensuite vous ajouterez une référence de service au service Calculator.Pour ce faire, vous devez d'abord démarrer l'application console GettingStartedHost.Une fois l'hôte en cours d'exécution, cliquez avec le bouton droit sur le dossier Références sous le projet GettingStartedClient dans l'Explorateur de solutions et sélectionnez Ajouter une référence de service et tapez l'URL suivante dans la zone d'adresse de la boîte de dialogue Ajouter une référence de service : http:\/\/localhost:8000\/ServiceModelSamples\/Service et cliquez sur le bouton **Aller à**.Le CalculatorService doit ensuite être affiché dans la zone de liste de services. Double\-cliquez sur CalculatorService pour développer et afficher les contrats de service implémentés par le service.Conservez l'espace de noms par défaut et cliquez sur le bouton **OK**.  
  
     Lorsque vous ajoutez une référence à un service à l'aide de Visual Studio, un nouvel élément s'affiche dans l'Explorateur de solutions sous le dossier Références de service sous le projet GettingStartedClient.Si vous utilisez l'outil [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), un fichier de code source et le fichier app.config sont générés.  
  
     Vous pouvez également utiliser l'outil en ligne de commande [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) avec les commutateurs appropriés pour créer le code client.L'exemple suivant génère un fichier de code et un fichier de configuration pour le service.Le premier exemple montre comment générer le proxy en VB et le deuxième montre comment générer le proxy en C\# :  
  
    ```  
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service  
  
    ```  
  
    ```csharp  
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service  
  
    ```  
  
 Vous avez créé le proxy que l'application cliente utilisera pour appeler le service de calculatrice.Passez à la section suivante de la série : [Comment : configurer un client](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
  
## Voir aussi  
 [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [Getting Started](../../../docs/framework/wcf/samples/getting-started-sample.md)   
 [Self\-Host](../../../docs/framework/wcf/samples/self-host.md)   
 [Comment : publier les métadonnées d'un service à l'aide d'un fichier de configuration](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)   
 [Comment : utiliser Svcutil.exe pour télécharger des documents de métadonnées](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)