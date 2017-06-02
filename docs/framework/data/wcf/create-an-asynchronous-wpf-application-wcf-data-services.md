---
title: "Proc&#233;dure&#160;: cr&#233;er une application WPF asynchrone (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Services de données WCF, opérations asynchrones"
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: cr&#233;er une application WPF asynchrone (WCF Data Services)
Avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez lier des données obtenues auprès d'un service de données à l'élément d'interface utilisateur d'une application WPF \(Windows Presentation Framework\).  Pour plus d'informations, consultez [Liaison de données aux contrôles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md). Vous pouvez également exécuter d'une manière asynchrone des opérations sur le service de données qui permettent à l'application de continuer à répondre en attendant une réponse à une demande de service de données.  Les applications pour Silverlight sont obligatoires pour accéder de façon asynchrone au service de données.  Pour plus d'informations, consultez [Opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 Cette rubrique montre comment accéder de façon asynchrone à un service de données et lier les résultats aux éléments d'une application WPF.  Les exemples dans cette rubrique utilisent l'exemple de service de données Northwind et des classes de service de données client générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 Vous trouverez ci\-après le code XAML qui définit la fenêtre de l'application WPF.  
  
 [!code-xml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## Exemple  
 La page code\-behind suivante du fichier XAML exécute une requête asynchrone à l'aide du service de données et lie les résultats aux éléments dans la fenêtre WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## Voir aussi  
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)