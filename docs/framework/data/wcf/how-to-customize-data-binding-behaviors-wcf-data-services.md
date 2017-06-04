---
title: "Proc&#233;dure&#160;: personnaliser des comportements de liaison de donn&#233;es (WCF Data Services) | Microsoft Docs"
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
  - "Services de données WCF, personnalisation"
  - "Services de données WCF, liaison de données"
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: personnaliser des comportements de liaison de donn&#233;es (WCF Data Services)
Avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez fournir une logique personnalisée appelée par <xref:System.Data.Services.Client.DataServiceCollection%601> lorsqu'un objet est ajouté ou supprimé de la collection de liaisons ou lorsqu'une modification de propriété est détectée.  Cette logique personnalisée est fournie sous la forme de méthodes, référencée comme délégués <xref:System.Func%602> qui retournent une valeur `false` lorsque le comportement par défaut doit être effectué une fois que la méthode personnalisée est terminée, et `true` lorsque le traitement suivant de l'événement doit être arrêté.  
  
 Les exemples dans cette rubrique fournissent des méthodes personnalisées pour les paramètres `entityCollectionChanged` et `entityChanged` de <xref:System.Data.Services.Client.DataServiceCollection%601>.  Les exemples dans cette rubrique utilisent l'exemple de service de données Northwind et des classes de service de données client générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 La page code\-behind suivante du fichier XAML crée une <xref:System.Data.Services.Client.DataServiceCollection%601> avec des méthodes personnalisées appelées lorsque des modifications sont apportées aux données liées à la collection de liaisons.  Lorsque l'événement <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> se produit, la méthode fournie empêche un élément ayant été supprimé de la collection de liaisons d'être supprimé du service de données.  Lorsque l'événement <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> se produit, la valeur `ShipDate` est validée pour vérifier que les modifications ne sont pas apportées aux ordres déjà livrés.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## Exemple  
 Le code XAML suivant définit la fenêtre de l'exemple précédent.  
  
 [!code-xml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## Voir aussi  
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)