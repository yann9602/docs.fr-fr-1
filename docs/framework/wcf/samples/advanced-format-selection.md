---
title: "Sélection avancée du format"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e02d9082-4d55-41d8-9329-98f6d1c77f06
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5b3c1bd6c63188b9b812248b8d815237832a4aad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="advanced-format-selection"></a>Sélection avancée du format
Cet exemple montre comment étendre le modèle de programmation REST [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] afin de prendre en charge de nouveaux formats pour les réponses sortantes. En outre, l'exemple utilise un modèle T4 pour retourner la réponse sous forme de page XHTML et ainsi montrer comment un modèle de programmation de style d'affichage peut être implémenté.  
  
## <a name="sample-details"></a>Détails de l'exemple  
 L'exemple se compose d'un service simple et du code client qui adresse des requêtes au service.  Le service prend en charge une seule opération [WebGet], dont la signature de méthode est la suivante : `Message EchoListWithGet(string list);`  
  
 Lorsque le client adresse une requête au service, il fournit la liste séparée par des virgules d'éléments provenant du paramètre de chaîne de requête `list` et le service retourne cette même liste dans l'un des formats suivants : XML, JSON, Atom, XHTML ou jpeg.  
  
 Le format de réponse retourné par le service est déterminé d'abord par un paramètre de chaîne de requête `format`, puis par un en-tête HTTP Accept fourni avec la requête. Si la valeur du paramètre de chaîne de requête `format` est l'un des formats précédents, la réponse est retournée dans ce format. Si le paramètre de chaîne de requête `format` est absent, le service effectue une itération au sein des éléments d'en-tête Accept de la requête et retourne le format du premier content-type pris en charge par le service.  
  
 Notez le type de retour de l'opération. Le modèle de programmation REST [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend en charge en natif que les formats de réponse XML et JSON lorsqu'une opération retourne un type autre que <xref:System.ServiceModel.Channels.Message>. Toutefois, lorsqu'il utilise <xref:System.ServiceModel.Channels.Message> comme type de retour, le développeur peut entièrement contrôler la façon dont le message doit être mis en forme.  
  
 L'exemple utilise les méthodes <xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A>, <xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> et <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> pour sérialiser la liste de chaînes en messages XML, JSON et ATOM, respectivement. Pour le format de réponse jpeg, la méthode <xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> est utilisée et l'image est enregistrée dans le flux de données. Pour la réponse XHTML, la méthode <xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> est utilisée avec un modèle T4 prétraité, qui se compose d'un fichier .tt et d'un fichier .cs généré automatiquement. Le fichier .tt permet à un développeur d'écrire une réponse sous forme de modèle contenant des variables et des structures de contrôle. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]T4, consultez [génération d’artefacts à l’aide de modèles de texte](http://go.microsoft.com/fwlink/?LinkId=166023).  
  
 L'exemple est constitué d'un service auto-hébergé et d'un client qui s'exécute dans une application console. Lorsque l'application console s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter cet exemple  
  
1.  Ouvrez la solution de l'exemple Advanced Format Selection. Pour que l'exemple fonctionne correctement, vous devez exécuter [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] en tant qu'administrateur. Cela en double-cliquant sur le [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] icône et en choisissant **exécuter en tant qu’administrateur** dans le menu contextuel.  
  
2.  Appuyez sur CTRL+MAJ+B pour générer la solution, puis appuyez sur Ctrl+F5 pour exécuter le projet d'application console AdvancedFormatSelection sans débogage. La fenêtre de console apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML.  
  
3.  Lorsque l'exemple s'exécute, le client envoie des requêtes au service et affiche les réponses dans la fenêtre de console. Notez les différents formats des réponses : XML, JSON, Atom et XHTML.  
  
4.  Vous êtes ensuite invité à naviguer jusqu'à un URI où vous pouvez demander la réponse dans un format .jpeg. Ouvrez un navigateur et naviguez jusqu'à l'URI fourni.  
  
5.  Appuyez sur une touche quelconque pour arrêter l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AdvancedFormatSelection`  
  
## <a name="see-also"></a>Voir aussi
