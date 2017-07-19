---
title: "Get UI Automation Element Properties | Microsoft Docs"
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
  - "properties, retrieving"
  - "UI Automation, retrieving properties of elements"
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
caps.latest.revision: 5
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 5
---
# Get UI Automation Element Properties
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui veulent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.  Pour obtenir les informations les plus récentes sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique montre comment récupérer les propriétés d'un élément [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
### Obtenir une valeur de propriété actuelle  
  
1.  Obtenez le <xref:System.Windows.Automation.AutomationElement> dont vous souhaitez obtenir la propriété.  
  
2.  Appelez <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ou récupérez la structure de propriété <xref:System.Windows.Automation.AutomationElement.Current%2A> et obtenez la valeur de l'un de ses membres.  
  
### Obtenir une valeur de propriété mise en cache  
  
1.  Obtenez le <xref:System.Windows.Automation.AutomationElement> dont vous souhaitez obtenir la propriété.  La propriété doit avoir été spécifiée dans <xref:System.Windows.Automation.CacheRequest>.  
  
2.  Appelez <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> ou récupérez la structure de propriété <xref:System.Windows.Automation.AutomationElement.Cached%2A> et obtenez la valeur de l'un de ses membres.  
  
## Exemple  
 L'exemple suivant présente différentes façons de récupérer les propriétés actuelles d'un <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## Voir aussi  
 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)   
 [Caching in UI Automation Clients](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)