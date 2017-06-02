---
title: "Obtenir des mod&#232;les de contr&#244;le UI Automation pris en charge | Microsoft Docs"
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
  - "modèles de contrôle, mise en route"
  - "Automation d’interface utilisateur, l’obtention de modèles de contrôle"
  - "mise en route, les modèles de contrôle"
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
caps.latest.revision: 10
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 10
---
# Obtenir des mod&#232;les de contr&#244;le UI Automation pris en charge
> [!NOTE]
>  Cette documentation est destinée aux développeurs .NET Framework qui veulent utiliser managé [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes définies dans le <xref:System.Windows.Automation> espace de noms. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique montre comment récupérer des objets de modèle de contrôle à partir de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] éléments.  
  
### <a name="obtain-all-control-patterns"></a>Obtenir tous les modèles de contrôle  
  
1.  Obtenir le <xref:System.Windows.Automation.AutomationElement> dont le contrôle des modèles vous intéressent.  
  
2.  Appelez <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> pour obtenir tous les modèles de contrôle à partir de l’élément.  
  
> [!CAUTION]
>  Il est fortement recommandé qu’un client n’utilise pas <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Performances peuvent être gravement affectées, car cette méthode appelle <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> en interne pour chaque modèle de contrôle existant. Si possible, un client doit appeler <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> pour les modèles qui l’intéressent.  
  
### <a name="obtain-a-specific-control-pattern"></a>Obtenir un modèle de contrôle spécifique  
  
1.  Obtenir le <xref:System.Windows.Automation.AutomationElement> dont le contrôle des modèles vous intéressent.  
  
2.  Appelez <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> pour interroger un modèle spécifique. Ces méthodes sont semblables, mais si le modèle n’est pas trouvé, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lève une exception, et <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> renvoie `false`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant récupère une <xref:System.Windows.Automation.AutomationElement> pour un élément de liste et obtient un <xref:System.Windows.Automation.SelectionItemPattern> à partir de cet élément.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles de contrôle UI Automation pour les Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)