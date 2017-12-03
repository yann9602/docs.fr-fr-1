---
title: "Comment : créer un client Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
caps.latest.revision: "64"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd2740cfef2a618e4ab220f7db84fc78a10e0980
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Comment : créer un client Windows Communication Foundation
Il s'agit de la quatrième des six tâches requises pour créer une application [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]. Pour une vue d’ensemble des six tâches, consultez la [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) rubrique.  
  
 Cette rubrique décrit comment extraire les métadonnées d'un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et les utiliser pour créer un proxy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] qui peut accéder au service. Cette tâche prend fin en utilisant la fonctionnalité Ajouter une référence de service fournie par Visual Studio. Cet outil obtient les métadonnées du point de terminaison MEX du service et génère un fichier de code source managé pour un proxy client dans le langage que vous avez choisi (C# par défaut). L'outil crée non seulement le proxy client, mais également le fichier de configuration (ou le met à jour) pour le client qui permet à l'application cliente de se connecter au service au niveau de l'un de ses points de terminaison.  
  
> [!NOTE]
>  Vous pouvez également utiliser le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) outil pour générer la classe de proxy et la configuration au lieu d’utiliser Ajouter une référence de Service à l’intérieur de Visual Studio.  
  
> [!WARNING]
>  Lors de l'appel d'un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à partir d'un projet de bibliothèque de classes dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], vous pouvez utiliser la fonctionnalité Ajouter une référence de service pour générer automatiquement un proxy et le fichier de configuration associé.  Le fichier de configuration ne sera pas utilisé par le projet de bibliothèque de classes. Vous devez ajouter les paramètres dans le fichier de configuration généré dans le fichier app.config pour le fichier exécutable qui appelle la bibliothèque de classes.  
  
 L'application cliente utilise la classe proxy générée pour communiquer avec le service. Cette procédure est décrite dans [Comment : utiliser un Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
### <a name="to-create-a-windows-communication-foundation-client"></a>Pour créer un client Windows Communication Foundation  
  
1.  Créer un nouveau projet d’application console en cliquant sur la solution de mise en route, sélectionnez **ajouter**, **nouveau projet**. Dans le **ajouter un nouveau projet** boîte de dialogue sur le côté gauche de la boîte de dialogue, sélectionnez **Windows** sous **c#** ou **VB**. Dans la section centrale de la boîte de dialogue Sélectionnez **Application Console**. Attribuez un nom au projet `GettingStartedClient`.  
  
2.  Définir le framework cible du projet GettingStartedClient à .NET Framework 4.5 en cliquant avec le bouton droit sur **GettingStartedClient** dans l’Explorateur de solutions et en sélectionnant **propriétés**. Dans la zone de liste déroulante **Framework cible** sélectionnez **.NET Framework 4.5**. Paramètre du framework cible pour un projet VB est un peu différent, dans la boîte de dialogue Propriétés du projet GettingStartedClient, cliquez sur le **compiler** onglet sur le côté gauche de l’écran, puis cliquez sur le **avancé Options de compilation** bouton dans le coin inférieur gauche de la boîte de dialogue. Puis sélectionnez **.NET Framework 4.5** dans la zone de liste déroulante **Framework cible**.  
  
     La définition de l’infrastructure cible provoque Visual Studio 2011 recharger la solution, appuyez sur **OK** lorsque vous y êtes invité.  
  
3.  Ajouter une référence à System.ServiceModel dans le projet GettingStartedClient en cliquant sur le **référence** dossier sous le projet GettingStartedClient dans l’Explorateur de solutions, puis sélectionnez **ajouter** Référence. Dans le **ajouter une référence** boîte de dialogue Sélectionnez **Framework** sur le côté gauche de la boîte de dialogue. Dans la zone de texte Rechercher des assemblys, tapez `System.ServiceModel`. Dans la section centrale de la boîte de dialogue Sélectionnez **System.ServiceModel**, cliquez sur le **ajouter** , puis cliquez sur le **fermer** bouton. Enregistrez la solution en cliquant sur le **Enregistrer tout** situé sous le menu principal.  
  
4.  Ensuite vous ajouterez une référence de service au service Calculator. Pour ce faire, vous devez d'abord démarrer l'application console GettingStartedHost. Une fois que l’ordinateur hôte est en cours d’exécution. vous pouvez cliquez avec le bouton droit sur le dossier références sous le projet GettingStartedClient dans l’Explorateur de solutions et sélectionnez Ajouter une référence de Service et tapez l’URL suivante dans la zone Adresse de la boîte de dialogue Ajouter une référence de Service : lien hypertexte « http:/ / localhost:8000/ServiceModelSamples/Service « http://localhost : 8000/ServiceModelSamples/Service et cliquez sur le **accédez** bouton. Le CalculatorService doit ensuite être affiché dans la zone de liste de services. Double-cliquez sur CalculatorService pour développer et afficher les contrats de service implémentés par le service. Laissez l’espace de noms par défaut et cliquez sur le **OK** bouton.  
  
     Lorsque vous ajoutez une référence à un service à l’aide de Visual Studio, un nouvel élément s’affiche dans l’Explorateur de solutions sous le dossier Références de service sous le projet GettingStartedClient.  Si vous utilisez la [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) outil seront générés un fichier de code source et le fichier app.config.  
  
     Vous pouvez également utiliser l’outil de ligne de commande [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) avec les commutateurs appropriés pour créer le code client. L'exemple suivant génère un fichier de code et un fichier de configuration pour le service. Le premier exemple montre comment générer le proxy en VB et le deuxième montre comment générer le proxy en C# :  
  
    ```  
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
    ```csharp  
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
 Vous avez créé le proxy que l'application cliente utilisera pour appeler le service de calculatrice. Passez à la rubrique suivante de la série : [Comment : configurer un Client](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Outil ServiceModel Metadata Utility (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Prise en main](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [L’auto-hébergement](../../../docs/framework/wcf/samples/self-host.md)  
 [Comment : publier des métadonnées pour un Service à l’aide d’un fichier de Configuration](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Comment : utiliser Svcutil.exe pour télécharger des Documents de métadonnées](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
