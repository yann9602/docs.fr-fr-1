---
title: Publication du formulaire
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe1be9177f3e811a3037377360f46f42904d5af3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="form-post"></a>Publication du formulaire
Cet exemple montre comment étendre le modèle de programmation REST WCF pour prendre en charge de nouveaux formats de requêtes entrantes. L'exemple inclut également une implémentation de formateur capable de désérialiser une requête provenant d'une publication de formulaire HTML en type [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. L'exemple utilise en outre un modèle T4 pour retourner une page HTML, qui fournit le formulaire HTML que les utilisateurs peuvent publier sur le service REST WCF.  
  
## <a name="demonstrates"></a>Démonstrations  
  
-   Extension de la prise en charge des nouveaux formats de requêtes entrantes.  
  
-   Intégration de modèles T4.  
  
## <a name="discussion"></a>Discussion  
 Cet exemple est composé de deux projets. Le premier est la bibliothèque HtmlFormProcessing qui inclut un formateur de requête personnalisé qui peut désérialiser des publications de formulaire HTML en types [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Le deuxième est une application console qui étend l'exemple Basic Resource Service de base pour utiliser le formateur de requête personnalisé de la bibliothèque HtmlFormProcessing.  
  
 Le formateur personnalisé capable de désérialiser des publications de formulaires HTML (HtmlFormRequestDispatchFormatter) accepte à la fois les types [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] qui peuvent être convertis à partir d'une chaîne à l'aide de <xref:System.ServiceModel.Dispatcher.QueryStringConverter> et les types marqués avec <xref:System.Runtime.Serialization.DataContractAttribute> dont les membres ne peuvent être convertis à partir d'une chaîne qu'à l'aide du QueryStringConverter.  
  
 Le projet de bibliothèque HtmlFormProcessing inclut également une classe de base abstraite, `RequestBodyDispatchFormatter`, qui peut être utilisée pour créer d'autres formateurs de requête personnalisés. Effectuer une dérivation de `RequestBodyDispatchFormatter` permet à un développeur de se concentrer sur la logique de désérialisation du corps de la requête, qui permet à la classe de base de mapper les paramètres du modèle URI aux paramètres de méthode de l'opération. Le projet de bibliothèque HtmlFormProcessing comprend aussi la classe `HtmlFormProcessingBehavior`, qui illustre la dérivation de <xref:System.ServiceModel.Description.WebHttpBehavior> pour remplacer le formateur de requête par défaut par un formateur de requête personnalisé.  
  
 Ce projet d’application console étend la [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemple. L'exemple Basic Resource Service montre comment exposer une ressource en utilisant le modèle de programmation REST WCF. Dans l'exemple Basic Resource Service, une ressource de collection de clients nommée « customer » est exposée de façon à ce que les clients qu'elle contient puissent être créés, récupérés, mis à jour et supprimés. L'exemple Basic Resource Service utilise uniquement les deux formats de requêtes entrantes pris en charge en natif : XML et JSON.  
  
 L'application console de cet exemple Form Post utilise le formateur personnalisé de la bibliothèque HtmlFormProcessing, qui permet aux utilisateurs de créer des clients en envoyant une requête provenant d'une publication de formulaire HTML à l'aide d'un navigateur. Il ajoute également une opération qui retourne une page HTML, laquelle inclut le formulaire à publier sur le service. Cette page HTML est générée à l'aide d'un modèle T4 prétraité, qui se compose d'un fichier .tt et d'un fichier .cs généré automatiquement. Le fichier .tt permet à un développeur d'écrire une réponse sous forme de modèle contenant des variables et des structures de contrôle. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]T4, consultez [génération d’artefacts à l’aide de modèles de texte](http://go.microsoft.com/fwlink/?LinkId=178139).  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez la solution de l'exemple Form Post. Pour que l'exemple fonctionne correctement, vous devez exécuter [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] en tant qu'administrateur. Cela en double-cliquant sur le [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] icône et en sélectionnant « Exécuter en tant qu’administrateur » dans le menu contextuel.  
  
2.  Appuyez sur CTRL+MAJ+B pour générer la solution, puis appuyez sur CTRL+F5 pour exécuter le projet FormPost.  
  
3.  La fenêtre de console apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML.  
  
4.  Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle (ajout, mise à jour, suppression d'un client, ou obtention de la liste des clients actuels) du service dans la fenêtre de console.  
  
5.  Vous êtes ensuite invité à naviguer jusqu'à l'URI du formulaire customer. Ouvrez un navigateur et naviguez jusqu'à l'URI fourni. Tapez un nom et une adresse pour le client et cliquez sur le **Submit** bouton.  
  
6.  Appuyez sur une touche quelconque dans la fenêtre de console pour continuer à exécuter l'exemple.  
  
7.  Lorsque l'exemple se termine, remarquez que le client que vous avez créé à l'aide du navigateur est inclus dans la liste finale des clients.  
  
8.  Appuyez sur une touche quelconque pour arrêter l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
