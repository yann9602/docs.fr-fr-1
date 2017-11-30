---
title: "Modèles de contrôle UI Automation pour les clients"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
caps.latest.revision: "24"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1d556b3da13b70a0a5e69eb72905e04a01dffa9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-control-patterns-for-clients"></a>Modèles de contrôle UI Automation pour les clients
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette vue d’ensemble présente des modèles de contrôle pour les clients UI Automation. Il inclut des informations sur comment un client UI Automation peut utiliser des modèles de contrôle pour accéder aux informations sur le [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 Les modèles de contrôle permettent de catégoriser et d'exposer les fonctionnalités d'un contrôle, indépendamment du type de contrôle ou de l'apparence du contrôle. Les clients UI Automation peuvent examiner un <xref:System.Windows.Automation.AutomationElement> pour déterminer le contrôle les modèles sont pris en charge et s’assurer du comportement du contrôle.  
  
 Pour obtenir une liste complète des modèles de contrôle, consultez [vue d’ensemble du modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Obtention de modèles de contrôle  
 Les clients récupèrent un modèle de contrôle d'un <xref:System.Windows.Automation.AutomationElement> en appelant <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> ou <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Les clients peuvent utiliser la méthode <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> ou une propriété `IsPatternAvailable` individuelle (par exemple, <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) pour déterminer si un modèle ou un groupe de modèles est pris en charge sur <xref:System.Windows.Automation.AutomationElement>. Toutefois, il est plus efficace d'essayer d'obtenir le modèle de contrôle et de tester une référence `null` que de vérifier les propriétés prises en charge et de récupérer le modèle de contrôle, car cela entraîne moins d'appels interprocessus.  
  
 L'exemple suivant montre comment obtenir un modèle de contrôle <xref:System.Windows.Automation.TextPattern> d'un <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Récupération de propriétés sur des modèles de contrôle  
 Les clients peuvent récupérer les valeurs de propriété sur les modèles de contrôle en appelant <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> ou <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> et en effectuant le cast de l'objet retourné en un type approprié. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriétés, consultez [propriétés UI Automation pour les Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
 En plus des méthodes `GetPropertyValue`, les valeurs de propriété peuvent être récupérées via les accesseurs [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] pour accéder aux propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sur un modèle.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Contrôles avec modèles variables  
 Certains types de contrôles prennent en charge différents modèles selon leur état ou la manière dont le contrôle est utilisé. Les exemples de contrôles qui peuvent avoir des modèles variables incluent les vues Liste (miniatures, mosaïques, icônes, liste, détails), les graphiques [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] (secteur, ligne, barre, valeur d'une cellule avec une formule), la zone de document [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (affichage normal, mode web, mode Plan, mode Impression, Aperçu avant impression) et les apparences du [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)].  
  
 Les contrôles implémentant des types de contrôles personnalisés peuvent disposer de n’importe quel jeu de modèles de contrôle nécessaires pour représenter leurs fonctionnalités.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)  
 [Modèle de texte UI Automation](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)  
 [Appeler un contrôle à l’aide d’UI Automation](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [Obtenir l’état bascule d’une case à cocher à l’aide d’UI Automation](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [Mappage de modèle de contrôle pour les Clients UI Automation](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Exemple de texte TextPattern Insert](http://msdn.microsoft.com/en-us/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [Exemple de sélection et de recherche de TextPattern](http://msdn.microsoft.com/en-us/0a3bca57-8b72-489d-a57c-da85b7a22c7f)  
 [InvokePattern et ExpandCollapsePattern Menu exemple d’élément](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
