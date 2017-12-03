---
title: "Comment : personnaliser les comportements de liaison de données (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9aa93e5c0971d1af1f1962bfe4f61a0f56f66b9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Comment : personnaliser les comportements de liaison de données (services de données WCF)
Avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez fournir une logique personnalisée appelée par <xref:System.Data.Services.Client.DataServiceCollection%601> lorsqu'un objet est ajouté ou supprimé de la collection de liaisons ou lorsqu'une modification de propriété est détectée. Cette logique personnalisée est fournie en tant que méthodes, référencées sous la forme <xref:System.Func%602> les délégués qui retournent une valeur de `false` lorsque le comportement par défaut doit toujours être effectué à l’issue de la méthode personnalisée et `true` quand d’autres le traitement de la événement doit être arrêté.  
  
 Les exemples dans cette rubrique fournissent des méthodes personnalisées pour les paramètres `entityChanged` et `entityCollectionChanged` de <xref:System.Data.Services.Client.DataServiceCollection%601>. Les exemples dans cette rubrique utilisent l'exemple de service de données Northwind et des classes de service de données client générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  
 La page code-behind suivante du fichier XAML crée une <xref:System.Data.Services.Client.DataServiceCollection%601> avec des méthodes personnalisées appelées lorsque des modifications sont apportées aux données liées à la collection de liaisons. Lorsque l'événement <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> se produit, la méthode fournie empêche un élément ayant été supprimé de la collection de liaisons d'être supprimé du service de données. Lorsque l'événement <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> se produit, la valeur `ShipDate` est validée pour vérifier que les modifications ne sont pas apportées aux ordres déjà livrés.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Exemple  
 Le code XAML suivant définit la fenêtre de l'exemple précédent.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
