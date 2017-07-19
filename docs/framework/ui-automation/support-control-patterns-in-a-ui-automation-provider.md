---
title: "Support Control Patterns in a UI Automation Provider | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control patterns, supporting in UI Automation provider"
  - "UI Automation, supporting control patterns in provider"
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
caps.latest.revision: 13
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 13
---
# Support Control Patterns in a UI Automation Provider
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique montre comment implémenter un ou plusieurs modèles de contrôle sur un fournisseur UI Automation de sorte que les applications clientes puissent manipuler les contrôles et en obtenir les données.  
  
### Prendre en charge les modèles de contrôle  
  
1.  Implémentez les interfaces appropriées pour les modèles de contrôle que l’élément doit prendre en charge, telles que <xref:System.Windows.Automation.Provider.IInvokeProvider> pour <xref:System.Windows.Automation.InvokePattern>.  
  
2.  Retournez l’objet contenant votre implémentation de chaque interface de contrôle dans votre implémentation de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=fullName>.  
  
## Exemple  
 L’exemple suivant illustre une implémentation de <xref:System.Windows.Automation.Provider.ISelectionProvider> pour une zone de liste personnalisée à sélection unique. Elle retourne trois propriétés et obtient l’élément sélectionné.  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## Exemple  
 L’exemple suivant illustre une implémentation de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> qui retourne la classe implémentant <xref:System.Windows.Automation.Provider.ISelectionProvider>. La plupart des contrôles de zone de liste pourraient aussi prendre en charge d’autres modèles, mais dans cet exemple, une référence null \(`Nothing` dans [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]\) est retournée pour tous les autres identificateurs de modèle.  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## Voir aussi  
 [UI Automation Providers Overview](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)   
 [Server\-Side UI Automation Provider Implementation](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)